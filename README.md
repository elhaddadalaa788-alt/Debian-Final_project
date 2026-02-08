# Debian-Final_project
Cybersecurity Final Project – Server Hardening & Incident Response
## Project Overview
This project simulates the recovery and security hardening of a compromised Debian server.  
The objective was to identify vulnerabilities, apply corrective actions, implement security controls, and document the incident response and recovery process according to cybersecurity best practices (NIST SP 800-61 and ISO 27001 principles).
## Environment
- Platform: Oracle VirtualBox
- Operating System: Debian Linux (provided vulnerable VM)
- Tools Used:
  - Nmap
  - rkhunter
  - UFW Firewall
  - SSH configuration tools
  - FTP service configuration
  - Linux system logs
---

## Phase 1 – Evidence Collection and Vulnerability Identification

### Network Scan
A system scan was performed using:

```bash
sudo nmap -sS localhost
```
Open ports detected:

21 (FTP)
22 (SSH)
25 (SMTP)
80 (HTTP)
631 (IPP)
3306 (MySQL)

This confirmed the presence of unnecessary exposed services.

##Rootkit Scan
.System integrity was analyzed using:
```
sudo rkhunter --check
```
Results indicated warnings requiring further monitoring and log review.

Phase 2 – Vulnerability Mitigation
File Permission Hardening

Sensitive WordPress configuration file permissions were corrected:
```
sudo chmod 600 /var/www/html/wp-config.php
```
This restricted unauthorized read access.
SSH Security Hardening

SSH configuration was modified to prevent direct root login:
```
PermitRootLogin no
```

Service restarted:
```
sudo systemctl restart ssh
```
Firewall Implementation

Firewall was enabled and configured:
```
sudo ufw enable
sudo ufw allow 22
sudo ufw allow 80
sudo ufw deny 21
sudo ufw deny 25
sudo ufw deny 3306
```
Verification:
```
sudo ufw status

```
This reduced external attack exposure.

Phase 3 – Incident Response and Recovery Planning
  Security recovery procedures included:

System service validation
Port restriction
Access control hardening
Rootkit inspection
Security monitoring recommendations

Incident handling followed:

Identification
Containment
Eradication
Recovery
Lessons Learned

##Deliverables Included
 #This repository contains:
```
pentest-report.pdf
incident-response-plan.pdf
recovery-plan.pdf
executive-summary.pdf
network-diagram.png
/evidence/ (screenshots of commands and results)

```
Conclusion

The compromised server was successfully analyzed, secured, and hardened using standard cybersecurity methodologies.
All identified vulnerabilities were mitigated, and security controls were implemented to reduce future risk exposure.

This project demonstrates practical application of penetration testing, system hardening, incident response, and recovery planning in a controlled lab environment.













