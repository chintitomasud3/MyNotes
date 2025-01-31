```python
import logging
import re
from getpass import getpass
from netmiko import ConnectHandler, NetMikoAuthenticationException, NetMikoTimeoutException

# Configure logging
logging.basicConfig(
    filename="switch_management.log",
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s",
)
console_handler = logging.StreamHandler()
console_handler.setLevel(logging.INFO)
formatter = logging.Formatter("%(asctime)s - %(levelname)s - %(message)s")
console_handler.setFormatter(formatter)
logging.getLogger().addHandler(console_handler)

def validate_ip(ip_address):
    """Validate an IPv4 address using a regular expression."""
    regex = r"^((25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[1-9]?[0-9])\.){3}(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[1-9]?[0-9])$"
    return bool(re.match(regex, ip_address))

def get_user_input():
    """Prompt the user for IP address, username, and password with input sanitization."""
    while True:
        ip_address = input("Enter the switch IP address: ").strip()
        if validate_ip(ip_address):
            break
        else:
            logging.error("Invalid IP address format. Please enter a valid IPv4 address.")
            print("Invalid IP address. Please try again.")

    while True:
        username = input("Enter the username: ").strip()
        if username:
            break
        else:
            logging.error("Username cannot be empty.")
            print("Username cannot be empty. Please try again.")

    while True:
        password = getpass("Enter the password: ").strip()
        if password:
            break
        else:
            logging.error("Password cannot be empty.")
            print("Password cannot be empty. Please try again.")

    return ip_address, username, password

def check_user_privilege(ip_address, username, password):
    """Check user privilege level to determine if an enable password is needed."""
    switch_config = {
        "device_type": "cisco_ios",
        "host": ip_address,
        "username": username,
        "password": password,
    }
    
    try:
        connection = ConnectHandler(**switch_config)
        privilege_level = connection.send_command("show privilege", read_timeout=20)  # Set read_timeout here
        
        # Check if user has level 15 access
        return "privilege level 15" in privilege_level
    except Exception as e:
        logging.error(f"Error checking user privileges: {str(e)}")
    
    return False

def parse_interface_status(output):
    """Parse the 'show interfaces status' output to classify interfaces by status."""
    connected_ports = []
    notconnected_ports = []

    for line in output.splitlines():
        if "connected" in line:
            parts = line.split()
            connected_ports.append(parts[0])
        elif "notconnect" in line:
            parts = line.split()
            notconnected_ports.append(parts[0])

    return connected_ports, notconnected_ports

def main():
    try:
        # Get sanitized user inputs
        ip_address, username, password = get_user_input()

        # Define the switch connection details without read_timeout
        switch_config = {
            "device_type": "cisco_ios",
            "host": ip_address,
            "username": username,
            "password": password,
        }

        # Establish the connection
        logging.info("Connecting to the switch at %s...", ip_address)
        connection = ConnectHandler(**switch_config)

        # Check user privileges to determine if we need an enable password
        enable_password_required = not check_user_privilege(ip_address, username, password)

        if enable_password_required:
            enable_password = getpass("Enter the enable password: ").strip()
            
            # Attempt to enter enable mode with provided enable password
            logging.info("Entering enable mode...")
            output = connection.send_command_timing("enable")
            output += connection.send_command_timing(enable_password)

            # Check for successful entry into enable mode by attempting a simple command
            test_output = connection.send_command_timing("show version")  # Test command to check access
            
            if "Invalid" in test_output or "error" in test_output.lower():
                print("You have entered a wrong enable password.")
                logging.warning("Incorrect enable password entered.")
                # Continue without entering configuration mode but allow 'show interfaces status'
        
        # Retrieve the port status using 'show interfaces status'
        logging.info("Retrieving interface status...")
        output = connection.send_command("show interfaces status", read_timeout=20)  # Set read_timeout here
        logging.info("Output from 'show interfaces status':\n%s", output)

        # Parse and display the interface statuses
        connected_ports, notconnected_ports = parse_interface_status(output)

        print("\nBefore Updating:")
        print(f"Connected Ports ({len(connected_ports)}): {', '.join(connected_ports)}")
        print(f"NotConnected Ports ({len(notconnected_ports)}): {', '.join(notconnected_ports)}")

        # Collect shutdown commands for ports in 'notconnect' state
        shutdown_commands = []
        for port in notconnected_ports:
            shutdown_commands.append(f"interface {port}")
            shutdown_commands.append("shutdown")

        # Apply the shutdown commands if any are generated
        if shutdown_commands:
            logging.info("Generating shutdown commands for unused ports...")
            logging.info("Shutdown commands:\n%s", "\n".join(shutdown_commands))
            config_output = connection.send_config_set(shutdown_commands)
            logging.info("Applied shutdown commands:\n%s", config_output)

            # Save the configuration to memory
            logging.info("Saving configuration to memory...")
            save_output = connection.send_command("write memory", read_timeout=20)  # Set read_timeout here
            logging.info("Configuration saved:\n%s", save_output)

            # Retrieve the updated port status
            logging.info("Retrieving updated interface status...")
            updated_output = connection.send_command("show interfaces status", read_timeout=20)  # Set read_timeout here
            logging.info("Updated output from 'show interfaces status':\n%s", updated_output)

            # Parse and display the updated interface statuses
            updated_connected_ports, updated_notconnected_ports = parse_interface_status(updated_output)

            print("\nAfter Updating:")
            print(f"Connected Ports ({len(updated_connected_ports)}): {', '.join(updated_connected_ports)}")
            print(f"NotConnected Ports ({len(updated_notconnected_ports)}): {', '.join(updated_notconnected_ports)}")

        else:
            logging.info("No unused ports found to shut down.")

        # Disconnect from the switch
        connection.disconnect()
        logging.info("Disconnected from the switch.")

    except NetMikoAuthenticationException as e:
        logging.error(f"Authentication failed: {str(e)}")
        print(f"Authentication failed: {str(e)}")
    except NetMikoTimeoutException as e:
        logging.error(f"Connection to the switch timed out: {str(e)}")
        print(f"Connection to the switch timed out: {str(e)}")
    except Exception as e:
        logging.error(f"An unexpected error occurred: {str(e)}")
        print(f"An unexpected error occurred: {e}")

if __name__ == "__main__":
    main()

```




