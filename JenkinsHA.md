![image](https://github.com/user-attachments/assets/644c45ce-9f7a-440d-b92c-ead18d01f4a9)


# **Documentation of Jenkins High Availability**

---

| **Author** | **Created on** | **Version** | **Last updated by** | **Last Edited On** | **Level**          | **Reviewer**    |
|------------|----------------|-------------|----------------------|---------------------|---------------------|------------------|
| Himanshu   | 2025-05-14     | 1.0         | Himanshu             | 2025-05-14        | Internal Reviewer   | Komal Jaiswal    |
| Himanshu   | 2025-05-14     | 1.0         | Himanshu             | 2025-05-14        | L0                  | Imran            |
| Himanshu   | 2025-05-14     | 1.0         | Himanshu             | 2025-05-14        | L1                  | Shashi           |
| Himanshu   | 2025-05-14     | 1.0         | Himanshu             | 2025-05-14        | L2                  | Mahesh Kumar     |


---

## **Table of Contents**  
1. [Introduction](#introduction)  
2. [Why Jenkins HA?](#why-jenkins-ha)  
3. [Architecture of Master-Slave](#architecture-of-master-slave)  
4. [Setup Steps](#setup-steps)  
5. [Active/Passive Nodes](#activepassive-nodes)
6. [Benefits](#benefits)  
7. [Conclusion](#conclusion)  
8. [Contact](#contact)  
9. [References](#references)  

---

## **Introduction**  
Jenkins High Availability (HA) ensures that CI/CD pipelines keep running even if a failure occurs. It prevents downtime and ensures continuous software delivery by utilizing redundancy, load balancing, and failover mechanisms.

### **HA setup using two methods:**  
- **Active/Passive Setup:** A failover approach where a standby Jenkins instance takes over in case of failure.
- **Autoscaling Group Setup:** Uses cloud-based auto-scaling to manage Jenkins instances dynamically based on demand.

---

## **Why Jenkins HA?**  
Jenkins HA is essential for organizations that rely on continuous integration and deployment. Below are the primary benefits:

| **Benefit**            | **Description**  |  
|----------------------|----------------|  
| **No Downtime**     | Ensures Jenkins remains operational even if a failure occurs. |  
| **Scalability**     | Expands Jenkins capacity based on workload requirements. |  
| **Load Balancing**  | Distributes workload across multiple nodes for optimized performance. |  
| **Business Continuity** | Ensures uninterrupted CI/CD pipelines and productivity. |  

---

## **Architecture of Master-Slave**  
Jenkins HA operates using a **Master-Slave** or **Multi-Master** architecture to distribute workload and increase resilience.

| **Component**      | **Purpose**  |  
|-------------------|-------------|  
| **Jenkins Master**  | Manages jobs, schedules builds, and distributes workloads. |  
| **Jenkins Agents**  | Execute builds, reducing the load on the master. |  
| **Shared Storage**  | Stores configurations, logs, plugins, and build artifacts. |  
| **Database Replication** | Synchronizes job configurations and prevents data loss. |  
| **Load Balancer**  | Distributes traffic between Jenkins instances to ensure availability. |  

### **Architecture Diagram**
![Screenshot from 2025-05-13 23-54-38](https://github.com/user-attachments/assets/35e42814-7367-46dc-8b67-4e50948dfb3f)


---

## **Setup Steps**  
Below are the steps to configure a Jenkins HA setup:

| **Step**            | **Action**  |  
|--------------------|------------|  
| **1. Install Jenkins Master** | Deploy Jenkins on multiple machines to create redundancy. |  
| **2. Configure Master** | Synchronize configurations across all master nodes and set up database replication. |  
| **3. Setup Load Balancer** | Use HAProxy, Nginx, or AWS ALB to distribute incoming traffic. |  
| **4. Connect Agents** | Install and configure Jenkins agents to execute builds. |  
| **5. Use Shared Storage** | Set up an NFS, AWS EFS, or GCS bucket for consistent data storage. |  
| **6. Implement Backup & Recovery** | Use ThinBackup or similar plugins to automate periodic backups. |  
| **7. Test Failover Mechanism** | Simulate failures and ensure automatic failover works correctly. |  

---

## **Active/Passive Nodes**

Jenkins HA can use an **Active/Passive** setup where only one master node is active at a time. 

| **Node Type**   | **Description**                                                                                                                                           |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Active Node** | The primary Jenkins instance that handles all job executions and user requests.    |
| **Passive Node**| A standby Jenkins instance that remains in sync with the active node but takes over only when the active node fails. |

### **Active-Passive Architecture Diagram**
![Screenshot from 2025-05-14 00-19-41](https://github.com/user-attachments/assets/c5430987-ff8b-44e5-b73b-113eb1fb0d9f)


---

## **Benefits**  
The HA setup provides several advantages:

| **Benefit**        | **Description**  |  
|-------------------|----------------|  
| **Less Downtime** | Ensures Jenkins stays operational during failures by switching to a backup instance. |  
| **Better Performance** | Reduces processing load on a single machine by distributing builds across multiple agents. |  
| **Scalability** | Supports dynamic expansion by adding additional agents or masters when needed. |  
| **Continuous CI/CD** | Guarantees job execution continuity, avoiding disruptions in development pipelines. |  

---

## **Conclusion**  
Setting up Jenkins in HA mode ensures smooth CI/CD operations, even if failures happen. Using multiple Jenkins masters, distributed agents, shared storage, and load balancing creates a reliable and scalable environment. Regular backups and failover testing enhance stability and provide business continuity. Organizations can leverage either an Active-Passive or Auto-Scaling Group setup depending on their infrastructure needs.

---

## **Contact**  
| Name              | Email Address                                   |
|-------------------|--------------------------------------------------|
| Himanshu Parashar | himanshu.parashar.snaatak@mygurukulam.co         |


---

## **References**  

| **Link** | **Description**  |  
|---------|---------------|  
| [Jenkins HA Guide](https://medium.com/@priyanshigola8/setup-jenkins-ha-high-availability-with-master-slave-architecture-9b95f8b341e4) | Step-by-step Jenkins HA setup. |  
| [ThinBackup Plugin](https://medium.com/devops-technical-notes-and-manuals/jenkins-backup-and-restore-using-plugins-guide-for-junior-devops-engineers-ffd0fd41fb8e) | How to back up and restore Jenkins configurations. |  

