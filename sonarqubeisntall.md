<p align="center">
  <img src="https://github.com/user-attachments/assets/2e0f55d0-3034-47da-a844-5c0a7d377207" alt="Screenshot from 2025-05-16 00-20-46" width="450">
</p>

| Author   | Created on | Version | Last updated by | Last Edited On | Level             | Reviewer        |
|----------|------------|---------|-----------------|----------------|-------------------|-----------------|
| Himanshu | 2025-05-16 | 1.0     | Himanshu        | 2025-05-16     | Internal Reviewer | Komal Jaiswal   |
| Himanshu | 2025-05-16 | 1.0     | Himanshu        | 2025-05-16     | L0                | Imran           |
| Himanshu | 2025-05-16 | 1.0     | Himanshu        | 2025-05-16     | L1                | Shashi          |
| Himanshu | 2025-05-16 | 1.0     | Himanshu        | 2025-05-16     | L2                | Mahesh Kumar    |

---

## Table of Contents

- [Introduction](#introduction)  
- [Prerequisites](#prerequisites)  
- [Steps to Install SonarQube on Ubuntu](#steps-to-install-sonarqube-on-ubuntu)  
- [Best Practices](#best-practices)  
- [Conclusion](#conclusion)  
- [Contact](#contact)  
- [References](#references)  

---

## Introduction

SonarQube is an open-source platform used for continuous inspection of code quality to perform automatic reviews with static analysis of code to detect bugs, code smells, and security vulnerabilities. This document provides a step-by-step guide to install and configure SonarQube on an Ubuntu server using PostgreSQL as the backend database.

---

## Prerequisites

Before starting the installation process, ensure you have the following:

| Requirement           | Details                                |
|-----------------------|--------------------------------------|
| Operating System      | Ubuntu 22.04 or 20.04                 |
| User Privileges       | Root or sudo privileges               |
| RAM                   | Minimum 2 GB (4 GB recommended)      |
| Database              | PostgreSQL installed or ready to be installed |


---

## Steps to Install SonarQube on Ubuntu

### 1. Install Java and Required Tools

```bash
sudo apt update
sudo apt install openjdk-17-jdk unzip wget -y
```

### 2. Create SonarQube User

```bash
sudo adduser --system --no-create-home --group --disabled-login sonar
```

### 3. Install PostgreSQL and Configure Database

```bash
sudo apt install postgresql postgresql-contrib -y
sudo -u postgres psql -c "CREATE USER sonar WITH ENCRYPTED PASSWORD 'sonar';"
sudo -u postgres psql -c "CREATE DATABASE sonarqube OWNER sonar;"
```

### 4. Download and Extract SonarQube

```bash
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.3.0.82913.zip
unzip sonarqube-10.3.0.82913.zip
sudo mv sonarqube-10.3.0.82913 /opt/sonarqube
sudo chown -R sonar:sonar /opt/sonarqube
```

### 5. Configure SonarQube Database Settings

Edit the \`sonar.properties\` file:

```bash
sudo nano /opt/sonarqube/conf/sonar.properties
```

Uncomment and set the following lines:
```bash
# PostgreSQL DB Configuration
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar
sonar.jdbc.url=jdbc:postgresql://localhost:5432/sonarqube

# Bind SonarQube to all network interfaces
sonar.web.host=0.0.0.0
```

Save and exit the editor.

### 6. Configure System Kernel Parameter

Set the virtual memory map count for Elasticsearch (SonarQube dependency):

```bash
echo "vm.max_map_count=262144" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

### 7. Start SonarQube Server

```bash
sudo -u sonar /opt/sonarqube/bin/linux-x86-64/sonar.sh start
```

### 8. Access SonarQube

Open a browser and navigate to:

```bash
http://<your-server-public-ip>:9000
```

The default login is usually:

- Username: admin  
- Password: admin

---

## Best Practices

- Run SonarQube behind a reverse proxy (like Nginx) for SSL termination and better security.
- Regularly update SonarQube to the latest stable version.
- Backup your PostgreSQL SonarQube database regularly.
- Monitor SonarQube logs for errors located at \`/opt/sonarqube/logs\`.
- Allocate sufficient system resources to handle code analysis workloads.

---

## Conclusion

Following this guide, you should now have a fully functional SonarQube server running on Ubuntu, connected to a PostgreSQL backend. This setup allows you to continuously monitor and improve code quality in your projects.

---

## Contact

| Name             | Email                                    |
|------------------|------------------------------------------|
| Himanshu Parashar| himanshu.parashar.snaatak@mygurukulam.co |

---

## References

| Resource                                  | Description                                         |
|-------------------------------------------|-----------------------------------------------------|
| [SonarQube Official Documentation](https://docs.sonarqube.org/latest/) | Official guide and documentation for SonarQube      |
| [PostgreSQL Documentation](https://www.postgresql.org/docs/) | PostgreSQL database user guide                       |
| [OpenJDK 17](https://openjdk.org/projects/jdk/17/)           | Java Development Kit required for SonarQube          |
