# Network Scanning & Enumeration Report

## Objective
The objective of this project was to perform a comprehensive network scanning and enumeration assessment on a target system in a controlled lab environment. The assessment aimed to identify open ports, running services, service versions, and security vulnerabilities using Nmap, without performing exploitation.

---

## Scope
- **Target System:** Intentionally vulnerable lab machine (Metasploitable)
- **Assessment Type:** Full TCP Network Reconnaissance & Enumeration
- **Environment:** Local virtual lab
- **Exploitation:** Not performed

---

## Tools Used
- Kali Linux
- Nmap

---

## Methodology
The assessment followed a structured and ethical approach:
- Conducted a full TCP port scan (`-p-`) to identify all exposed services.
- Performed service and version detection to identify outdated or risky software.
- Executed OS fingerprinting to determine system-level exposure.
- Ran Nmap NSE vulnerability scripts to detect known vulnerabilities.
- Reviewed the complete scan output and categorized findings based on risk severity.

---

## Findings Summary

### Critical Risk Findings
- **Java RMI (Port 1099):** Identified with a default configuration remote code execution vulnerability.
- **Distccd (Port 3632):** Known remote command execution vulnerability detected.
- **Bindshell (Port 1524):** Remote shell access exposed, allowing direct command execution.
- **UnrealIRCd (Port 6667):** Backdoored version detected, posing a critical compromise risk.

---

### High Risk Findings
- **FTP (Port 21):** Anonymous login enabled on an outdated vsftpd service.
- **Telnet (Port 23):** Plaintext authentication protocol exposed.
- **SMB (Ports 139/445):** File-sharing services exposed, increasing lateral movement risk.
- **Apache Tomcat (Port 8180):** Vulnerable to Slowloris Denial of Service attack.
- **PostgreSQL (Port 5432):** Outdated database service with multiple known vulnerabilities.
- **X11 (Port 6000):** Exposed graphical service allowing potential keystroke interception.

---

### Medium Risk Findings
- **Apache HTTP (Port 80):** Outdated web server version detected.
- **NFS (Port 2049):** Network file-sharing service exposed.
- **MySQL (Port 3306):** Database service exposed to the network.
- **VNC (Port 5900):** Remote desktop service exposed without network restrictions.
- **AJP (Port 8009):** Internal Tomcat connector exposed externally.

---

### Low Risk & Informational Findings
- **SSH (Port 22):** Secure remote access service exposed.
- **SMTP (Port 25):** Mail transfer service detected.
- **DNS (Port 53):** Domain name service exposed.
- **RPC (Port 111):** Auxiliary system service detected.

---

## OS-Level Observation
- The target system was identified as running an **outdated Linux 2.6.x kernel**, increasing exposure to known system-level vulnerabilities.

---

## Risk Analysis
The assessment revealed multiple critical and high-risk services running on the target system, significantly increasing the overall attack surface. Outdated software versions, legacy protocols, and misconfigured services contribute to a high likelihood of system compromise if left unpatched.

---

## Recommendations
- Disable unnecessary and legacy services such as Telnet, R services, and Bindshell.
- Patch or upgrade outdated applications including Apache, PostgreSQL, Tomcat, and UnrealIRCd.
- Restrict access to remote services using firewall rules and network segmentation.
- Upgrade the operating system to a supported and secure version.
- Perform regular vulnerability assessments and continuous monitoring.

---

## Conclusion
This project demonstrates how network scanning and enumeration can effectively identify exposed services, outdated software, and critical vulnerabilities without exploitation. The findings highlight the importance of reducing attack surface and maintaining proper system hardening.

---

## Disclaimer
This assessment was conducted in a controlled lab environment for educational purposes only. No unauthorized systems were scanned.
