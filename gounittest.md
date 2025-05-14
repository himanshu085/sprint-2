<p align="center">
  <img src="https://github.com/user-attachments/assets/4f2d68d7-3e53-40f2-bd5b-164f02f0d0fa" alt="Screenshot from 2025-05-14 22-35-08" width="450">
</p>

# Golang Unit Testing

| **Author** | **Created on** | **Version** | **Last updated by** | **Last Edited On** | **Level**          | **Reviewer**    |
|------------|----------------|-------------|----------------------|---------------------|---------------------|------------------|
| Himanshu   | 2025-05-14     | 1.0         | Himanshu             | 2025-05-14        | Internal Reviewer   | Komal Jaiswal    |
| Himanshu   | 2025-05-14     | 1.0         | Himanshu             | 2025-05-14        | L0                  | Imran            |
| Himanshu   | 2025-05-14     | 1.0         | Himanshu             | 2025-05-14        | L1                  | Shashi           |
| Himanshu   | 2025-05-14     | 1.0         | Himanshu             | 2025-05-14        | L2                  | Mahesh Kumar     |


## Table of Contents

- [Introduction](#introduction)
- [Pre-requisite](#Pre-requisite)
- [Run Time Dependancy](#run-time-dependency)
- [What is Unit Testing?](#what-is-unit-testing)
- [Why Unit Testing?](#why-unit-testing)
- [General Workflow](#General-Workflow)
- [Different Tools for Unit Testing](#different-tools-for-unit-testing)
- [Comparison of Different Tools](#comparison-of-different-tools)
- [Advantages of Unit Testing](#advantages-of-unit-testing)
- [Proof of Concept](#proof-of-concept-poc)
- [Best Practices of Unit Testing](#best-practices-of-unit-testing)
- [Recommendations / Conclusion](#recommendation-and-conclusion)
- [Contact](#Contact)
- [References](#References)




## Introduction

This document offers a comprehensive guide to unit testing in Go, covering best practices, tools, workflows, and a proof of concept to illustrate its practical application.

## Pre-requisite

**[Go Installation](https://github.com/Cloud-NInja-snaatak/Documentation/blob/aditya_scrum31/commonstack/applications/golang/installation/installation_guide.md) :** Ensure Go (version greater than 1.21) is installed on your system.



## Run Time Dependency

| **Name** | **Version** | **Description** |
|------|---------|-------------|
| **go** | Greater then 1.21 | Application is built on this version only |



## What is Unit Testing?

Unit testing is a method of software testing that focuses on validating individual functions or components in isolation to ensure they work correctly. It helps identify bugs early, improves code quality, and supports better maintainability.

## Why Unit Testing?

- **Built-in Testing Package**: Golang provides a native `testing` package for writing and executing unit tests.
- **Performance and Simplicity**: Golang’s testing framework is lightweight and easy to use.
- **Automated Testing**: Supports automated test execution using `go test`.
- **Benchmarking and Example Tests**: Built-in support for performance testing and documentation through examples.


## General Workflow

![Screenshot from 2025-05-14 23-57-46](https://github.com/user-attachments/assets/8b910416-43b9-49d1-97a1-cded61cf9181)


### **Description of Flow Diagram**

| **Steps** | **Description** |
| ------------- | --------------- |
| **Directory** | Create a new directory named `Golang-testing` |
| **Clone Git Repository** | Clone the Git repository `employee-API.git` into the current directory |
| **Install Go** | Install Go programming language using the Snap package manager |
| **Run Unit Tests** | Execute unit tests for the current codebase |
| **Run All Tests** | Run tests recursively for all packages |
| **Run Tests with Verbose and Coverage** | Execute tests with verbose output and coverage information |
| **Generate Coverage Profile** | Create a coverage profile file `coverage.out` for further analysis |
| **Generate HTML Report** | Convert the coverage profile to an HTML report for detailed visualization |
| **Completion** | The flow is completed, and the necessary steps for testing and coverage analysis have been executed |



## Different Tools for Unit Testing

| **Tool**            | **Description** | **Key Features** | **Use Cases** |
|---------------------|-----------------------------------------------------|-----------------------------------------|----------------------------------------|
| **Testing**          | The default Go testing package, built into the standard library. | - Simple and lightweight<br>- Uses `Test*` functions<br>- Supports benchmarks and examples | Basic unit tests, benchmarking, and example-based documentation. |
| **Testify**        | A powerful testing framework that enhances Go’s standard `testing` package. | - Better assertions (e.g., `assert.Equal`, `require.NotNil`)<br>- Mocking support via `mock` package | Writing expressive unit tests with better readability and mocking capabilities. |
| **Ginkgo & Gomega** | A Behavior-Driven Development (BDD) testing framework for Go. | - Structured in a BDD format (`Describe`, `It`, `BeforeEach`)<br>- Uses Gomega matchers (`Expect`, `HaveOccurred`) | Writing tests in a more structured, BDD style, useful for complex applications. |
| **GoMock**         | A mocking framework for Go, used alongside `testing`. | - Generates mocks using `mockgen`<br>- Works well with interfaces | Mocking dependencies for testing services, repositories, etc. |
| **Goconvey**       | A testing framework with a web-based UI and live results. | - Auto-refresh UI for real-time feedback<br>- BDD-style syntax | Writing tests with real-time feedback and an interactive UI. |
| **httptest**       | A package in the standard library for testing HTTP servers and handlers. | - Provides `httptest.NewRecorder()` for response capture<br>- Simulates HTTP requests easily | Testing HTTP handlers, APIs, and server behavior. |



## Advantages of Unit Testing 


| **Benefit**                     | **Description** |
|----------------------------------|--------------------------------------------------|
| **Early Bug Detection**          | Identifies defects early in the development cycle, reducing costs and effort. |
| **Improved Code Quality**        | Enforces better coding practices and maintains high code standards. |
| **Facilitates Refactoring**      | Allows safe and reliable code changes without breaking functionality. |
| **Faster Debugging**             | Helps isolate and fix issues quickly, improving development efficiency. |
| **Continuous Integration Support** | Works seamlessly with CI/CD pipelines, ensuring automated testing and deployment. |



## Proof of Concept (POC)

- Please Refer Here for [POC](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Aayush-SCRUM-84/Application%20CI%20Design/GoLang%20CI%20Checks/Unit%20Testing/POC/README.md)

---

## Best Practices of Unit Testing

| **Best Practice**                     | **Description** |
|----------------------------------------|-------------------------------------------------------------|
| **Keep Tests Independent**             | Avoid dependencies between tests to ensure reliability. |
| **Use Table-Driven Tests**             | Improve maintainability by structuring tests with multiple cases. |
| **Mock External Dependencies**         | Use mocking frameworks like `GoMock` to isolate unit tests. |
| **Use Assertions for Readability**     | Utilize `Testify` for clearer and more readable assertions. |
| **Run Tests Automatically**            | Integrate tests into CI/CD pipelines for continuous validation. |
| **Measure Code Coverage**              | Use `go test -cover` to track how much code is tested. |
| **Use Benchmarks for Performance Testing** | Implement `Benchmark` functions to measure execution speed. |


## Recommendation and Conclusion

Go's built-in testing support makes unit testing both efficient and simple. The choice of framework depends on the project's complexity and specific needs—while the standard testing package works well for most cases, tools like Testify and Ginkgo provide additional functionality for more advanced scenarios.

## Contact

| **Name**              | **Email**                                     |
|------------------------|-----------------------------------------------|
| Himanshu Parashar      | himanshu.parashar.snaatak@mygurukulam.co     |


---

## References

| Tool              | Documentation Link                                                     |
|-------------------|------------------------------------------------------------------------|
| **Ginkgo**  | [GitLab CI/CD Documentation](https://docs.gitlab.com/ee/ci/)           |
| **Testify**     | [Testify GitHub Repository](https://github.com/stretchr/testify)      |
|  **Golang**    | [Golang Official Testing Documentation](https://golang.org/pkg/testing/)  |
