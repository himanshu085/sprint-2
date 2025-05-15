
# React Unit Testing & CI Integration

| Author   | Created on | Version | Last updated by | Last Edited On | Level             | Reviewer        |
|----------|------------|---------|------------------|----------------|-------------------|-----------------|
| Himanshu | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | Internal Reviewer | Komal Jaiswal   |
| Himanshu | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | L0                | Imran           |
| Himanshu | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | L1                | Shashi          |
| Himanshu | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | L2                | Mahesh Kumar    |

---

## Table of Contents

- [Introduction](#introduction)
- [Pre-requisite](#pre-requisite)
- [Run Time Dependency](#run-time-dependency)
- [What is Unit Testing?](#what-is-unit-testing)
- [Why Unit Testing?](#why-unit-testing)
- [General Workflow](#general-workflow)
- [Different Tools for Unit Testing](#different-tools-for-unit-testing)
- [Comparison of Different Tools](#comparison-of-different-tools)
- [Advantages of Unit Testing](#advantages-of-unit-testing)
- [Proof of Concept](#proof-of-concept-poc)
- [Best Practices of Unit Testing](#best-practices-of-unit-testing)
- [Recommendations / Conclusion](#recommendations--conclusion)
- [Contact](#contact)
- [References](#references)

---

## Introduction

This document provides a comprehensive guide to unit testing and CI integration for React applications, covering essential tools, practices, and a POC setup for implementing effective testing workflows.

---

## Pre-requisite

- Node.js (v18 or higher)
- React (v18+)
- Package Manager (npm or yarn)

---

## Run Time Dependency

| Name                  | Version | Description                                |
|-----------------------|---------|--------------------------------------------|
| Node.js               | ≥ 18    | JavaScript runtime for running React and test runners |
| React                 | ≥ 18    | Component-based UI library                 |
| Jest                  | Latest  | JavaScript testing framework               |
| React Testing Library | Latest  | Library for DOM testing in React           |
| CI/CD Tool            | Any supported | For automating test execution        |

---

## What is Unit Testing?

Unit testing in React focuses on testing individual components and functions in isolation to ensure they behave as expected under various scenarios.

---

## Why Unit Testing?

- **Component Reliability**: Validates UI components behave correctly.
- **Faster Debugging**: Pinpoints issues quickly during development.
- **Regression Prevention**: Avoids introducing bugs with new changes.
- **Confidence in Refactoring**: Enables safe updates and enhancements.
- **CI Compatibility**: Seamless automation with popular CI/CD tools.

---

## General Workflow

![Screenshot from 2025-05-15 11-35-32](https://github.com/user-attachments/assets/efb2fb5e-2440-4fc2-809c-897462b5b269)


| Step                | Description                                                  |
|---------------------|--------------------------------------------------------------|
| Setup Project       | Initialize React project and install testing dependencies    |
| Write Unit Tests    | Add test cases for components and utility functions          |
| Local Test Execution| Use npm test or yarn test for local verification             |
| Code Coverage       | Generate reports using Jest’s built-in features              |
| CI Integration      | Configure CI pipelines (GitHub Actions/GitLab CI) for automated testing |
| Notifications       | Add Slack/email for failure alerts                           |
| Deployment          | Proceed only if tests pass                                   |

---

## Different Tools for Unit Testing

| Tool                  | Description                                  | Key Features                      | Use Cases                        |
|-----------------------|----------------------------------------------|-----------------------------------|----------------------------------|
| Jest                  | Default test runner for React (by Meta)      | Snapshot testing, mocking, fast execution | All-purpose test execution     |
| React Testing Library | Focused on testing React components          | DOM interaction, better test semantics | Component and UI testing       |
| Enzyme (Deprecated)   | Legacy tool for component testing (Airbnb)   | Shallow rendering, lifecycle testing | Legacy codebases               |
| Cypress               | End-to-end test framework                    | UI testing, assertions with DOM   | Integration & UI flow testing   |
| Vitest                | Fast unit testing with Vite compatibility    | Vite-native speed, snapshot support | Modern Vite-based React projects |

---

## Comparison of Different Tools

| Criteria         | Jest | React Testing Library | Cypress | Vitest     |
|------------------|------|------------------------|---------|------------|
| Purpose          | Unit & snapshot testing | UI behavior testing | E2E testing | Unit + fast CI |
| Mocking Support  | ✅    | ✅ (via Jest)           | ⚠️ Limited | ✅         |
| Speed            | Fast | Fast                   | Slower  | Very Fast  |
| Community        | Very Large | Large          | Large   | Growing    |
| CI Integration   | ✅    | ✅                      | ✅       | ✅         |

---

## Advantages of Unit Testing

| Benefit                  | Description                                     |
|--------------------------|-------------------------------------------------|
| Faster Feedback Loops    | Catch bugs early in development                 |
| Improved Component Design| Encourages modular and testable code           |
| Prevents Regressions     | Ensures new changes don’t break old features   |
| Higher Developer Confidence | Safer deployments and changes              |
| Easy CI Integration      | Supports automation and fast delivery          |

---

## Proof of Concept (POC)

You can refer to the POC implementation at:  
**React Unit Testing POC**

---

## Best Practices of Unit Testing

| Best Practice                   | Description                                        |
|---------------------------------|----------------------------------------------------|
| Test Behavior, Not Implementation | Focus on what the component does, not how it does it. |
| Use Mocking for External APIs   | Avoid actual API calls; use Jest mock functions.  |
| Keep Tests Isolated             | Tests should not depend on global state.          |
| Leverage Test IDs               | Use data-testid for stable DOM queries.           |
| Maintain 80–90% Coverage        | Helps balance quality and effort.                 |
| CI Execution on PR              | Run all tests on each pull request.               |
| Use Linting & Formatting        | Keep test code clean and consistent.              |

---

## Recommendations / Conclusion

Jest combined with React Testing Library offers the most robust, flexible, and developer-friendly experience for unit testing React applications. It is simple to integrate with CI/CD pipelines and provides excellent debugging and coverage tools. For modern setups using Vite, Vitest is also a strong alternative.

**Recommended Tool for Most React Projects**: Jest + React Testing Library

---

## Contact

| Name              | Email                                         |
|-------------------|-----------------------------------------------|
| Himanshu Parashar | himanshu.parashar.snaatak@mygurukulam.co      |

---

## References

| Tool                  | Documentation Link                                                |
|-----------------------|-------------------------------------------------------------------|
| Jest                  | https://jestjs.io/docs/getting-started                            |
| React Testing Library | https://testing-library.com/docs/react-testing-library/intro     |
| Vitest                | https://vitest.dev/                                               |
| Cypress               | https://docs.cypress.io/                                          |
| GitHub Actions        | https://docs.github.com/en/actions                                |
