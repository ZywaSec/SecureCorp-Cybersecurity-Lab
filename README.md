# 🛡️ SecureCorp Cybersecurity Lab
Enterprise cybersecurity lab for offensive security, defensive monitoring, Active Directory, SIEM and endpoint security.

![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-red?style=for-the-badge)
![VirtualBox](https://img.shields.io/badge/Virtualization-VirtualBox-blue?style=for-the-badge)
![OPNsense](https://img.shields.io/badge/Firewall-OPNsense-orange?style=for-the-badge)
![Windows Server](https://img.shields.io/badge/AD-Windows%20Server-0078D4?style=for-the-badge)
![Kali Linux](https://img.shields.io/badge/Attack-Kali%20Linux-557C94?style=for-the-badge)
![Wazuh](https://img.shields.io/badge/SIEM-Wazuh-4C8BF5?style=for-the-badge)
![Sysmon](https://img.shields.io/badge/Monitoring-Sysmon-purple?style=for-the-badge)

> **An isolated enterprise-style cybersecurity laboratory designed to practice offensive security, Active Directory security, endpoint monitoring, SIEM, threat detection and security analysis.**

---

## 📑 Table of Contents

- [About the Project](#-about-the-project)
- [Objectives](#-objectives)
- [Architecture](#-architecture)
- [Network Architecture](#-network-architecture)
- [Virtual Machines](#-virtual-machines)
- [Security Components](#-security-components)
- [Active Directory](#-active-directory)
- [BloodHound](#-bloodhound)
- [Wazuh](#-wazuh)
- [Sysmon](#-sysmon)
- [File Integrity Monitoring](#-file-integrity-monitoring)
- [Security Configuration Assessment](#-security-configuration-assessment)
- [Offensive Security](#-offensive-security)
- [Detection Pipeline](#-detection-pipeline)
- [Security Scenarios](#-security-scenarios)
- [Evidence](#-evidence)
- [Repository Structure](#-repository-structure)
- [Skills Demonstrated](#-skills-demonstrated)
- [Challenges](#-challenges)
- [Future Improvements](#-future-improvements)
- [Ethical Scope](#-ethical-scope)
- [Project Status](#-project-status)
- [Author](#-author)

---

# 🔎 About the Project

**SecureCorp Cybersecurity Lab** is a virtual enterprise cybersecurity environment created to reproduce a small corporate infrastructure inside an isolated laboratory.

The project combines both **offensive security** and **defensive security** activities.

The laboratory is designed to simulate a realistic workflow:

```text
Reconnaissance
      ↓
Network Enumeration
      ↓
Active Directory Enumeration
      ↓
Controlled Security Testing
      ↓
Endpoint Telemetry
      ↓
Wazuh Detection
      ↓
Investigation
      ↓
MITRE ATT&CK Analysis

The main objective is to understand how an attacker can interact with an enterprise environment and how defensive technologies can detect and investigate the resulting activity.

🎯 Objectives

The main objectives of the project are:

Build an isolated enterprise-style virtual network.
Configure network segmentation using OPNsense.
Deploy a Windows Server Active Directory environment.
Join a Windows client to the domain.
Perform controlled reconnaissance from Kali Linux.
Enumerate Active Directory.
Analyze AD relationships using BloodHound.
Deploy Wazuh as a SIEM and security monitoring platform.
Deploy Wazuh agents on Windows endpoints.
Install and configure Sysmon.
Monitor Windows security events.
Implement File Integrity Monitoring.
Perform Security Configuration Assessment.
Generate controlled security events.
Detect and investigate events through Wazuh.
Relate security events to MITRE ATT&CK techniques.
Document the complete environment as a cybersecurity portfolio project.
🏗️ Architecture

The laboratory is built using VirtualBox and consists of several virtual machines connected through isolated virtual networks.

High-Level Architecture
🌐 Network Architecture

The laboratory uses several isolated network segments.

Network	Subnet	Purpose
NAT Network	192.168.100.0/24	Internet / external connectivity
Corporate Network	192.168.20.0/24	Internal enterprise network
Attack Network	192.168.10.0/24	Offensive security testing
Target Network	192.168.50.0/24	Isolated target systems
Host-only Network	192.168.56.0/24	Host/lab management
Network Topology

The detailed network topology is available in:

architecture/network-topology.png

🖥️ Virtual Machines
Machine	Operating System	Role
OPNsense	OPNsense	Firewall / Router
SERVER01	Windows Server	Domain Controller / Active Directory
WCLIENT	Windows	Domain Client / Endpoint
Kali Linux	Kali Linux	Offensive Security
Wazuh	Ubuntu Server	SIEM / Security Monitoring
Main Domain
securecorp.local
Domain Controller
SERVER01.securecorp.local
Wazuh Server
Ubuntu

The Wazuh server is deployed on the corporate network.

🔐 Security Components

The laboratory combines multiple security technologies:

Technology	Role
VirtualBox	Virtualization
OPNsense	Firewall and network segmentation
Windows Server	Active Directory
Windows Client	Endpoint
Kali Linux	Offensive security
BloodHound	Active Directory analysis
Wazuh	SIEM / XDR / monitoring
Sysmon	Endpoint telemetry
MITRE ATT&CK	Attack technique mapping
🏢 Active Directory

The laboratory contains an Active Directory domain:

securecorp.local

The Domain Controller is:

SERVER01.securecorp.local

The Active Directory environment includes:

Users
Groups
Organizational Units
Group Policies
Domain Controller
Windows domain client
Documentation

Detailed Active Directory documentation is available in:

active-directory/domain-structure.md
active-directory/organizational-units.md
active-directory/users-and-groups.md
active-directory/bloodhound-analysis.md
🕵️ BloodHound

BloodHound is used to analyze relationships inside the Active Directory environment.

The laboratory uses bloodhound-python from Kali Linux to collect Active Directory information.

The collection includes information about:

Users
Groups
Computers
Domains
Organizational Units
Group Policy Objects
Collection Workflow
Kali Linux
     ↓
bloodhound-python
     ↓
Active Directory
     ↓
Collection Files
     ↓
BloodHound
     ↓
Relationship Analysis

The objective is to understand:

Identity relationships
Group memberships
Privilege relationships
Potential attack paths
Active Directory security weaknesses

Detailed documentation:

active-directory/bloodhound-analysis.md

🛡️ Wazuh

Wazuh is the main security monitoring and SIEM platform used in the laboratory.

The Wazuh environment includes:

Wazuh Manager
      │
      ├── Wazuh Indexer
      │
      └── Wazuh Dashboard
             │
             ↑
       Wazuh Agent
             ↑
       Windows Client
Main Functions
Security event monitoring
Endpoint monitoring
Log collection
File Integrity Monitoring
Security Configuration Assessment
Windows event analysis
Sysmon event collection
Security alerting
Threat detection
Wazuh Documentation
wazuh/installation.md
wazuh/agent-deployment.md
wazuh/sysmon.md
wazuh/fim.md
wazuh/sca.md
wazuh/detection-rules.md
🔬 Sysmon

Microsoft Sysmon is installed on the Windows endpoint to provide detailed system activity telemetry.

Current version used in the laboratory:

Sysmon 15.22

Sysmon provides visibility into activities such as:

Process creation
Network connections
Process execution
Registry activity
File activity
PowerShell activity
Example Detection Flow
Windows Endpoint
       ↓
     Sysmon
       ↓
Windows Event Logs
       ↓
 Wazuh Agent
       ↓
 Wazuh Manager
       ↓
Wazuh Dashboard

One important event monitored during the laboratory is:

Event ID 1 — Process Creation

Documentation:

wazuh/sysmon.md

📁 File Integrity Monitoring

File Integrity Monitoring is used to detect changes to monitored files and directories.

A dedicated test directory is used:

C:\SecureCorp-Test
Validation Scenario
Create File
     ↓
Modify File
     ↓
Delete File
     ↓
Wazuh Detection
     ↓
Security Alert

The objective is to verify that changes on the Windows endpoint are detected and reported by Wazuh.

Documentation:

wazuh/fim.md

📊 Security Configuration Assessment

Wazuh SCA is used to evaluate the security configuration of the Windows endpoint.

The laboratory produced the following observed results:

Result	Count
Passed	124
Failed	348
Not Applicable	10

These results are used as a configuration baseline to identify security hardening opportunities.

Documentation:

wazuh/sca.md

⚔️ Offensive Security

Kali Linux is used as the main offensive security platform.

All offensive activities are performed against systems belonging to the isolated laboratory.

Workflow
Reconnaissance
      ↓
Nmap Scanning
      ↓
Service Enumeration
      ↓
Authentication Testing
      ↓
Controlled Attack Scenario
      ↓
Wazuh Detection
      ↓
Investigation
Documentation
offensive-security/reconnaissance.md
offensive-security/nmap.md
offensive-security/authentication-testing.md
offensive-security/attack-scenarios.md
🔎 Detection Pipeline

The main objective of the laboratory is to connect offensive activity with defensive detection.

This architecture demonstrates a simplified attack → telemetry → detection → investigation workflow.

🚨 Security Scenarios

The laboratory can be used to simulate several controlled security scenarios.

Scenario 1 — Network Reconnaissance
Kali Linux
    ↓
Network Discovery
    ↓
Nmap
    ↓
Service Enumeration
Scenario 2 — Active Directory Enumeration
Kali Linux
    ↓
AD Enumeration
    ↓
BloodHound Collection
    ↓
Relationship Analysis
Scenario 3 — Process Monitoring
Windows
    ↓
Process Execution
    ↓
Sysmon Event ID 1
    ↓
Wazuh
    ↓
Alert / Investigation
Scenario 4 — File Modification
C:\SecureCorp-Test
       ↓
File Created / Modified / Deleted
       ↓
Wazuh FIM
       ↓
Security Alert
📸 Evidence

Evidence and screenshots are stored in:

evidence/screenshots/

The evidence structure is organized by laboratory phase:

evidence/
└── screenshots/
    ├── 01-infrastructure/
    ├── 02-network/
    ├── 03-active-directory/
    ├── 04-bloodhound/
    ├── 05-wazuh/
    ├── 06-sysmon/
    └── 07-offensive-security/

Screenshots are used to document:

Virtual machines
Network configuration
Active Directory
BloodHound
Wazuh
Sysmon
Security testing
Detection results
📂 Repository Structure
SecureCorp-Cybersecurity-Lab/
│
├── README.md
├── LICENSE
│
├── active-directory/
│   ├── bloodhound-analysis.md
│   ├── domain-structure.md
│   ├── organizational-units.md
│   └── users-and-groups.md
│
├── architecture/
│   └── network-topology.png
│
├── docs/
│   └── SecureCorp-Lab-Technical-Report.md
│
├── evidence/
│   └── screenshots/
│
├── offensive-security/
│   ├── attack-scenarios.md
│   ├── authentication-testing.md
│   ├── nmap.md
│   └── reconnaissance.md
│
└── wazuh/
    ├── agent-deployment.md
    ├── detection-rules.md
    ├── fim.md
    ├── installation.md
    ├── sca.md
    └── sysmon.md
🧠 Skills Demonstrated

This project demonstrates practical experience with:

Networking
Network segmentation
Virtual networking
Firewall configuration
Routing
TCP/IP
Network reconnaissance
Port and service enumeration
Active Directory
Active Directory deployment
Domain management
Users and groups
Organizational Units
Group Policies
AD enumeration
BloodHound analysis
Offensive Security
Reconnaissance
Nmap
Service enumeration
Authentication testing
Controlled attack scenarios
Defensive Security
SIEM deployment
Wazuh
Windows monitoring
Sysmon
File Integrity Monitoring
Security Configuration Assessment
Security event investigation
Security Analysis
Log analysis
Detection engineering
Alert investigation
MITRE ATT&CK mapping
Attack-to-detection correlation
🧩 Challenges

During the development of the laboratory, several technical challenges were encountered, including:

Virtual network configuration
Firewall and routing troubleshooting
Communication between isolated networks
Active Directory configuration
Wazuh deployment and configuration
Wazuh agent connectivity
Sysmon integration
Windows event collection
Detection validation

These challenges provided practical experience in troubleshooting complex cybersecurity infrastructures.

🚀 Future Improvements

Planned improvements include:

Advanced Wazuh detection rules
More Sysmon telemetry
Custom MITRE ATT&CK mappings
Additional Active Directory attack simulations
Improved network segmentation
Additional Windows endpoints
Linux endpoint monitoring
Automated attack simulations
Security dashboards
Incident response playbooks
Detection engineering documentation
Additional SOC scenarios
🔐 Ethical Scope

This project is designed exclusively for education, cybersecurity training and authorized security testing.

All offensive security activities are performed inside an isolated laboratory environment under controlled conditions.

No unauthorized systems, networks or accounts are targeted.

📈 Project Status

Status: 🟡 In Progress

Completed / Implemented
 VirtualBox laboratory environment
 OPNsense firewall
 Network segmentation
 Active Directory
 Windows domain client
 BloodHound collection
 Wazuh deployment
 Wazuh agent
 Sysmon installation
 File Integrity Monitoring testing
 Security Configuration Assessment
 Offensive security documentation
In Progress
 Complete detection rule documentation
 Complete evidence screenshots
 MITRE ATT&CK mapping
 Final validation
 Complete technical report
👩‍💻 Author

Fatima Ezzahrae Ouhmich

Cybersecurity and Embedded Systems Engineering Student
ENSA Tétouan — Morocco

⭐ Project

SecureCorp Cybersecurity Lab

A practical cybersecurity laboratory combining:

Offensive Security + Active Directory + SIEM + Endpoint Monitoring + Detection Engineering


### ⚠️ Petite correction importante avant de le publier

Dans ton README, j'ai volontairement gardé les informations réseau générales que nous avons déjà définies, mais **ne mets pas dans un dépôt public** les mots de passe Wazuh, comptes AD, tokens, clés privées ou autres secrets.

Et pour les IP précises des machines, je te conseille de ne les ajouter au README **qu'après vérification de tes valeurs finales** dans VirtualBox/OPNsense.

**Tu peux maintenant remplacer entièrement ton `README.md` actuel par ce contenu.**
