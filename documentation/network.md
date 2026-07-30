# Network Design

## Overview

This document describes the logical network architecture of the AutoCloud Enterprise infrastructure.

The environment is deployed using a dedicated VirtualBox Host-Only network, allowing secure communication between virtual machines while isolating the infrastructure from the external network.

All servers use static IP addresses to ensure predictable communication and simplify infrastructure automation with Ansible.

---

# Network Topology

<p align="center">
    <img src="../assets/images/network-topology.png" alt="AutoCloud Enterprise Network Topology" width="100%">
</p>

---

# Network Architecture

The infrastructure consists of a dedicated private network connecting four virtual machines.

The physical host acts as the automation workstation and communicates with all servers using SSH through the private network.

The Windows client simulates an enterprise employee workstation and accesses infrastructure services exactly as a real user would.

---

# IP Addressing Plan

| Hostname | IP Address | Operating System | Role |
|-----------|------------|------------------|------|
| cloud01 | 10.10.10.10 | Ubuntu Server | Private Cloud |
| idm01 | 10.10.10.20 | Ubuntu Server | Identity & Storage |
| monitor01 | 10.10.10.30 | Ubuntu Server | Monitoring & Security |
| client01 | 10.10.10.40 | Windows | Employee Workstation |

Network

```
10.10.10.0/24
```

Subnet Mask

```
255.255.255.0
```

---

# Host Naming Convention

The infrastructure follows a simple and consistent hostname convention.

| Hostname | Description |
|-----------|-------------|
| cloud01 | Private Cloud Platform |
| idm01 | Identity & Storage |
| monitor01 | Monitoring & Security |
| client01 | Windows Employee Workstation |

---

# Domain & DNS

Internal Domain

```
technova.local
```

Fully Qualified Domain Names

| Service | FQDN |
|----------|------|
| Nextcloud | cloud.technova.local |
| Identity Server | idm.technova.local |
| Monitoring | monitor.technova.local |
| Client | client01.technova.local |

---

# Network Services

| Service | Protocol | Port | Server |
|----------|----------|------|--------|
| SSH | TCP | 22 | All Linux Servers |
| HTTP | TCP | 80 | cloud01 |
| HTTPS | TCP | 443 | cloud01 |
| LDAP | TCP | 389 | idm01 |
| LDAPS | TCP | 636 | idm01 |
| DNS | TCP/UDP | 53 | idm01 |
| NFS | TCP | 2049 | idm01 |
| Grafana | TCP | 3000 | monitor01 |
| Prometheus | TCP | 9090 | monitor01 |

---

# Communication Flow

The following diagram illustrates the normal service communication path.

```text
Employee
      │
      ▼
client01
      │
      ▼
cloud01 (Nextcloud)
      │
      ├────────► MariaDB
      ├────────► Redis
      │
      ▼
idm01 (FreeIPA)
      │
      ▼
NFS Storage
      │
      ▼
monitor01
(Prometheus • Grafana • Wazuh)
```

---

# Network Security

The infrastructure follows a least-privilege networking model.

Security measures include:

- Static IP addressing
- Private Host-Only network
- SSH key authentication
- UFW firewall
- Restricted service ports
- HTTPS for web services
- Centralized authentication with FreeIPA

Only required services are exposed between infrastructure components.

---

# Future Improvements

Future network enhancements include:

- VLAN segmentation
- Reverse Proxy DMZ
- VPN access (WireGuard)
- High Availability
- Load Balancer
- Internal Certificate Authority
- Dual Network Interfaces