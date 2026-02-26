
# Nmap Master Commands for CEH

## **Basic Scanning Commands**

### **1. Basic Host Discovery**
```bash
nmap -sn [target]          # Ping scan (host discovery only)
nmap -sP [target]          # Same as -sn (deprecated)
nmap -Pn [target]          # Assume host is online (skip host discovery)
```

### **2. Port Scanning**
```bash
nmap -sS [target]          # TCP SYN scan (stealth scan)
nmap -sT [target]          # TCP connect scan (full connection)
nmap -sU [target]          # UDP scan
nmap -sA [target]          # TCP ACK scan
nmap -sW [target]          # TCP Window scan
nmap -sM [target]          # TCP Maimon scan
```

### **3. Service Version Detection**
```bash
nmap -sV [target]          # Version detection
nmap -A [target]           # Comprehensive scan (OS detection + version + script)
nmap -O [target]           # OS detection
```

## **Advanced Scanning Techniques**

### **4. Script Scanning**
```bash
nmap -sC [target]          # Default scripts scan
nmap --script [script] [target]  # Specific script
nmap --script-all [target]  # All available scripts
nmap --script-updatedb     # Update script database
```

### **5. Aggressive Scanning**
```bash
nmap -T4 [target]          # Timing template (0-5, higher is faster)
nmap -F [target]           # Fast scan (100 most common ports)
nmap -p- [target]          # Scan all 65535 ports
nmap -p 1-65535 [target]   # Same as above
```

### **6. Output Options**
```bash
nmap -oN output.txt [target]  # Normal output
nmap -oX output.xml [target]  # XML output
nmap -oG output.gnmap [target] # Grepable output
nmap -oA output [target]     # Output all formats
```

## **Target Specification**

### **7. Target Selection**
```bash
nmap 192.168.1.1            # Single IP
nmap 192.168.1.1-20         # IP range
nmap 192.168.1.0/24         # CIDR notation
nmap domain.com            # Domain name
nmap [file.txt]            # Input from file
```

### **8. Port Specification**
```bash
nmap -p 80 [target]        # Single port
nmap -p 80,443 [target]    # Multiple ports
nmap -p 1-100 [target]     # Port range
nmap -p U:53,T:21-25,80 [target]  # UDP and TCP ports
```

## **CEH Exam Essential Commands**

### **9. Common CEH Commands**
```bash
# Basic network scan
nmap -sS -sV -O -A [target]  # Comprehensive scan

# Web server scan
nmap -p 80,443 --script http-enum [target]

# SMB enumeration
nmap -p 445 --script smb-enum-shares [target]

# SNMP enumeration
nmap -sU -p 161 --script snmp-netstat [target]

# DNS zone transfer
nmap -p 53 --script dns-zone-transfer [target]
```

### **10. Firewall/IDS Evasion**
```bash
nmap -f [target]           # Fragment packets
nmap -D RND:10 [target]    # Decoy scan
nmap -S [fake_ip] [target] # Spoof source IP
nmap --source-port 53 [target] # Use specific source port
nmap --mtu 24 [target]     # Set MTU
```

## **Tips for CEH Exam:**
1. Remember the timing templates (-T0 to -T5)
2. Know the difference between TCP scan types
3. Understand script categories (--script-help)
4. Practice output interpretation
5. Remember common port numbers and services
6. Know how to use Nmap for vulnerability scanning

Would you like me to explain any specific command in more detail?
