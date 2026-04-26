# Network Scan Report — Metasploitable 2

**Date:** April 25, 2026
**Tester:** AdrianFlorin07
**Target:** 192.168.56.101 (Metasploitable 2)
**Tool:** Nmap 7.99
**Command:** `nmap -sV -O -A 192.168.56.101`

---

## Methodology

Full TCP scan with OS detection, service version enumeration and default script scanning (-A flag). Performed from Kali Linux (192.168.56.102) over an isolated Host-Only network.

---

## Open Ports & Services

| Port | Protocol | Service | Version | Severity |
|------|----------|---------|---------|----------|
| 21 | TCP | FTP | vsftpd 2.3.4 |  CRITICAL |
| 22 | TCP | SSH | OpenSSH 4.7p1 |  MEDIUM |
| 23 | TCP | Telnet | Linux telnetd |  CRITICAL |
| 25 | TCP | SMTP | Postfix smtpd |  MEDIUM |
| 53 | TCP | DNS | ISC BIND 9.4.2 |  MEDIUM |
| 80 | TCP | HTTP | Apache 2.2.8 |  MEDIUM |
| 111 | TCP | RPCbind | v2 |  LOW |
| 139 | TCP | Samba | 3.0.20-Debian |  CRITICAL |
| 445 | TCP | Samba | 3.0.20-Debian |  CRITICAL |
| 512 | TCP | exec | netkit-rsh |  CRITICAL |
| 513 | TCP | login | rlogind |  CRITICAL |
| 514 | TCP | shell | rshd |  CRITICAL |
| 1524 | TCP | bindshell | root shell |  CRITICAL |
| 2049 | TCP | NFS | v2-4 |  MEDIUM |
| 3306 | TCP | MySQL | 5.0.51a |  CRITICAL |
| 5432 | TCP | PostgreSQL | 8.3.0 |  MEDIUM |
| 5900 | TCP | VNC | Protocol 3.3 |  CRITICAL |
| 6667 | TCP | IRC | UnrealIRCd |  CRITICAL |
| 8180 | TCP | HTTP | Apache Tomcat |  MEDIUM |

**Total open ports: 23**

---

## OS Detection

- **OS:** Linux 2.6.9 - 2.6.33
- **Distribution:** Ubuntu 8.04 (Hardy Heron)
- **Architecture:** i686

---

## Critical Findings

### 1. vsftpd 2.3.4 Backdoor — CVE-2011-2523
- **Port:** 21/TCP
- **Impact:** Unauthenticated remote root access
- **CVSS Score:** 10.0
- **Mitigation:** Upgrade to vsftpd 2.3.5 or later

### 2. Samba usermap_script — CVE-2007-2447
- **Port:** 139/445 TCP
- **Impact:** Unauthenticated remote root code execution
- **CVSS Score:** 10.0
- **Mitigation:** Upgrade to Samba 3.0.25rc4 or later

### 3. Bindshell — Port 1524
- **Port:** 1524/TCP
- **Impact:** Instant root access with no authentication
- **Mitigation:** Close port 1524, audit all running services

### 4. Telnet — Port 23
- **Impact:** Credentials transmitted in plaintext
- **Mitigation:** Disable Telnet, use SSH only

### 5. MySQL — Port 3306
- **Impact:** Database access without credentials from remote hosts
- **Mitigation:** Bind MySQL to localhost, enforce authentication

---

## Summary

| Severity | Count |
|----------|-------|
| Critical | 8 |
|  Medium | 12 |
|  Low | 3 |
