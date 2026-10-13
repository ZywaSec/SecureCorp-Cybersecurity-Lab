
# Architecture

This folder describes the network design of the SecureCorp lab. The whole environment runs on VirtualBox and is isolated from any real infrastructure.

## Logical Architecture

```
            INTERNET / NAT
                  │
                  ▼
          ┌───────────────┐
          │ OPNsense      │
          │ Firewall      │
          └───────┬───────┘
      ┌───────────┼────────────┐
      ▼           ▼            ▼
 Corporate Net  Attack Net  Target Net
192.168.20.0/24 192.168.10.0/24 192.168.50.0/24
      │           │
 SERVER01        Kali
 WCLIENT
 WAZUH
```

## OPNsense Interfaces

| Interface | Device | Address | Role |
|---|---|---|---|
| LAN | em1 | 192.168.20.1/24 | Corporate network |
| OPT1 | em2 | 192.168.10.1/24 | Attack network |
| OPT2 | em3 | 192.168.50.1/24 | Target network |
| WAN | em0 | 10.0.2.15/24 (DHCP) | Internet / NAT |

## Virtual Machines

| Machine | System | IP Address | Function |
|---|---|---|---|
| Kali | Kali Linux | 192.168.10.100 | Reconnaissance |
| WCLIENT | Windows 11 | 192.168.20.20 | Endpoint |
| WAZUH | Ubuntu Server | 192.168.20.116 | SIEM / Monitoring |
| SERVER01 | Windows Server | 192.168.20.10 | Active Directory domain controller |

## Segmentation Principle

The analysis machine (Kali) sits on a different network from the target (WCLIENT). All traffic between them is routed and filtered by OPNsense.

```
Kali (192.168.10.0/24) ──▶ OPNsense ──▶ Corporate Network (192.168.20.0/24)
```

## Screenshots

- `evidence/screenshots/fig01-virtualbox-vms.png`
- `evidence/screenshots/fig02-logical-architecture.png`
- `evidence/screenshots/fig03-opnsense-interfaces.png`
