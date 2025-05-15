<p align="center">
  <img src="https://github.com/user-attachments/assets/2e0f55d0-3034-47da-a844-5c0a7d377207" alt="Screenshot from 2025-05-16 00-20-46" width="450">
</p>

# Application CI Design | SonarQube | Software Configuration

| Author   | Created on | Version | Last updated by | Last Edited On | Level             | Reviewer        |
|----------|------------|---------|------------------|----------------|-------------------|-----------------|
| Himanshu | 2025-05-16 | 1.0     | Himanshu         | 2025-05-16     | Internal Reviewer | Komal Jaiswal   |
| Himanshu | 2025-05-16 | 1.0     | Himanshu         | 2025-05-16     | L0                | Imran           |
| Himanshu | 2025-05-16 | 1.0     | Himanshu         | 2025-05-16     | L1                | Shashi          |
| Himanshu | 2025-05-16 | 1.0     | Himanshu         | 2025-05-16     | L2                | Mahesh Kumar    |

## Table of Contents

- [Overview](#overview)  
- [Purpose](#purpose)  
- [Pre-requisites](#pre-requisites)  
- [System Requirements](#system-requirements)  
- [Dependencies](#dependencies)  
- [Runtime Dependencies](#runtime-dependencies)  
- [Important Ports](#important-ports)  
- [Workflow](#workflow)  
- [Ansible Role Design for SonarQube](#ansible-role-design-for-sonarqube)  
- [POC – Manual SonarQube Setup](#poc--manual-sonarqube-setup)  
- [Best Practices](#best-practices)  
- [Conclusion](#conclusion)  
- [Contact](#contact)  
- [References](#references)  

## Overview

This document outlines the design and planning of an Ansible role to automate the installation and configuration of **SonarQube** as part of a CI workflow. While actual Ansible role implementation is planned for the next sprint, a Proof of Concept (POC) is included to demonstrate manual setup.

## Purpose

- Define a reusable Ansible role for automating SonarQube setup  
- Validate the process through a manual installation POC  
- Prepare for future CI/CD pipeline integration  

## Pre-requisites

Before setting up SonarQube using Ansible, ensure you have the following:

- Ansible installed on your local machine  
- A target Ubuntu server (20.04 or later) with a non-root user having sudo privileges  

## System Requirements

The system requirements vary based on the size of the codebase being analyzed:

| **Component** | **Minimum Requirement** | **Recommended**     |
|---------------|--------------------------|----------------------|
| CPU           | 2 vCPUs                  | 4 vCPUs or more      |
| RAM           | 4 GB                     | 8 GB or more         |
| Storage       | 10 GB free disk space    | 50 GB or more        |
| OS            | Ubuntu 20.04             | Latest LTS version   |

## Dependencies

Ensure the following dependencies are installed on the Ansible control node and optionally on the target node:

- Python (v3.6+)  
- Ansible (v2.9+)  

## Runtime Dependencies

Once SonarQube is running, ensure the following services are available:

- SonarQube Server  
- OpenJDK (v11+)  
- PostgreSQL Database  
- Reverse Proxy (optional, e.g., Nginx or Apache)  

## Important Ports

Ensure the following ports are open and accessible for correct functionality:

| **Port** | **Service**    | **Description**                          |
|----------|----------------|------------------------------------------|
| 9000     | SonarQube      | Default web UI and API access            |
| 5432     | PostgreSQL     | Database communication                   |
| 80/443   | Nginx (optional) | Web access via reverse proxy (HTTP/HTTPS) |

## Workflow

The Ansible role execution will follow this lifecycle:

![Screenshot from 2025-05-16 00-05-09](https://github.com/user-attachments/assets/37f8ebea-bf53-4bb0-9177-bda62a477a76)


The playbook ensures idempotent execution and uses handlers to restart services only when needed.

## Ansible Role Design for SonarQube

### Role Name: `sonarqube`

**Directory Structure**
```
roles/
└── sonarqube/
    ├── defaults/
    │   └── main.yml
    ├── files/
    │   └── sonar.sh
    ├── handlers/
    │   └── main.yml
    ├── meta/
    │   └── main.yml
    ├── tasks/
    │   └── main.yml
    ├── templates/
    │   └── sonar.properties.j2
    └── vars/
        └── main.yml
```

### Key Responsibilities

- **defaults/main.yml**: Holds configurable variables (Java version, Sonar port, etc.)  
- **tasks/main.yml**: Automates Java installation, database setup, and SonarQube installation  
- **templates/sonar.properties.j2**: Jinja2 template for SonarQube configuration  
- **handlers/main.yml**: Defines triggers to restart services when configuration changes  
- **files/sonar.sh**: Optional custom startup script for SonarQube  
- **vars/main.yml**: Platform-specific settings and overrides  
- **meta/main.yml**: Metadata for defining role dependencies and version compatibility  

## POC – Manual SonarQube Setup

To validate setup steps, here’s a quick guide for manual SonarQube installation on Ubuntu:

```bash
# Install Java and required tools
sudo apt update
sudo apt install openjdk-11-jdk unzip wget -y

# Create sonar user
sudo adduser --system --no-create-home --group --disabled-login sonar

# Install PostgreSQL
sudo apt install postgresql postgresql-contrib -y
sudo -u postgres psql -c "CREATE USER sonar WITH ENCRYPTED PASSWORD 'sonar';"
sudo -u postgres psql -c "CREATE DATABASE sonarqube OWNER sonar;"

# Download and extract SonarQube
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.3.0.82913.zip
unzip sonarqube-10.3.0.82913.zip
sudo mv sonarqube-10.3.0.82913 /opt/sonarqube
sudo chown -R sonar:sonar /opt/sonarqube

# Edit sonar.properties for DB config
sudo nano /opt/sonarqube/conf/sonar.properties

# Start the server
sudo -u sonar /opt/sonarqube/bin/linux-x86-64/sonar.sh start

# Access SonarQube at:
# http://<your-server-ip>:9000
```

## Best Practices

- Use **Ansible Vault** to secure sensitive values like database passwords  
- Separate concerns with **modular roles** (e.g., Java, PostgreSQL, SonarQube)  
- Leverage **handlers** for smart restarts  
- Maintain **idempotency** in all tasks  
- Include **health checks** and `wait_for` module to validate service status  

## Conclusion

With a clear structure and modular design, this documentation sets the stage for implementing an Ansible role to provision SonarQube in a CI/CD environment. The manual POC confirms feasibility and supports a confident transition into automated setup next sprint.

## Contact

| Name              | Email                                         |
|-------------------|-----------------------------------------------|
| Himanshu Parashar | himanshu.parashar.snaatak@mygurukulam.co      |

## References

| Resource              | Link                                                                 |
|-----------------------|----------------------------------------------------------------------|
| SonarQube Downloads   | https://www.sonarsource.com/products/sonarqube/downloads/            |
| SonarQube Docs        | https://docs.sonarsource.com/sonarqube/latest/                       |
| Ansible Role Guide    | https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html |
| Ansible Installation  | https://docs.ansible.com/ansible/latest/installation_guide/index.html |
