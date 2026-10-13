# Active Directory

Active Directory provides centralized identity management for the lab.

- **Domain:** `securecorp.local`
- **Domain controller:** SERVER01 (192.168.20.10), with the AD DS and DHCP roles

## Domain Structure

```
securecorp.local
├── Admins
├── Builtin
├── Computers
├── Domain Controllers
├── ForeignSecurityPrincipals
├── Groups
├── Managed Service Accounts
├── SecureCorp_Users
├── Servers
├── service_Accounts
├── Users
└── Workstations
```

## Organizational Units

The `SecureCorp_Users` OU contains one sub-OU per department:

```
SecureCorp_Users
├── Finance
├── HR
├── Interns
├── IT
├── Management
└── Sales
```

## Security Groups

`Finance_Users`, `HR_Users`, `IT_Admins`, `IT_Users`, `Managers`, `Sales_Users`

## Group Policy

GPOs centralize the configuration of Windows workstations: password policies, security settings, logging, restrictions and general Windows configuration.

## BloodHound Analysis

Data was collected from Kali with `bloodhound-python` and analyzed in BloodHound.

| Object type | Objects collected |
|---|---|
| Domains | 1 |
| Computers | 2 |
| Users | 15 |
| Groups | 58 |
| GPOs | 2 |
| OUs | 13 |
| Containers | 19 |
| Trusts | 0 |

BloodHound shows the relationships between users, groups, computers, OUs, GPOs and domains as a graph. For example, it displays the privileged groups with control over the WMIGPO container.

## Screenshots

- `evidence/screenshots/fig04-server-manager.png`
- `evidence/screenshots/fig05-domain-structure.png`
- `evidence/screenshots/fig06-organizational-units.png`
- `evidence/screenshots/fig07-security-groups.png`
- `evidence/screenshots/fig08-it-ou-users.png`
- `evidence/screenshots/fig09-bloodhound-collection.png`
- `evidence/screenshots/fig10-bloodhound-wmigpo.png`
- `evidence/screenshots/fig11-bloodhound-graph.png`
