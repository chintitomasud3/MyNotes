# **Core Security Principles**

## **CIA Triad**
- **Confidentiality**: Protect data from unauthorized access (e.g., encryption, access controls).
- **Integrity**: Ensure data is accurate and unaltered (e.g., hashing, checksums).
- **Availability**: Keep systems and data accessible to authorized users (e.g., redundancy, DDoS protection).

## **AAA Framework**
- **Authentication**: Verify identity (e.g., passwords, biometrics, MFA).
- **Authorization**: Determine permissions (e.g., role-based access control).
- **Accounting**: Track actions (e.g., logs, audits).
- **Non-repudiation**: Ensure a party cannot deny an action (e.g., digital signatures).

## **Fundamental Security Models**
- **Least Privilege**: Users/processes only get access needed for their tasks.
- **Defense-in-Depth**: Layered security (e.g., firewall + antivirus + encryption).
- **Zero Trust**: Assume no user or device is trusted by default—verify everything.
- **Separation of Duties**: Split critical tasks to prevent fraud/abuse (e.g., one person creates accounts, another approves them).

## **Types of Security Controls**
- **Preventive**: Stop incidents (e.g., firewalls, locks).
- **Detective**: Identify incidents (e.g., IDS, logs).
- **Corrective**: Fix damage (e.g., backups, patches).
- **Deterrent**: Discourage attacks (e.g., warning banners).
- **Compensating**: Alternative controls when primary ones fail (e.g., manual logs if automated logging fails).
- **Physical/Technical/Administrative**: Locks (physical), encryption (technical), policies (administrative).

## **Emerging Trends and Concepts**
- **Cloud Security**: Shared responsibility model—provider secures infrastructure, you secure data/configurations.
- **Internet of Things (IoT)**: Weak security in devices (e.g., default passwords) increases attack surface.
- **Artificial Intelligence (AI)**: Used in attacks (e.g., deepfakes) and defenses (e.g., anomaly detection).
- **Supply Chain Security**: Risks from third-party vendors (e.g., SolarWinds attack).
- **Automation**: Streamlines security ops (e.g., SOAR tools).

## **Key Terms to Know**
- **Threat**: Potential danger (e.g., malware).
- **Vulnerability**: Weakness (e.g., unpatched software).
- **Risk**: Likelihood and impact of a threat exploiting a vulnerability.
- **Exploit**: Method to take advantage of a vulnerability.
- **Mitigation**: Reducing risk (e.g., applying updates).

## **Practical Examples**
- **CIA in Action**: Encrypting a file (confidentiality), using a hash to verify it (integrity), and hosting it on a redundant server (availability).
- **Zero Trust**: Requiring MFA even for internal network access.
- **Defense-in-Depth**: A company uses a firewall, antivirus, and employee training to protect against phishing.

## **Exam Focus**
- **Scenarios**: You might see questions like, “Which control prevents unauthorized access?” (Answer: Preventive—e.g., a firewall).
- **Definitions**: Know the difference between detective (e.g., IDS) and corrective (e.g., restoring from backup).
- **Trends**: Be ready for questions on cloud or IoT security challenges.
![image](https://github.com/user-attachments/assets/9404fd83-0f94-488b-ad16-a9c97caccf94)
