# SecureCorp Cybersecurity Lab

**A Virtualized Enterprise Cybersecurity Environment**

## Overview

SecureCorp Cybersecurity Lab is a hands-on cybersecurity project designed to explore enterprise network security, network segmentation, Active Directory administration, and security monitoring.

The lab combines virtualized infrastructure, firewall controls, a Windows domain environment, Kali Linux for authorized security testing, and Wazuh SIEM for security event monitoring.

## Objectives

- Design a segmented enterprise network.
- Configure firewall rules and network communication controls.
- Deploy and manage a Windows Active Directory domain.
- Monitor Windows security events using Sysmon and Wazuh.
- Investigate failed authentication attempts and file integrity events.
- Practice authorized security testing in an isolated environment.

## Architecture

The lab includes the following components:

| Component | Purpose |
|---|---|
| OPNsense | Firewall and network segmentation |
| Windows Server | Active Directory domain services |
| Windows Client | Domain-joined workstation |
| Kali Linux | Authorized security testing |
| Wazuh SIEM | Security monitoring and event analysis |
| VirtualBox | Virtualization platform |

## Network Segmentation

The virtual environment uses separate private network segments:

- Corporate network: `192.168.20.0/24`
- Security testing network: `192.168.10.0/24`
- Target network: `192.168.50.0/24`

OPNsense is used to control communication between the configured networks.

These addresses belong to the lab environment and should not be interpreted as public infrastructure.

## Security Monitoring

The monitoring activities include:

- Windows event collection
- Sysmon event monitoring
- File Integrity Monitoring (FIM)
- Analysis of failed authentication events
- Investigation of security alerts through Wazuh

## Tools and Technologies

- OPNsense
- VirtualBox
- Windows Server and Active Directory
- Windows client
- Kali Linux
- Wazuh SIEM
- Sysmon
- BloodHound and supporting tools, where applicable

## Evidence and Documentation

The repository is intended to contain:

- Network architecture diagrams
- Firewall configuration evidence
- Active Directory configuration screenshots
- Wazuh dashboards and security events
- Testing methodology and observed results
- Technical documentation

## Security and Ethics

All testing is intended for a controlled, authorized lab environment.

Sensitive credentials, private keys, tokens, and confidential configuration data must not be included in this repository.

## Learning Outcomes

This project supports practical learning in network security, Windows domain administration, security monitoring, log analysis, and defensive security engineering.

## Author

**Fatima Ezzahrae Ouhmich**

Cybersecurity and Embedded Systems Engineering Student

ENSA Tétouan, Morocco

---

*This repository documents a personal cybersecurity lab and its verified configurations and results.*
