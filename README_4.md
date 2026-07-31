# Security Labs — Home Pentest Portfolio

A collection of hands-on security projects completed in a fully isolated home lab, built to practice core offensive and defensive security skills: reconnaissance, vulnerability identification, exploitation, detection engineering, and professional reporting.

**Lab environment:** Kali Linux (attacker), Metasploitable2 (target), and a custom-built Debian web server, all running as VirtualBox VMs on an isolated Internal Network with no route to the host machine, the internet, or any production system. All testing was conducted against intentionally vulnerable training images or infrastructure the author built and owned.

---

## Projects

### 01 — Unauthenticated Remote Code Execution via UnrealIRCd Backdoor
[01-unrealircd-rce/report.docx](./01-unrealircd-rce/report.docx)

Full network penetration test starting from host discovery and a full-port Nmap scan, through identification and exploitation of a known backdoor in UnrealIRCd 3.2.8.1 (CVE-2010-2075), resulting in immediate, unauthenticated **root-level** access to the target.

**Skills demonstrated:** network reconnaissance (`arp-scan`, `nmap`), service enumeration, Metasploit Framework usage, exploit execution, post-exploitation verification, professional report writing.

**Key result:** Unauthenticated root shell obtained with zero credentials required.

---

### 02 — Web Application Exploitation & Privilege Escalation (DVWA on Metasploitable2)
[02-dvwa-privesc/report.docx](./02-dvwa-privesc/report.docx)

A realistic two-stage compromise: exploiting an OS command injection vulnerability in DVWA to gain a low-privileged (`www-data`) reverse shell, followed by manual enumeration and exploitation of a misconfigured SUID `nmap` binary to escalate to full **root** access.

**Skills demonstrated:** web application vulnerability scanning (`nikto`), manual exploitation of OS command injection, reverse shell handling, TTY upgrade techniques, local privilege escalation enumeration (SUID binaries, kernel version, cron), professional report writing.

**Key result:** Full root compromise starting from a public-facing web vulnerability, with no prior credentials.

---

### 03 — Simulated Credential Harvesting & Detection Engineering
[03-credential-harvesting-detection/report.docx](./03-credential-harvesting-detection/report.docx)

A project modeling social-engineering-based credential theft from both sides: a web server was built from scratch and configured to host a simulated login page that silently captures submitted credentials, IP address, and browser fingerprint. A companion detection script was then built to scan the server's own access logs and flag this exact attack pattern.

**Skills demonstrated:** Linux server provisioning (Debian, Apache, PHP), static network configuration, PHP scripting, simulated social-engineering attack construction, Apache log analysis, bash scripting for detection/alerting, blue-team-style reporting.

**Key result:** Successfully captured test credentials end-to-end, then built a working detection script that correctly flagged 100% of test submissions from server-side logs alone.

---

## Methodology

All three projects followed a consistent phase-based approach modeled on real-world security assessment methodology:

1. **Reconnaissance / Setup** — host discovery and service enumeration, or environment provisioning
2. **Vulnerability Identification / Technique Selection** — matching discovered services against known CVEs, or selecting a realistic attack technique to model
3. **Exploitation / Simulation** — gaining code execution or a shell on the target, or executing the simulated attack
4. **Post-Exploitation, Detection & Reporting** — verifying impact, and where applicable, building detective controls, then documenting findings, risk, and remediation in a client-report format

## Disclaimer

All testing in this repository was performed exclusively against intentionally vulnerable training images (Metasploitable2, DVWA) or infrastructure built and owned by the author, inside a fully isolated virtual lab with no connectivity to any production network, third-party system, real domain, or the internet. Project 03's simulated login page used only fictitious test data entered by the author and was never deployed publicly or used against any real person. Nothing in this repository was performed against systems the author does not own or have explicit authorization to test.
