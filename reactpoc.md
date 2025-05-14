
# React CI Check | Unit Testing | POC

| Author     | Created on | Version | Last updated by | Last Edited On | Level             | Reviewer        |
|------------|------------|---------|------------------|----------------|-------------------|-----------------|
| Himanshu   | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | L0                | Imran           |
| Himanshu   | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | L1                | Shashi          |
| Himanshu   | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | L2                | Mahesh Kumar    |
| Himanshu   | 2025-05-15 | 1.0     | Himanshu         | 2025-05-15     | Internal Reviewer | Komal Jaiswal   |

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

Install testing dependencies:

```bash
npm install --save-dev @testing-library/react@12.1.5 @testing-library/jest-dom@5.16.5
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

### Test Case Updates

#### Updated Test Files

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

---

### Why Use MemoryRouter?

- **<MemoryRouter>** creates an **in-memory history stack** to simulate routing behavior during tests without modifying browser history.
- It is necessary when components use React Router features like Link, useNavigate, etc.
- Ideal for unit testing: avoids needing a real DOM or full routing setup.

---

### Install Testing Dependencies

If not already done, install project dependencies:

```bash
npm install
```

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

Sample output:

```
PASS  src/__tests__/HomePage.test.js
PASS  src/__tests__/AttendanceForm.test.js
PASS  src/__tests__/EmployeeList.test.js
```

---

### Generating the Report

#### Generate Coverage Report

```bash
npm test -- --coverage
```

Sample output:

| File         | % Stmts | % Branch | % Funcs | % Lines |
|--------------|---------|----------|--------|---------|
| All files    |   85.71 |       80 |     90 |   85.71 |

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

---

## Conclusion

Unit testing in React using Jest and React Testing Library ensures reliable component behavior, detects issues early, and supports CI pipelines. Wrapping routing-dependent components with **<MemoryRouter>** enables tests to run seamlessly.

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
