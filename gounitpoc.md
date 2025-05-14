<p align="center">
  <img src="https://github.com/user-attachments/assets/4f2d68d7-3e53-40f2-bd5b-164f02f0d0fa" alt="Screenshot from 2025-05-14 22-35-08" width="450">
</p>

# Golang CI Check | Unit Testing | POC

| **Author** | **Created on** | **Version** | **Last updated by** | **Last Edited On** | **Level**          | **Reviewer**    |
|------------|----------------|-------------|----------------------|---------------------|---------------------|------------------|
| Himanshu   | 2025-05-15     | 1.0         | Himanshu             | 2025-05-15        | Internal Reviewer   | Komal Jaiswal    |
| Himanshu   | 2025-05-15     | 1.0         | Himanshu             | 2025-05-15        | L0                  | Imran            |
| Himanshu   | 2025-05-15     | 1.0         | Himanshu             | 2025-05-15        | L1                  | Shashi           |
| Himanshu   | 2025-05-15     | 1.0         | Himanshu             | 2025-05-15        | L2                  | Mahesh Kumar     |


---
 ## Table of Contents
 
- [Introduction](#Introduction)
- [Steps of unit testing](#Steps-of-unit-testing)
  - [Cloning the Go Application](#1-cloning-the-go-application)
  - [Install Prerequisites](#2-install-prerequisites)
  - [Run the Tests](#3-run-the-test)
  - [Generating the report](#4-generating-the-report)
- [Conclusion](#Conclusion)
- [Contact](#Contact)
- [Refrence](#Refrence)

---

## Introduction

In this document, we are creating a proof of concept (POC) for unit testing a GoLang-based API to identify errors through the testing process.



## Steps of unit testing  

####  1. Cloning the Go Application

First make a directory, then Within that directory clone the repository. 
  
  ```
  mkdir Go-testing
  cd Go-testing
  git clone https://github.com/OT-MICROSERVICES/employee-api.git  
  cd employee-api/routes/
  ```

 ![Screenshot from 2025-05-15 00-21-42](https://github.com/user-attachments/assets/a3a8a85b-c469-4cd5-9a8f-715e286cd769)


#### 2. Install Prerequisites

To install Golang on your system, please follow the link below for the Golang Installation Guide. :- [Golang Installation Guide](https://github.com/Cloud-NInja-snaatak/Documentation/blob/aditya_scrum31/commonstack/applications/golang/installation/installation_guide.md)


#### 3. Run the test
  
* Open a terminal or command prompt, navigate to the directory containing your Go files, and run the tests using the go test command:

```
go test
```
![Screenshot from 2025-05-15 00-26-08](https://github.com/user-attachments/assets/c21c1c1b-e43d-43b9-875a-d3218e974ef3)


---

* Run tests for the entire project, including all packages, you can run  

```
 go test ./...
```

![Screenshot from 2025-05-15 00-30-55](https://github.com/user-attachments/assets/90261f71-e7cb-4938-985e-d65f0a62cc81)


---

#### 4. Generating the report    

* 4.1   Generating a Test Coverage Profile
    
  * To generate a test coverage report in Go, you can use the built-in go test tool with the -coverprofile flag to generate a coverage profile

```
go test -coverprofile=coverage.out
```

![Screenshot from 2025-05-15 00-34-55](https://github.com/user-attachments/assets/414c21eb-8ef5-46a0-857d-2fa2b7bb0a20)

---

* 4.2 Generating an HTML Coverage Report
  
```
go tool cover -html=coverage.out -o coverage.html
```
![Screenshot from 2025-05-15 00-35-46](https://github.com/user-attachments/assets/0369e011-7648-4ce3-9aaa-e557033ea6f7)


When unit tests are executed in Go using the standard testing package, a detailed report is generated that verifies whether each function or method operates correctly and produces the expected outcomes. 

![Screenshot from 2025-05-15 00-38-07](https://github.com/user-attachments/assets/458f50be-c7f1-4726-a7bc-737e5ffbc6b1)




## Conclusion

Unit testing in Go helps ensure code correctness, catch bugs early, enhance reliability, and support efficient debugging and maintenance. In our project, we use the Gotest tool to perform unit testing.

---

 ## Contact

| **Name**              | **Email**                                     |
|------------------------|-----------------------------------------------|
| Himanshu Parashar      | himanshu.parashar.snaatak@mygurukulam.co     |
 
 ---

 ## Refrence

 | Link|Description|
 |:---:|:---:|
| [Test Guide](https://medium.com/@andrewdavisescalona/testing-in-go-some-tools-you-can-use-f3e79b398d8d)  |  Golang testing | 
 
