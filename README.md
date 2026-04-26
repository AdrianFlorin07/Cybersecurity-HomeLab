# Cybersecurity HomeLab

![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kali-linux&logoColor=white)
![VirtualBox](https://img.shields.io/badge/VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)
![Metasploit](https://img.shields.io/badge/Metasploit-2596CD?style=for-the-badge&logo=metasploit&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)
![Snort](https://img.shields.io/badge/Snort-CC0000?style=for-the-badge&logo=snort&logoColor=white)

A hands-on cybersecurity home lab built to simulate real-world attack and defense scenarios using virtualized environments.

---

## Network Architecture

![Network Diagram](CyberSecurity-HomeLab/Images/Diagram.png)

| Machine | OS | IP Address | Role |
|---|---|---|---|
| Kali Linux | Debian-based | 192.168.56.102 | Attacker |
| Metasploitable 2 | Ubuntu 8.04 | 192.168.56.101 | Vulnerable Target |
| Ubuntu Server | Ubuntu 24.04 | 192.168.56.103 | Realistic Target |

All VMs are connected via a **Host-Only network** (isolated from the internet) inside VirtualBox.

---

### Network Reconnaissance
- Configured isolated lab network with 3 virtual machines
- Performed full Nmap scan with OS detection and service versioning
- Captured and analyzed network traffic with Wireshark (ICMP, ARP, TCP)

| Nmap Scan | Wireshark Capture |
|---|---|
| ![Nmap1](CyberSecurity-HomeLab/Images/Nmap1.png) | ![PCAP](CyberSecurity-HomeLab/Images/PCAP1.png) |
| ![Nmap2](CyberSecurity-HomeLab/Images/Nmap2.png) | |
| ![Nmap3](CyberSecurity-HomeLab/Images/Nmap3.png) | |

---

### Vulnerability Assessment & Exploitation
- Identified 23 open ports and critical services on Metasploitable 2
- Exploited **CVE-2007-2447** (Samba usermap_script) using Metasploit Framework
- Obtained **root shell** on target system
- Accessed `/etc/passwd` and `/etc/shadow` — full system compromise demonstrated

| Metasploit Exploit | Root Shell + /etc/shadow |
|---|---|
| ![meta1](CyberSecurity-HomeLab/Images/meta1.png) | ![meta2](CyberSecurity-HomeLab/Images/meta2.png) |

---

### Network Defense
- Deployed **Snort IDS 3.12** with custom ICMP detection rules
- Simulated attack detected in real time — **11 alerts** on 14 analyzed packets
- Configured iptables firewall rules on Ubuntu Server

| Snort Alerts | Snort Statistics |
|---|---|
| ![snort1](CyberSecurity-HomeLab/Images/snort1.png) | ![snort2](CyberSecurity-HomeLab/Images/snort2.png) |

---

## Key Findings

| CVE | Service | Severity | Impact |
|---|---|---|---|
| CVE-2007-2447 | Samba 3.0.20 | **CRITICAL (10.0)** | Remote Code Execution → Root |
| CVE-2011-2523 | vsftpd 2.3.4 | **CRITICAL** | Backdoor → Root shell |
| N/A | Telnet (port 23) | **HIGH** | Credentials transmitted in plaintext |
| N/A | Bindshell (port 1524) | **CRITICAL** | Root shell exposed directly |
| N/A | MySQL (port 3306) | **HIGH** | Unauthenticated access possible |

---

## Tools Used

| Tool | Purpose |
|---|---|
| **Nmap** | Network scanning and service enumeration |
| **Wireshark** | Packet capture and traffic analysis |
| **Metasploit Framework** | Exploitation |
| **Snort IDS 3.12** | Intrusion detection |
| **VirtualBox** | Virtualization platform |

---

## Repository Structure

Cybersecurity-HomeLab/
├── README.md
├── CyberSecurity-HomeLab/
│   ├── Images/          # Screenshots and diagrams
│   ├── Reports/
│   │   ├── nmap-report.md
│   │   └── pentest-report.md
│   └── Configs/
│       └── network-setup.md


---

## Disclaimer

This lab is built exclusively for **educational purposes** in an isolated virtual environment. All attacks were performed only on intentionally vulnerable machines. No real systems were harmed.

---

**Author:** AdrianFlorin07 | [GitHub](https://github.com/AdrianFlorin07)
