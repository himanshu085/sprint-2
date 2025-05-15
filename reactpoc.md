<p align="center">
  <img src="https://github.com/user-attachments/assets/23f64d70-2ea5-4030-ae31-12affaea2290" alt="Screenshot from 2025-05-15 10-58-00" width="450">
</p>

# React CI Check | Unit Testing | POC

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
- [Steps of Unit Testing](#steps-of-unit-testing)  
  - [Cloning the React Application](#cloning-the-react-application)  
  - [Test Case Updates](#test-case-updates)  
    - [Updated Test Files](#updated-test-files)  
    - [Why Use MemoryRouter?](#why-use-memoryrouter)  
  - [Install Testing Dependencies](#install-testing-dependencies)  
  - [Running the Tests](#running-the-tests)  
  - [Generating the Report](#generating-the-report)  
    - [Generate Coverage Report](#generate-coverage-report)  
    - [View Coverage Report](#view-coverage-report)  
- [Conclusion](#conclusion)  
- [Contact](#contact)  
- [Reference](#reference)  
---

## Introduction

In this document, we are creating a proof of concept (POC) for unit testing a React-based frontend application to validate component behavior and identify bugs early using **Jest** and **React Testing Library**.

---

## Prerequisites

Ensure Node.js (>=14) and npm (or yarn) are installed.

Verify setup:

```bash
sudo apt install -y nodejs npm
```

Check versions:

```bash
node -v
npm -v
```

---

## Steps of Unit Testing

### Cloning the React Application

```bash
mkdir React-Testing
cd React-Testing
git clone https://github.com/OT-MICROSERVICES/frontend.git
cd frontend
```
![Screenshot from 2025-05-15 02-34-50](https://github.com/user-attachments/assets/b2ad64fb-4a77-4c53-b0df-3613c2f05e5e)


### Test Case Updates

#### Updated Test Files
```bash
mkdir -p src/tests
vi src/tests/AttendanceForm.test.js
```

✅ **src/__tests__/AttendanceForm.test.js**

```javascript
import React from "react";
import { render } from "@testing-library/react";
import { MemoryRouter } from "react-router-dom";
import AttendanceForm from "../AttendanceForm";

test("renders AttendanceForm component without crashing", () => {
  render(
    <MemoryRouter>
      <AttendanceForm />
    </MemoryRouter>
  );
});
```
```bash
vi src/tests/EmployeeList.test.js
```

✅ **src/__tests__/EmployeeList.test.js**

```javascript
import React from "react";
import { render } from "@testing-library/react";
import { MemoryRouter } from "react-router-dom";
import EmployeeList from "../EmployeeList";

test("renders EmployeeList component without crashing", () => {
  render(
    <MemoryRouter>
      <EmployeeList />
    </MemoryRouter>
  );
});
```

```bash
vi src/tests/HomePage.test.js
```

✅ **src/__tests__/HomePage.test.js**

```javascript
import React from "react";
import { render } from "@testing-library/react";
import { MemoryRouter } from "react-router-dom";
import HomePage from "../HomePage.react";

test("renders HomePage component without crashing", () => {
  render(
    <MemoryRouter>
      <HomePage />
    </MemoryRouter>
  );
});
```
![Screenshot from 2025-05-15 02-31-44](https://github.com/user-attachments/assets/ff3a396d-0a34-410a-8ad8-7b62676d60c0)

---

### Why Use MemoryRouter?

- **<MemoryRouter>** creates an **in-memory history stack** to simulate routing behavior during tests without modifying browser history.
- It is necessary when components use React Router features like Link, useNavigate, etc.
- Ideal for unit testing: avoids needing a real DOM or full routing setup.

---

### Install Testing Dependencies

If not already done, install project dependencies:

```bash
npm install --save-dev @testing-library/react@12.1.5 @testing-library/jest-dom@5.16.5
```
![Screenshot from 2025-05-15 01-31-27](https://github.com/user-attachments/assets/d211fe5f-3df7-44ed-ac54-0a19c8cf3596)

---

### Running the Tests

React apps (via Create React App) come with **Jest** preconfigured.

Run all tests:

```bash
npm test
```

Or in CI mode:

```bash
npm test -- --watchAll=false
```
![Screenshot from 2025-05-15 01-30-00](https://github.com/user-attachments/assets/01122808-df4b-4837-a003-8b197e322b31)

Output:

![Screenshot from 2025-05-15 01-30-20](https://github.com/user-attachments/assets/0b21d270-7e6c-4824-802f-a35cd643bac6)

---

### Generating the Report

#### Generate Coverage Report

```bash
npm test -- --coverage
```

![Screenshot from 2025-05-15 01-36-34](https://github.com/user-attachments/assets/0042aa20-fa2a-4364-8b91-95d118078cac)

Output:

![Screenshot from 2025-05-15 01-37-02](https://github.com/user-attachments/assets/58271d0f-0086-4fb7-b574-3bb40a382f4c)


#### View Coverage Report

Open in browser:

```bash
xdg-open coverage/lcov-report/index.html  # Linux
open coverage/lcov-report/index.html      # macOS
```

Or manually navigate to:

```
coverage/lcov-report/index.html
```
![Screenshot from 2025-05-15 01-40-06](https://github.com/user-attachments/assets/eae4a359-3e98-4d5a-adb3-e0d69e275599)

---

## Conclusion

Unit testing in React using Jest and React Testing Library ensures the reliability of UI components, detects edge-case bugs early, improves code maintainability, and supports CI pipelines. This POC confirms the ability to run CI-compatible unit tests and generate insightful coverage reports for the React application in the frontend repository. Wrapping routing-dependent components with <MemoryRouter> ensures seamless test execution without relying on a real DOM or full routing setup.

---

## Contact

| Name              | Email                                         |
|-------------------|-----------------------------------------------|
| Himanshu Parashar | himanshu.parashar.snaatak@mygurukulam.co      |

---

## Reference

| Link                                                                 | Description                                      |
|----------------------------------------------------------------------|--------------------------------------------------|
| [React Testing Library Docs](https://testing-library.com/docs/react-testing-library/intro/) | Official guide for unit testing React components |
| [Jest Documentation](https://jestjs.io/docs/getting-started)         | JavaScript testing framework documentation       |
