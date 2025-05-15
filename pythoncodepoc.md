<p align="center">
  <img src="https://github.com/user-attachments/assets/0b0eea18-d900-4abd-9e03-e866a426d4c8" alt="Screenshot from 2025-05-15 13-25-41" width="450">
</p>


# Proof of Concept (POC): Python Code Compilation Using PyInstaller

| Author   | Created on | Version | Last updated by | Last Edited On | Level             | Reviewer        |
|----------|------------|---------|------------------|----------------|-------------------|-----------------|
| Himanshu | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | Internal Reviewer | Komal Jaiswal   |
| Himanshu | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | L0                | Imran           |
| Himanshu | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | L1                | Shashi          |
| Himanshu | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | L2                | Mahesh Kumar    |

---

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Objective](#objective)
- [Steps](#steps)
- [Contact](#contact)
- [References](#references)

---

## Introduction

The objective of this POC is to demonstrate how to use PyInstaller to compile a simple Python application into a standalone executable that can run without requiring a Python interpreter on the target system.

---

## Prerequisites

- **Python Installed**: Ensure you have Python installed on your system (preferably Python 3.x).
- For Python Installation follow this [Guide](https://github.com/Cloud-NInja-snaatak/Documentation/blob/aditya_scrum13/commonstack/applications/python/installation/installation_guide.md)
- **PyInstaller Installed**: Install PyInstaller via pip if you haven’t done so yet.
```bash
pip install pyinstaller
```
- **Ensure Flask Installed**: Install Flask via pip if you haven't done so yet.
  ```bash
  pip install flask
  ```

- **Ensure Flask Installed**: Install Flasgger via pip if you haven't done so yet.

```bash
pip install flasgger
```

- **Ensure Prometheus Flask Exporter Installed**: Install Prometheus Flask Exporter via pip if you haven't done so yet.

```bash
pip install prometheus_flask_exporter
```

- **Ensure Email Installed**: Install Email via pip if you haven't done so yet.

  ```bash
  pip install emails
```

## Objective

Compile and test the Attendance and Notification Python services using PyInstaller in a CI-friendly setup.

---

## Steps

### Clone the repositories:

```bash
git clone https://github.com/OT-MICROSERVICES/attendance-api.git
git clone https://github.com/OT-MICROSERVICES/notification-worker.git
```
### Navigate to the directory and locate your main script  
Typically, this will be `main.py` or the entry-point script of the service.

### Compile the main Python script using PyInstaller:

```bash
pyinstaller --onefile app.py
```
This command generates a standalone binary in the `dist/` directory.

### Run the compiled binary:

```bash
./dist/app
```
Make sure to give execution permission if required:

```bash
chmod +x ./dist/app
```

## Contact

| Name              | Email                                         |
|-------------------|-----------------------------------------------|
| Himanshu Parashar | himanshu.parashar.snaatak@mygurukulam.co      |

---

## References

| Reference URL                                               | Description                 |
|-------------------------------------------------------------|-----------------------------|
| https://pyinstaller.org/en/stable/                          | Official PyInstaller Docs    |
| https://github.com/OT-MICROSERVICES/attendance-api.git      | Attendance API Repo          |
| https://github.com/OT-MICROSERVICES/notification-worker.git | Notification Worker Repo     |
