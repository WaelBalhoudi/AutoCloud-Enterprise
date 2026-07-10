# AutoCloud Enterprise Architecture

## Overview

AutoCloud Enterprise simulates the infrastructure of a medium-sized organization using enterprise Linux technologies and Infrastructure as Code principles.

The environment is designed to demonstrate how servers are provisioned, configured, secured, monitored, and maintained in a production-like environment.

---

# Design Principles

The project follows these principles:

- Infrastructure as Code
- Automation First
- Security by Default
- Separation of Responsibilities
- Reproducibility
- Documentation-Driven Development

---

# Infrastructure Components

## Automation Workstation

Responsibilities:

- Runs Vagrant
- Runs Ansible
- Creates virtual machines
- Deploys infrastructure

Installed Software

- Git
- VirtualBox
- Vagrant
- Ansible

---

## cloud01

Role

Private Cloud Server

Responsibilities

- Reverse Proxy
- Nextcloud
- MariaDB
- Redis

Deployment

Docker Compose managed by Ansible.

---

## idm01

Role

Identity & Storage Server

Responsibilities

- FreeIPA
- LDAP Authentication
- User Management
- Group Management
- NFS Server
- LVM Storage

---

## monitor01

Role

Monitoring & Security Server

Responsibilities

- Prometheus
- Grafana
- Alertmanager
- Wazuh
- Fail2Ban
- Auditd

---

## client01

Windows workstation used to simulate an enterprise employee.

Used for:

- Authentication testing
- Nextcloud access
- File sharing
- Permission validation

---

# Deployment Workflow

1. Clone repository
2. Create virtual machines with Vagrant
3. Configure servers with Ansible
4. Deploy Docker services
5. Configure monitoring
6. Apply security hardening
7. Execute validation tests

---

# Project Goals

This project demonstrates practical skills in:

- Linux Administration
- Infrastructure Automation
- DevOps
- Cloud Infrastructure
- Identity Management
- Enterprise Storage
- Monitoring
- Cybersecurity
