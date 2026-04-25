#  Cybersecurity HomeLab

![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kali-linux&logoColor=white)
![VirtualBox](https://img.shields.io/badge/VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)
![Metasploit](https://img.shields.io/badge/Metasploit-2596CD?style=for-the-badge&logo=metasploit&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)

A hands-on cybersecurity home lab built to simulate real-world attack and defense scenarios using virtualized environments.

---

## 🖧 Network Architecture

> ![Network Diagram](diagram.png)

| Machine | OS | IP Address | Role |
|---|---|---|---|
| Kali Linux | Debian-based | 192.168.56.102 | Attacker |
| Metasploitable 2 | Ubuntu 8.04 | 192.168.56.101 | Vulnerable Target |
| Ubuntu Server | Ubuntu 24.04 | 192.168.56.103 | Realistic Target |

All VMs are connected via a **Host-Only network** (isolated from the internet) inside VirtualBox.

---

## Completed Tasks

### Network Reconnaissance
- Configured isolated lab network with 3 virtual machines
- Performed full Nmap scan with OS detection and service versioning
- Captured and analyzed network traffic with Wireshark (ICMP, ARP, TCP)

### Vulnerability Assessment & Exploitation
- Identified 20+ open ports and critical services on Metasploitable 2
- Exploited **CVE-2007-2447** (Samba usermap_script) using Metasploit
- Obtained **root shell** on target system
- Accessed `/etc/passwd` and `/etc/shadow` — full system compromise demonstrated

### Network Defense *(in progress)*
- Firewall configuration with iptables
- Intrusion Detection System with Snort/Suricata
- Attack simulation and alert verification

---

##  Key Findings

| CVE | Service | Severity | Impact |
|---|---|---|---|
| CVE-2007-2447 | Samba 3.0.20 | **CRITICAL (10.0)** | Remote Code Execution → Root |
| CVE-2011-2523 | vsftpd 2.3.4 | **CRITICAL** | Backdoor → Root shell |
| N/A | Telnet (port 23) | **HIGH** | Credentials transmitted in plaintext |
| N/A | Bindshell (port 1524) | **CRITICAL** | Root shell exposed directly |
| N/A | MySQL (port 3306) | **HIGH** | Unauthenticated access possible |

---

##  Tools Used

- **Nmap** — Network scanning and service enumeration
- **Wireshark** — Packet capture and traffic analysis  
- **Metasploit Framework** — Exploitation
- **VirtualBox** — Virtualization platform

---

## Repository Structure
Cybersecurity-HomeLab/
├── README.md
├── images/              # Screenshots and diagrams
├── reports/
│   ├── nmap-report.md   # Full Nmap findings
│   └── pentest-report.md # Penetration test report
└── configs/
└── network-setup.md  # Lab setup guide

---

## Disclaimer

This lab is built exclusively for **educational purposes** in an isolated virtual environment. All attacks were performed only on intentionally vulnerable machines. No real systems were harmed.

---

**Author:** AdrianFlorin07 | [GitHub](https://github.com/AdrianFlorin07)

