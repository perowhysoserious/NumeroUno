# Automated Security Hardening & Compliance Auditing (Debian 13)

## Project
Automated security hardening and compliance auditing solution for Linux OS (Debian 13), demonstrating IaC security practices. This project implements CIS Benchmark Level 1 controls using Ansible, achieving an improvement in security posture (Lynis score: 35 → 65).

## ️ Tech
 OS:Debian 13 (Testing)
 Automation: Ansible
 Auditing:Lynis Security Auditor
 Standards: CIS Debian 11 Benchmark (Adapted for Debian 13)

## Quick Start

### Prerequisites
- Debian 11/12/13 system (VM)
- Ansible 2.9+
- SSH access to target system

### Deployment

# Clone repository
git clone https://github.com/perowhysoserious/NumeroUno.git
cd NumeroUno

# Update hosts.ini with your target system
nano hosts.ini

# Run hardening playbook
ansible-playbook -i hosts.ini harden.yml

# Validate with Lynis
lynis audit system

### What Gets Configured
- SSH hardening (disable root login, key-only auth)
- Password complexity enforcement
- USB storage kernel module blacklisting
- Audit logging (systemd-journald)
- System use notification banners
- Core CIS Level 1 benchmarks

##  Security Controls Implemented
| Control Category | Technical Action | Result |
 
 Identity & Auth | Disabled Root SSH login; Enforced Password Complexity | Implemented |
 System Protection | Blacklisted `usb-storage` kernel modules | Implemented |
 System Monitoring | Configured `systemd-journald` for audit trails | Implemented |
 Legal Compliance | Deployed mandatory System Use Banners (MOTD) | Implemented |

## Results
The system's security posture was validated by using Lynis. 
 Pre-Hardening Score:35
 Post-Hardening Score:65
 Status: Compliant with Core CIS Level 1 Requirements.

![Lynis Score](lynis_score.png)

## Lessons Learned
 Version Adaptation: Successfully adapted a Debian 11 CIS role for Debian 13 by implementing variable overrides.
 Conflict Resolution: Identified and resolved a kernel module conflict where `usb-storage` was held open by the UTM hypervisor.
 Validation: I built the playbook to check the system state before acting and added an automated Lynis audit to verify the security results.


