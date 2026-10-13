# Wazuh Monitoring

Wazuh is the central monitoring and detection platform of the lab. It collects and analyzes telemetry from the Windows 11 endpoint (WCLIENT).

- **Wazuh server:** 192.168.20.116 (Ubuntu Server)
- **Monitored endpoint:** WCLIENT (192.168.20.20)

## Architecture

```
WCLIENT
   │  Wazuh Agent
   ▼
Wazuh Manager ──▶ Wazuh Indexer ──▶ Wazuh Dashboard
```

## Data Sources

| Source | Purpose |
|---|---|
| Windows Security events | Authentication and account activity |
| Sysmon | Process creation, network connections, image loading |
| File Integrity Monitoring (FIM) | Detect changes in monitored files |
| Security Configuration Assessment (SCA) | Compare configuration with the CIS Microsoft Windows 11 Enterprise Benchmark |
| Syscollector | System inventory (hardware, OS, network, packages, ports, processes, users, groups, services, browser extensions) |
| PowerShell logs | Monitor PowerShell activity |

## Sysmon

Sysmon is installed on WCLIENT as the `Sysmon64` service. The key event is **Event ID 1: Process Creation**, which is retrieved with `Get-WinEvent` and visible in Wazuh.

## File Integrity Monitoring

A test directory was created for FIM:

```powershell
New-Item -ItemType Directory -Path C:\SecureCorp-Test -Force
```

Wazuh Discover displayed the real-time events generated for `C:\SecureCorp-Test`.

## Security Configuration Assessment

The SCA module uses the CIS Microsoft Windows 11 Enterprise Benchmark to identify compliant and non-compliant controls and to track improvements in security posture.

## Syscollector

Inventory scan runs about every hour, with an additional scan at startup.

## Windows Security Events Studied

| Event ID | Description |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4688 | Process creation |
| 4720 | User account created |
| 4728 | Member added to a security-enabled global group |
| 4732 | Member added to a security-enabled local group |

## PowerShell Monitoring

The `Microsoft-Windows-PowerShell/Operational` log is collected. Legitimate commands such as `Get-Process` and `Get-Service` were run to generate and verify events in Wazuh.

## Screenshots

- `evidence/screenshots/fig12-wazuh-dashboard.png`
- `evidence/screenshots/fig13-sysmon-event-id-1.png`
- `evidence/screenshots/fig14-sysmon-service.png`
- `evidence/screenshots/fig15-fim-test-directory.png`
- `evidence/screenshots/fig16-wazuh-fim-events.png`
- `evidence/screenshots/fig17-event-4625.png`
- `evidence/screenshots/fig18-event-4624.png`
- `evidence/screenshots/fig19-event-4688.png`
- `evidence/screenshots/fig20-event-4728.png`
- `evidence/screenshots/fig21-powershell-log.png`
- `evidence/screenshots/fig22-powershell-wazuh.png`
