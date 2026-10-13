# Offensive Security

> **Ethical notice:** All activities were performed inside an isolated virtual lab, on machines owned by the author, for educational purposes only. Never run these techniques against systems you do not own or do not have explicit permission to test.

The goal of this part is not to exploit the lab, but to understand how offensive activity is **generated, collected, analyzed and documented** from a defender's point of view.

## Scenario: Network Reconnaissance

```
Kali (192.168.10.100) ──Nmap──▶ OPNsense ──▶ WCLIENT (192.168.20.20)
```

### Command

```bash
nmap -Pn -sV -sC 192.168.20.20
```

### Results

| Port | State | Service | Version |
|---|---|---|---|
| 135/tcp | open | msrpc | Microsoft Windows RPC |
| 139/tcp | open | netbios-ssn | Microsoft Windows netbios-ssn |
| 445/tcp | open | microsoft-ds | n/a |

The remaining 997 scanned ports were filtered. The scan reported that SMB2 message signing is **enabled and required**.

### Analysis

Reconnaissance identifies the network surface visible from the attack network. It is a preliminary step; the project does not aim to exploit the identified services.

## MITRE ATT&CK Mapping

This is a documentary mapping and does not imply that every technique was fully executed.

| Activity | Technique | Description |
|---|---|---|
| Network scanning | T1046 | Network Service Scanning |
| PowerShell | T1059.001 | Command and Scripting Interpreter: PowerShell |
| Process discovery | T1057 | Process Discovery |
| Account discovery | T1087 | Account Discovery |
| Use of a valid account | T1078 | Valid Accounts (depending on the scenario) |
| Windows logon | Events 4624 / 4625 | Authentication telemetry |
| File monitoring | Wazuh FIM | Integrity monitoring |

## Detection Perspective

| Activity | Visible through |
|---|---|
| Nmap scan | Network activity |
| PowerShell execution | Process and command activity |
| File modification | File Integrity Monitoring |
| Authentication failure | Windows Security event |
| System configuration | Security Configuration Assessment |

## Screenshots

- `evidence/screenshots/fig23-nmap-scan.png`
