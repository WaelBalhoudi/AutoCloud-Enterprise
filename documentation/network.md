# Network Design

## Network Overview

The infrastructure uses a dedicated VirtualBox private network.

Network Address:

10.10.10.0/24

---

## Server Addressing

| Hostname | IP Address | Purpose |
|-----------|------------|----------|
| cloud01 | 10.10.10.10 | Private Cloud |
| idm01 | 10.10.10.20 | Identity & Storage |
| monitor01 | 10.10.10.30 | Monitoring & Security |
| client01 | 10.10.10.40 | Windows Client |

---

## Domain

Internal Domain

technova.local

Fully Qualified Domain Names

cloud.technova.local

idm.technova.local

monitor.technova.local

client01.technova.local

---

## Network Services

| Service | Port |
|----------|------|
| SSH | 22 |
| HTTP | 80 |
| HTTPS | 443 |
| LDAP | 389 |
| LDAPS | 636 |
| NFS | 2049 |
| Grafana | 3000 |
| Prometheus | 9090 |

---

## Communication Flow

client01

↓

cloud01 (Nextcloud)

↓

idm01 (Authentication)

↓

NFS Storage

↓

monitor01 (Monitoring & Security)
