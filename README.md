# Security Labs — Home Pentest Portfolio

A collection of hands-on penetration testing projects completed in a fully isolated home lab, built to practice core offensive security skills: reconnaissance, vulnerability identification, exploitation, and post-exploitation reporting.

**Lab environment:** Kali Linux (attacker) and Metasploitable2 (target), running as VirtualBox VMs on an isolated Internal Network with no route to the host machine, the internet, or any production system. All testing was conducted against intentionally vulnerable training images.

---

## Projects

### 01 — Unauthenticated Remote Code Execution via UnrealIRCd Backdoor
[`/01-unrealircd-rce/report.pdf`](./01-unrealircd-rce/report.pdf)

Full network penetration test starting from host discovery and a full-port Nmap scan, through identification and exploitation of a known backdoor in UnrealIRCd 3.2.8.1 (CVE-2010-2075), resulting in immediate, unauthenticated **root-level** access to the target.

**Skills demonstrated:** network reconnaissance (`arp-scan`, `nmap`), service enumeration, Metasploit Framework usage, exploit execution, post-exploitation verification, professional report writing.

**Key result:** Unauthenticated root shell obtained with zero credentials required.

---

### 02 — Web Application Exploitation & Privilege Escalation (DVWA on Metasploitable2)
[`/02-dvwa-privesc/report.pdf`](./02-dvwa-privesc/report.pdf)

A realistic two-stage compromise: exploiting an OS command injection vulnerability in DVWA to gain a low-privileged (`www-data`) reverse shell, followed by manual enumeration and exploitation of a misconfigured SUID `nmap` binary to escalate to full **root** access.

**Skills demonstrated:** web application vulnerability scanning (`nikto`), manual exploitation of OS command injection, reverse shell handling, TTY upgrade techniques, local privilege escalation enumeration (SUID binaries, kernel version, cron), professional report writing.

**Key result:** Full root compromise starting from a public-facing web vulnerability, with no prior credentials.

---

## Methodology

Both engagements followed a consistent four-phase approach modeled on real-world penetration testing methodology:

1. **Reconnaissance** — host discovery and service/version enumeration
2. **Vulnerability Identification** — matching discovered services/versions against known CVEs and misconfigurations
3. **Exploitation** — gaining code execution or a shell on the target
4. **Post-Exploitation & Reporting** — verifying impact (privilege level, data access) and documenting findings, risk, and remediation in a client-report format

## Disclaimer

All testing in this repository was performed exclusively against intentionally vulnerable training images (Metasploitable2, DVWA) inside a fully isolated virtual lab with no connectivity to any production network, third-party system, or the internet. Nothing here was performed against systems the author does not own or have explicit authorization to test.
