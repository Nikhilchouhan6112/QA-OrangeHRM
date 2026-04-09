# Test Plan — OrangeHRM Web Application

**Document Version:** 1.0  
**Prepared By:** QA Intern  
**Date:** April 2026  
**Status:** Approved

---

## 1. Introduction

### 1.1 Purpose
This Test Plan describes the testing approach, scope, resources, and schedule for testing the **OrangeHRM** Human Resource Management web application. It serves as a guide for executing manual tests and reporting defects.

### 1.2 Project Overview
OrangeHRM is a widely-used open-source HR management system. This testing project specifically targets the publicly available demo instance to evaluate the quality of its key modules from an end-user's perspective.

- **Application:** OrangeHRM Demo
- **URL:** https://opensource-demo.orangehrmlive.com/
- **Demo Credentials:** Admin / admin123

---

## 2. Scope

### 2.1 In Scope
The following modules will be tested:

| Module              | Features Covered                                   |
|---------------------|----------------------------------------------------|
| Login / Authentication | Valid login, invalid login, blank fields, logout  |
| Employee Management | Add employee, search, view, edit employee details  |
| Leave Management    | Apply leave, view leave balance, approve/reject    |

### 2.2 Out of Scope
- Performance / Load Testing
- Automation Testing
- API Testing
- Mobile responsiveness testing
- Security / Penetration Testing
- Modules: Recruitment, Time, Reports, Admin configuration

---

## 3. Test Objectives
- Verify that all in-scope features work as per expected behavior
- Identify defects and document them with clear reproduction steps
- Ensure a smooth user experience for core HR workflows
- Achieve at least 75% pass rate on executed test cases

---

## 4. Test Strategy

### 4.1 Testing Types
| Test Type         | Description                                                  |
|-------------------|--------------------------------------------------------------|
| Functional Testing | Verify each feature works as expected                       |
| Negative Testing   | Input invalid data to check system handles errors gracefully |
| UI Testing         | Check labels, buttons, placeholders, and layout             |
| Boundary Testing   | Test at edge input values (max/min characters, dates, etc.) |

### 4.2 Test Levels
- **System Testing** — End-to-end feature validation
- **Acceptance Testing** — Verifying features meet expected criteria

### 4.3 Test Design Techniques
- **Equivalence Partitioning** — Grouping valid/invalid input ranges
- **Boundary Value Analysis** — Testing at min/max limits
- **Error Guessing** — Based on experience and common failure patterns

---

## 5. Test Environment

| Component       | Details                                      |
|-----------------|----------------------------------------------|
| Browser         | Google Chrome (Latest Version)               |
| OS              | Windows 10/11                                |
| URL             | https://opensource-demo.orangehrmlive.com/   |
| Username        | Admin                                        |
| Password        | admin123                                     |
| Screen Res.     | 1920 x 1080                                  |
| Internet        | Broadband (stable connection required)       |

---

## 6. Test Schedule

| Phase                  | Start Date   | End Date     |
|------------------------|--------------|--------------|
| Test Planning          | April 1, 2026  | April 2, 2026  |
| Test Case Design       | April 3, 2026  | April 5, 2026  |
| Test Execution         | April 6, 2026  | April 8, 2026  |
| Defect Reporting       | April 6, 2026  | April 8, 2026  |
| Test Summary Report    | April 9, 2026  | April 9, 2026  |

---

## 7. Entry & Exit Criteria

### 7.1 Entry Criteria (Start Testing When…)
- Test environment is set up and accessible
- Test cases have been reviewed and approved
- Demo application is live and accessible
- Browser is configured correctly

### 7.2 Exit Criteria (Stop Testing When…)
- All planned test cases have been executed
- All critical and major bugs have been reported
- Test summary report has been prepared
- Pass rate ≥ 75% achieved

---

## 8. Test Deliverables

| Deliverable              | Description                                |
|--------------------------|--------------------------------------------|
| Test Plan                | This document                              |
| Test Cases               | Detailed step-by-step test cases           |
| Bug Reports              | Defect details with reproduction steps     |
| Test Summary Report      | Final execution metrics and sign-off       |

---

## 9. Roles & Responsibilities

| Role         | Name       | Responsibility                                          |
|--------------|------------|----------------------------------------------------------|
| QA Intern    | [Your Name]| Test case design, execution, bug reporting, documentation|
| Reviewer     | Self-review| Reviewing test artifacts                                 |

---

## 10. Risk & Mitigation

| Risk                                  | Likelihood | Impact | Mitigation Strategy                           |
|---------------------------------------|------------|--------|-----------------------------------------------|
| Demo site may be slow/down            | Medium     | High   | Test during off-peak hours; retry on next day |
| Shared test data modified by others   | High       | Medium | Document current state before testing begins  |
| Limited test time                     | Low        | Medium | Prioritize critical test cases first          |

---

## 11. Defect Management

- All bugs will be documented in the `Bug-Reports/` directory
- Each bug follows the standard bug report template
- **Severity Levels:** Critical → Major → Minor → Trivial
- **Priority Levels:** High → Medium → Low

---

## 12. Approvals

| Role       | Name         | Signature | Date         |
|------------|--------------|-----------|--------------|
| QA Intern  | [Your Name]  | ✅         | April 2026   |
