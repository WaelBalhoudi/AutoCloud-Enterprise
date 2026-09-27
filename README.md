# AutoCloud Enterprise

## Automated Private Cloud Infrastructure

![Ubuntu Server](https://img.shields.io/badge/Ubuntu_Server-24.04-E95420?logo=ubuntu&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-System_Administration-FCC624?logo=linux&logoColor=black)
![Ansible](https://img.shields.io/badge/Ansible-Infrastructure_as_Code-EE0000?logo=ansible&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Containerization-2496ED?logo=docker&logoColor=white)
![Docker Compose](https://img.shields.io/badge/Docker_Compose-Orchestration-2496ED?logo=docker&logoColor=white)
![Vagrant](https://img.shields.io/badge/Vagrant-Virtualization-1868F2?logo=vagrant&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-Monitoring-E6522C?logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-Observability-F46800?logo=grafana&logoColor=white)

<p align="center">
  <img src="assets/images/banner.png" alt="AutoCloud Enterprise Banner" width="100%">
</p>

---

## 📖 Project Overview

AutoCloud Enterprise is a **production-inspired Linux infrastructure project** designed to demonstrate practical skills in:

- Linux System Administration
- Infrastructure as Code (IaC)
- DevOps automation
- Private cloud deployment
- Identity management
- Enterprise storage
- Infrastructure monitoring
- Security hardening
- Backup and disaster recovery

The infrastructure is provisioned using **Vagrant and VirtualBox**, while server configuration is automated using **Ansible**.

Future application and infrastructure services will be deployed using **Docker and Docker Compose**.

The project is developed incrementally through clearly defined implementation phases.

---

## 📚 Table of Contents

- [Project Overview](#-project-overview)
- [Objectives](#-objectives)
- [Key Features](#-key-features)
- [Architecture Overview](#-architecture-overview)
- [Technology Stack](#-technology-stack)
- [Repository Structure](#-repository-structure)
- [Documentation](#-documentation)
- [Deployment Workflow](#-deployment-workflow)
- [Project Roadmap](#-project-roadmap)
- [Current Project Status](#-current-project-status)
- [Skills Demonstrated](#-skills-demonstrated)
- [Screenshots](#-screenshots)
- [License](#-license)

---

## 🎯 Objectives

The goal of this project is to design, automate, deploy, secure, monitor, and maintain a realistic enterprise infrastructure using Infrastructure as Code principles.

The project demonstrates how to:

- Provision infrastructure automatically
- Configure Linux servers with Ansible
- Deploy containerized services
- Manage enterprise identity
- Configure centralized storage
- Monitor infrastructure health
- Apply security hardening
- Automate backups
- Validate infrastructure using automated tests
- Document infrastructure and operational procedures

---

## 🚀 Key Features

- Infrastructure as Code (IaC)
- Automated Virtual Machine Provisioning
- Enterprise Linux Administration
- Configuration Management with Ansible
- Private Cloud Platform
- Docker & Docker Compose
- Centralized Identity Management
- Enterprise Storage using LVM and NFS
- Infrastructure Monitoring
- Security Hardening
- Backup & Disaster Recovery
- Automated Infrastructure Validation

---

## 🏗️ Architecture Overview

The project uses an automation workstation to provision and manage multiple Linux servers.

| Machine | Operating System | IP Address | Purpose |
|----------|------------------|------------|---------|
| Automation Workstation | Windows 11 + WSL | — | Vagrant & Ansible Control Node |
| cloud01 | Ubuntu Server 24.04 | 10.10.10.10 | Private Cloud Platform |
| idm01 | Ubuntu Server 24.04 | 10.10.10.20 | Identity Management & Storage |
| monitor01 | Ubuntu Server 24.04 | 10.10.10.30 | Monitoring & Security |
| client01 | Windows | Planned | Employee Workstation |

> `cloud01`, `idm01`, and `monitor01` are currently provisioned. `client01` is planned for a later phase.

### Architecture Diagram

<p align="center">
  <img src="assets/images/architecture.png" alt="AutoCloud Enterprise Architecture" width="100%">
</p>

### Network Topology

<p align="center">
  <img src="assets/images/network-topology.png" alt="AutoCloud Enterprise Network Topology" width="100%">
</p>

For more information, see the [Network Design](documentation/network.md) documentation.

---

## 🛠 Technology Stack

| Category | Technologies |
|----------|--------------|
| Operating System | Ubuntu Server 24.04 |
| Virtualization | VirtualBox, Vagrant |
| Automation | Ansible |
| Containers | Docker, Docker Compose |
| Cloud Platform | Nextcloud |
| Reverse Proxy | Nginx |
| Database | MariaDB |
| Cache | Redis |
| Identity Management | FreeIPA |
| Storage | NFS, LVM |
| Monitoring | Prometheus, Grafana |
| Security | Wazuh, Fail2Ban, Auditd |
| Version Control | Git & GitHub |

> The project is implemented incrementally. Some technologies listed above belong to future phases and are not yet deployed.

---

## 📂 Repository Structure

```text
AutoCloud-Enterprise/
│
├── assets/
│   └── images/
│       ├── banner.png
│       ├── architecture.png
│       ├── network-topology.png
│       └── dashboards/
│
├── ansible/
│   ├── ansible.cfg
│   ├── group_vars/
│   │   └── all.yml
│   ├── host_vars/
│   ├── inventory/
│   │   └── hosts.yml
│   ├── roles/
│   │   ├── common/
│   │   └── linux_admin/
│   ├── requirements.yml
│   └── site.yml
│
├── docker/
│
├── documentation/
│   ├── architecture.md
│   ├── network.md
│   ├── installation.md
│   ├── security.md
│   ├── backup.md
│   ├── phase-5-linux-administration.md
│   └── troubleshooting.md
│
├── diagrams/
│
├── scripts/
│
├── tests/
│
├── screenshots/
│
├── Vagrantfile
│
└── README.md
```

> Per-server IP and role information lives in the `servers` variable inside `ansible/group_vars/all.yml`. `host_vars/` is currently empty and reserved for future host-specific overrides.

---

## 📖 Documentation

| Document                                                     | Description                                                                               |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------------------- |
| 📐 [Architecture](documentation/architecture.md)             | Infrastructure architecture and server roles                                              |
| 🌐 [Network Design](documentation/network.md)                | Network topology, IP addressing and communication                                         |
| ⚙️ Phase 4 — Ansible Base Configuration                      | Ansible inventory, common role and base configuration                                     |
| 🐧 Phase 5 — Linux Administration                            | Linux baseline, users, SSH, firewall, permissions, storage, services, logs and monitoring |
| 🚀 [Installation Guide](documentation/installation.md)       | Project installation and deployment *(In Progress)*                                       |
| 🔒 [Security Guide](documentation/security.md)               | Security hardening and best practices *(Coming Soon)*                                     |
| 💾 [Backup & Recovery](documentation/backup.md)              | Backup strategy and disaster recovery *(Coming Soon)*                                     |
| 🛠 [Troubleshooting Guide](documentation/troubleshooting.md) | Common issues and solutions                                                               |

---

## 🚀 Deployment Workflow

### 1. Clone the repository

```bash
git clone https://github.com/WaelBalhoudi/AutoCloud-Enterprise.git
```

### 2. Enter the project directory

```bash
cd AutoCloud-Enterprise
```

### 3. Provision the virtual machines

```bash
vagrant up
```

This currently provisions:

```text
cloud01    → 10.10.10.10
idm01      → 10.10.10.20
monitor01  → 10.10.10.30
```

### 4. Configure the Ansible environment

Because the project is currently located on a Windows-mounted WSL filesystem, Ansible may not automatically load the repository `ansible.cfg`.

From the project root, set:

```bash
export ANSIBLE_CONFIG="$PWD/ansible/ansible.cfg"
```

Verify:

```bash
echo "$ANSIBLE_CONFIG"
```

Expected:

```text
/mnt/c/Users/<username>/.../AutoCloud-Enterprise/ansible/ansible.cfg
```

### 5. Test Ansible connectivity

```bash
ansible all -i ansible/inventory/hosts.yml -m ping
```

Expected result:

```text
cloud01    → SUCCESS
idm01      → SUCCESS
monitor01  → SUCCESS
```

### 6. Install required Ansible collections

```bash
ansible-galaxy collection install -r ansible/requirements.yml
```

### 7. Deploy the infrastructure configuration

```bash
ansible-playbook ansible/site.yml
```

The playbook currently applies:

* Common Linux configuration
* Hostname configuration
* Package management
* Timezone and time synchronization
* User and group management
* Enterprise directory structure
* `/etc/hosts` configuration
* MOTD configuration
* SSH administration
* UFW firewall
* File permissions and ownership
* Storage and disk information
* System service validation
* Log management
* System resource monitoring

### 8. Validate connectivity

```bash
ansible all -i ansible/inventory/hosts.yml -m ping
```

### 9. Validate the deployment

```bash
ansible-playbook ansible/site.yml --check
```

---

## 🗺️ Project Roadmap

* [x] Phase 1 — Project Planning & Architecture
* [x] Phase 2 — Enterprise Network Design
* [x] Phase 3 — Infrastructure Provisioning & Networking
* [x] Phase 4 — Ansible Base Configuration
* [x] Phase 5 — Linux Administration
* [ ] Phase 6 — Docker Engine Installation
* [ ] Phase 7 — Private Cloud Deployment (Nextcloud)
* [ ] Phase 8 — Identity Management
* [ ] Phase 9 — Enterprise Storage
* [ ] Phase 10 — Monitoring & Observability
* [ ] Phase 11 — Security Hardening
* [ ] Phase 12 — Backup & Disaster Recovery
* [ ] Phase 13 — Infrastructure Testing
* [ ] Phase 14 — Documentation Finalization
* [ ] Phase 15 — GitHub Actions CI/CD
* [ ] Phase 16 — Project Release

---

## 📈 Current Project Status

### Current Phase

**Phase 5 — Linux Administration ✅**

### Completed

#### Phase 1 — Project Planning & Architecture

* ✅ Enterprise architecture design
* ✅ Server role definition
* ✅ Infrastructure planning

#### Phase 2 — Enterprise Network Design

* ✅ Network topology
* ✅ IP addressing
* ✅ Server communication design
* ✅ Private network design

#### Phase 3 — Infrastructure Provisioning & Networking

* ✅ Vagrant configuration
* ✅ VirtualBox infrastructure
* ✅ Ubuntu Server 24.04 virtual machines
* ✅ Static IP addressing
* ✅ SSH connectivity

#### Phase 4 — Ansible Base Configuration

* ✅ Ansible inventory
* ✅ Ansible common role
* ✅ Hostname configuration
* ✅ Common package installation
* ✅ Timezone configuration
* ✅ Time synchronization
* ✅ `sysadmins` group
* ✅ `automation` user
* ✅ Enterprise directory structure
* ✅ `/etc/hosts` configuration
* ✅ Custom MOTD
* ✅ SSH service configuration
* ✅ Infrastructure validation

#### Phase 5 — Linux Administration

* ✅ Linux baseline and system information
* ✅ User and privilege management
* ✅ SSH administration and configuration audit
* ✅ UFW firewall
* ✅ File permissions and ownership
* ✅ Storage and disk inventory
* ✅ System service management
* ✅ System log management
* ✅ System resource monitoring
* ✅ Ansible-based validation

### Current Infrastructure

| Server    | IP Address  | Role                  | Status  |
| --------- | ----------- | ---------------------- | ------- |
| cloud01   | 10.10.10.10 | Private Cloud         | ✅ Ready |
| idm01     | 10.10.10.20 | Identity & Storage    | ✅ Ready |
| monitor01 | 10.10.10.30 | Monitoring & Security | ✅ Ready |

### Validation

```text
Servers managed:     3
Servers reachable:  3/3
Servers configured: 3/3
Failed hosts:       0
Unreachable hosts:  0
Firewall:            Active
SSH:                 Active
```

### Next Phase

**Phase 6 — Docker Engine Installation**

---

## 💼 Skills Demonstrated

This project demonstrates practical experience in:

* Linux System Administration
* Infrastructure as Code
* Ansible Configuration Management
* Virtualization
* Vagrant
* Enterprise Networking
* SSH Administration
* Linux Package Management
* User and Group Management
* Time Synchronization
* File Permissions and Ownership
* Filesystem and Storage Administration
* Firewall Configuration
* System Service Management
* Log Management
* System Resource Monitoring
* Infrastructure Automation
* Docker & Containerization
* Identity & Access Management
* Monitoring & Observability
* Security Hardening
* Backup & Recovery
* DevOps Practices
* Technical Documentation

---

## 📸 Screenshots

Screenshots are captured throughout the project to document infrastructure deployment and configuration.

### Phase 4 — Ansible Base Configuration

Recommended evidence:

* Ansible project structure
* Ansible inventory
* Ansible connectivity test
* Successful Ansible playbook execution
* Base configuration validation
* Server login and MOTD
* Enterprise directory structure

### Phase 5 — Linux Administration

Recommended evidence:

* Linux baseline information
* User and privilege validation
* SSH configuration audit
* UFW firewall status
* Enterprise directory permissions
* Storage and filesystem information
* System service validation
* Journal/log validation
* Resource monitoring
* Successful Phase 5 deployment

Additional screenshots will be added as future phases are completed.

---

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

If you discover a bug or have an idea for enhancement, feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the MIT License.
