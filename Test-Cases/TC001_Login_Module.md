# Test Cases — Login Module

**Module:** Login / Authentication  
**Application:** OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/)  
**Prepared By:** QA Intern  
**Date:** April 2026  
**Total Test Cases:** 10

---

## Test Case Template Reference

| Field            | Description                                      |
|------------------|--------------------------------------------------|
| Test Case ID     | Unique identifier (TC-LOG-XXX)                   |
| Title            | Short description of what is being tested        |
| Module           | Feature area                                     |
| Test Type        | Positive / Negative / UI                         |
| Priority         | High / Medium / Low                              |
| Preconditions    | Setup needed before test execution               |
| Test Steps       | Step-by-step actions                             |
| Expected Result  | What should happen                               |
| Actual Result    | What actually happened during execution          |
| Status           | Pass ✅ / Fail ❌ / Blocked 🔒                    |

---

## TC-LOG-001: Valid Login with Correct Credentials

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-001                                                          |
| **Title**        | Login with valid username and password                              |
| **Module**       | Login                                                               |
| **Test Type**    | Positive                                                            |
| **Priority**     | High                                                                |
| **Preconditions**| Browser is open; application URL is loaded                          |
| **Test Steps**   | 1. Navigate to https://opensource-demo.orangehrmlive.com/ <br> 2. Enter username: `Admin` <br> 3. Enter password: `admin123` <br> 4. Click the **Login** button |
| **Expected Result** | User is successfully logged in and redirected to the Dashboard  |
| **Actual Result**   | User is redirected to the Dashboard successfully                |
| **Status**       | ✅ Pass                                                              |
| **Remarks**      | Core login functionality works as expected                          |

---

## TC-LOG-002: Login with Invalid Password

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-002                                                          |
| **Title**        | Login with valid username and incorrect password                    |
| **Module**       | Login                                                               |
| **Test Type**    | Negative                                                            |
| **Priority**     | High                                                                |
| **Preconditions**| Browser is open; application URL is loaded                          |
| **Test Steps**   | 1. Navigate to the login page <br> 2. Enter username: `Admin` <br> 3. Enter password: `wrongpassword` <br> 4. Click the **Login** button |
| **Expected Result** | Error message displayed: *"Invalid credentials"*                |
| **Actual Result**   | Error message is displayed                                       |
| **Status**       | ✅ Pass                                                              |
| **Remarks**      | —                                                                   |

---

## TC-LOG-003: Login with Invalid Username

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-003                                                          |
| **Title**        | Login with incorrect username and correct password                  |
| **Module**       | Login                                                               |
| **Test Type**    | Negative                                                            |
| **Priority**     | High                                                                |
| **Preconditions**| Browser is open; application URL is loaded                          |
| **Test Steps**   | 1. Navigate to the login page <br> 2. Enter username: `wronguser` <br> 3. Enter password: `admin123` <br> 4. Click the **Login** button |
| **Expected Result** | Error message displayed: *"Invalid credentials"*                |
| **Actual Result**   | Error message is displayed                                       |
| **Status**       | ✅ Pass                                                              |
| **Remarks**      | —                                                                   |

---

## TC-LOG-004: Login with Blank Username

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-004                                                          |
| **Title**        | Login with username field left empty                                |
| **Module**       | Login                                                               |
| **Test Type**    | Negative                                                            |
| **Priority**     | High                                                                |
| **Preconditions**| Browser is open; application URL is loaded                          |
| **Test Steps**   | 1. Navigate to the login page <br> 2. Leave username blank <br> 3. Enter password: `admin123` <br> 4. Click the **Login** button |
| **Expected Result** | Validation message: *"Required"* shown under username field     |
| **Actual Result**   | Validation message is shown                                      |
| **Status**       | ✅ Pass                                                              |
| **Remarks**      | —                                                                   |

---

## TC-LOG-005: Login with Blank Password

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-005                                                          |
| **Title**        | Login with password field left empty                                |
| **Module**       | Login                                                               |
| **Test Type**    | Negative                                                            |
| **Priority**     | High                                                                |
| **Preconditions**| Browser is open; application URL is loaded                          |
| **Test Steps**   | 1. Navigate to the login page <br> 2. Enter username: `Admin` <br> 3. Leave password blank <br> 4. Click the **Login** button |
| **Expected Result** | Validation message: *"Required"* shown under password field     |
| **Actual Result**   | Validation message is shown                                      |
| **Status**       | ✅ Pass                                                              |
| **Remarks**      | —                                                                   |

---

## TC-LOG-006: Login with Both Fields Blank

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-006                                                          |
| **Title**        | Login with both username and password fields empty                  |
| **Module**       | Login                                                               |
| **Test Type**    | Negative                                                            |
| **Priority**     | Medium                                                              |
| **Preconditions**| Browser is open; application URL is loaded                          |
| **Test Steps**   | 1. Navigate to the login page <br> 2. Leave both fields blank <br> 3. Click the **Login** button |
| **Expected Result** | Validation messages shown on both fields                        |
| **Actual Result**   | Validation messages are shown on both fields                    |
| **Status**       | ✅ Pass                                                              |
| **Remarks**      | —                                                                   |

---

## TC-LOG-007: Case Sensitivity of Username Field

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-007                                                          |
| **Title**        | Verify username field is case-sensitive                             |
| **Module**       | Login                                                               |
| **Test Type**    | Negative                                                            |
| **Priority**     | Medium                                                              |
| **Preconditions**| Browser is open; application URL is loaded                          |
| **Test Steps**   | 1. Navigate to the login page <br> 2. Enter username: `admin` (lowercase) <br> 3. Enter password: `admin123` <br> 4. Click **Login** |
| **Expected Result** | Login fails with *"Invalid credentials"* message                |
| **Actual Result**   | Login fails with invalid credentials message                    |
| **Status**       | ✅ Pass                                                              |
| **Remarks**      | Username is case-sensitive as expected                              |

---

## TC-LOG-008: Password Masking Verification

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-008                                                          |
| **Title**        | Verify password is masked by default                                |
| **Module**       | Login                                                               |
| **Test Type**    | UI                                                                  |
| **Priority**     | Medium                                                              |
| **Preconditions**| Browser is open; application URL is loaded                          |
| **Test Steps**   | 1. Navigate to the login page <br> 2. Click on the password field <br> 3. Type any characters <br> 4. Observe the field input |
| **Expected Result** | Characters appear as dots/asterisks (masked)                    |
| **Actual Result**   | Characters appear as dots                                        |
| **Status**       | ✅ Pass                                                              |
| **Remarks**      | —                                                                   |

---

## TC-LOG-009: Logout Functionality

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-009                                                          |
| **Title**        | Verify user can successfully logout                                 |
| **Module**       | Login                                                               |
| **Test Type**    | Positive                                                            |
| **Priority**     | High                                                                |
| **Preconditions**| User is logged into the application                                 |
| **Test Steps**   | 1. After logging in, click on the user avatar/name (top-right) <br> 2. Click **Logout** from the dropdown menu |
| **Expected Result** | User is logged out and redirected to the login page             |
| **Actual Result**   | User is redirected to login page                                 |
| **Status**       | ✅ Pass                                                              |
| **Remarks**      | —                                                                   |

---

## TC-LOG-010: Session Persistence After Logout (Back Button Test)

| Field            | Details                                                             |
|------------------|---------------------------------------------------------------------|
| **Test Case ID** | TC-LOG-010                                                          |
| **Title**        | Verify browser back button does not bypass logout                   |
| **Module**       | Login                                                               |
| **Test Type**    | Negative / Security                                                 |
| **Priority**     | High                                                                |
| **Preconditions**| User is logged in and then logs out                                 |
| **Test Steps**   | 1. Log in with valid credentials <br> 2. Navigate to the Dashboard <br> 3. Click **Logout** <br> 4. Press the browser **Back** button |
| **Expected Result** | User is NOT taken back to Dashboard; login page is shown OR a session-expired message appears |
| **Actual Result**   | Dashboard page briefly appears before redirecting to login — session data is still accessible momentarily |
| **Status**       | ❌ Fail                                                              |
| **Remarks**      | **Bug Reported:** BUG-006 — Session persistence after logout        |

---

## Test Cases Summary — Login Module

| Test Case ID | Title                                 | Status  |
|--------------|---------------------------------------|---------|
| TC-LOG-001   | Valid login                           | ✅ Pass  |
| TC-LOG-002   | Invalid password                      | ✅ Pass  |
| TC-LOG-003   | Invalid username                      | ✅ Pass  |
| TC-LOG-004   | Blank username                        | ✅ Pass  |
| TC-LOG-005   | Blank password                        | ✅ Pass  |
| TC-LOG-006   | Both fields blank                     | ✅ Pass  |
| TC-LOG-007   | Case sensitivity                      | ✅ Pass  |
| TC-LOG-008   | Password masking                      | ✅ Pass  |
| TC-LOG-009   | Logout                                | ✅ Pass  |
| TC-LOG-010   | Back button after logout              | ❌ Fail  |

**Pass: 9 | Fail: 1 | Pass Rate: 90%**
