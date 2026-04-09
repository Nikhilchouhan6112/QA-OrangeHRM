# Test Summary Report — OrangeHRM Web Application

**Project:** Manual QA Testing — OrangeHRM HR Management System
**Prepared By:** QA Intern
**Date:** April 9, 2026
**Document Version:** 1.0
**Status:** Final

---

## 1. Executive Summary

This report summarizes the results of manual functional testing conducted on the **OrangeHRM Demo** web application. Testing was performed across three core modules: **Login/Authentication**, **Employee Management (PIM)**, and **Leave Management**.

A total of **30 test cases** were executed. **6 defects** were identified — 1 Critical, 2 Major, and 3 Minor. The overall pass rate achieved was **80%**, meeting the exit criteria of ≥75% defined in the Test Plan.

---

## 2. Test Scope

| Module              | Test Cases Executed | Pass | Fail | Pass Rate |
|---------------------|---------------------|------|------|-----------|
| Login / Auth        | 10                  | 9    | 1    | 90%       |
| Employee Management | 10                  | 8    | 2    | 80%       |
| Leave Management    | 10                  | 8    | 2    | 80%       |
| **Total**           | **30**              | **25** | **5** |**83%**  |

> **Note:** One additional defect (BUG-001) was identified as a security concern during exploratory testing outside of formal test case execution, bringing total bugs to 6.

---

## 3. Test Execution Details

| Metric                    | Value         |
|---------------------------|---------------|
| Test Execution Start Date | April 6, 2026 |
| Test Execution End Date   | April 8, 2026 |
| Total Test Cases Planned  | 30            |
| Total Test Cases Executed | 30            |
| Test Cases Passed         | 25            |
| Test Cases Failed         | 5             |
| Test Cases Blocked        | 0             |
| Test Cases Skipped        | 0             |
| Overall Pass Rate         | **83%**       |

---

## 4. Defect Summary

| Bug ID  | Title                                              | Severity | Priority | Status |
|---------|----------------------------------------------------|----------|----------|--------|
| BUG-001 | Misleading error message & no account lockout on login | Major    | High     | Open   |
| BUG-002 | No input validation on Employee Name field         | Major    | High     | Open   |
| BUG-003 | Leave balance does not update after approval       | Critical | High     | Open   |
| BUG-004 | Employee profile photo upload fails intermittently | Minor    | Medium   | Open   |
| BUG-005 | Leave application accepts past dates               | Major    | High     | Open   |
| BUG-006 | Browser back button shows dashboard after logout   | Major    | High     | Open   |

---

## 5. Defect Distribution

### By Severity

| Severity | Count | Percentage |
|----------|-------|------------|
| Critical | 1     | 17%        |
| Major    | 4     | 67%        |
| Minor    | 1     | 17%        |

```
Critical  ██░░░░░░░░░░  1
Major     ████████░░░░  4
Minor     ██░░░░░░░░░░  1
```

### By Module

| Module              | Bugs Found |
|---------------------|------------|
| Login / Auth        | 2          |
| Employee Management | 2          |
| Leave Management    | 2          |

### By Priority

| Priority | Count |
|----------|-------|
| High     | 5     |
| Medium   | 1     |
| Low      | 0     |

---

## 6. Test Environment

| Component    | Details                                             |
|--------------|-----------------------------------------------------|
| Application  | OrangeHRM Demo                                      |
| URL          | https://opensource-demo.orangehrmlive.com/          |
| Browser      | Google Chrome (Latest)                              |
| OS           | Windows 11                                          |
| Resolution   | 1920 × 1080                                         |
| Test Type    | Manual / Functional / UI                            |
| Credential   | Admin / admin123                                    |

---

## 7. Test Coverage Analysis

### Features Tested ✅

- [x] Login with valid credentials
- [x] Login with invalid/blank credentials
- [x] Password masking
- [x] Logout & session management
- [x] Add, search, edit, delete employee
- [x] Employee profile photo upload
- [x] Apply for leave (valid/invalid)
- [x] Leave balance display
- [x] Leave approval/rejection by admin
- [x] Date picker boundary conditions

### Features Not Tested (Out of Scope) ❌

- [ ] Recruitment Module
- [ ] Time & Attendance Module
- [ ] Performance Management
- [ ] Reports & Analytics
- [ ] Admin Configuration
- [ ] API endpoints
- [ ] Mobile / Responsive layout
- [ ] Cross-browser testing (Firefox, Safari, Edge)

---

## 8. Key Observations & Findings

### 🔴 Critical Finding
- **BUG-003** (Leave balance mismatch) is the most severe issue found. It directly affects HR data integrity and could have downstream effects on payroll and compliance reporting.

### 🟠 Security Findings
- **BUG-001** (No login lockout) and **BUG-006** (Session back-button access) suggest that security best practices (OWASP guidelines) are not fully implemented. These must be addressed before any production deployment.

### 🟡 Data Validation Gaps
- **BUG-002** and **BUG-005** indicate insufficient input validation — both client-side and server-side. A comprehensive validation layer should be implemented across all form fields.

### 🟢 Positive Observations
- Core workflows (valid login, add employee, approve leave) function correctly
- The UI is clean and navigable — form layouts are intuitive
- Toast notifications appear for most success/failure actions
- Confirmation dialogs before destructive actions (like delete) are implemented

---

## 9. Risks & Recommendations

| Risk                                      | Recommendation                                                     |
|-------------------------------------------|--------------------------------------------------------------------|
| Leave balance inconsistency               | Fix server-side leave deduction logic immediately                  |
| No brute-force protection on login        | Implement account lockout after N failed attempts                  |
| Session not fully invalidated on logout   | Add cache-control headers & server-side session invalidation       |
| Missing input validation on name fields   | Add regex-based validation on all text fields                      |
| Photo upload unreliability                | Fix server-side file persistence; add proper error messaging       |
| Past-date leave accepted                  | Add date validation (client + server) to reject past leave dates   |

---

## 10. Exit Criteria Verification

| Criterion                             | Target  | Achieved | Met?     |
|---------------------------------------|---------|----------|----------|
| All planned test cases executed       | 30      | 30       | ✅ Yes    |
| Overall pass rate                     | ≥ 75%   | 83%      | ✅ Yes    |
| All critical bugs reported            | 100%    | 100%     | ✅ Yes    |
| Test summary report prepared          | Yes     | Yes      | ✅ Yes    |

**All exit criteria have been met. Testing is complete.**

---

## 11. Conclusion

The OrangeHRM demo application was tested across 3 modules with 30 test cases executed. The application demonstrates functional core workflows but has notable defects — particularly around **security (session management, login lockout)**, **data integrity (leave balance)**, and **input validation**.

It is recommended that the **1 Critical** and **4 Major** bugs be resolved before the application is considered production-ready. The **1 Minor** bug may be addressed in a subsequent release.

---

## 12. Sign-Off

| Role         | Name          | Date           | Signature |
|--------------|---------------|----------------|-----------|
| QA Intern    | [Your Name]   | April 9, 2026  | ✅         |

---

*This report is prepared as part of a QA portfolio project for internship/job applications. Testing was conducted on the publicly available OrangeHRM demo environment.*
