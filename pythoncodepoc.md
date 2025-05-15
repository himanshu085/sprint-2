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
![Screenshot from 2025-05-15 14-47-43](https://github.com/user-attachments/assets/ef4757ff-feea-4185-9790-1f00d0c57456)


### Navigate to the directory and locate your main script  
Typically, this will be `main.py` or the entry-point script of the service.

![Screenshot from 2025-05-15 14-49-50](https://github.com/user-attachments/assets/56f2cf54-e68a-4bae-b547-7fb1de0c7e0e)


### Compile the main Python script using PyInstaller:

```bash
pyinstaller --onefile app.py
```
This command generates a standalone binary in the `dist/` directory.

![Screenshot from 2025-05-15 14-54-22](https://github.com/user-attachments/assets/6926b1c7-5156-4021-a6f9-46e2987886bb)
![Screenshot from 2025-05-15 14-54-48](https://github.com/user-attachments/assets/83d61dfa-03b1-44f8-af8c-e37862aa893e)
![Screenshot from 2025-05-15 15-48-57](https://github.com/user-attachments/assets/1afe74ad-6ea3-4a08-9f5f-91bab276caf8)


### Run the compiled binary:

```bash
./dist/app
```
Make sure to give execution permission if required:

```bash
chmod +x ./dist/app
```
![Screenshot from 2025-05-15 15-34-45](https://github.com/user-attachments/assets/74131034-ab69-4d47-b2c6-44d5d9803803)
![Screenshot from 2025-05-15 15-49-26](https://github.com/user-attachments/assets/d162a277-dc97-4cb4-8f44-0a4c89ede908)


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
