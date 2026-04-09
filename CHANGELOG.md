# Changelog

All notable changes to this QA project are documented here.

---

## [1.0.0] — April 9, 2026

### 🎉 Initial Release

#### Added
- `README.md` — Full project overview with badges, structure, and metrics
- `Test-Plan/Test_Plan.md` — Scope, strategy, risks, entry/exit criteria
- `Test-Cases/TC001_Login_Module.md` — 10 test cases for Login/Auth module
- `Test-Cases/TC002_Employee_Management.md` — 10 test cases for Employee Management
- `Test-Cases/TC003_Leave_Management.md` — 10 test cases for Leave Management
- `Bug-Reports/BUG-001_Login_Error_Message.md` — No account lockout (Major)
- `Bug-Reports/BUG-002_No_Validation_Employee_Name.md` — Input validation missing (Major)
- `Bug-Reports/BUG-003_Leave_Balance_Mismatch.md` — Balance not updated (Critical)
- `Bug-Reports/BUG-004_Profile_Photo_Upload_Failure.md` — Intermittent upload fail (Minor)
- `Bug-Reports/BUG-005_Leave_Accepts_Past_Date.md` — Past date accepted (Major)
- `Bug-Reports/BUG-006_Logout_Session_Persistence.md` — Session not invalidated (Major)

- `Summary-Report/Test_Summary_Report.md` — Final test closure report

#### Test Results
- **Total Test Cases:** 30
- **Passed:** 25 | **Failed:** 5
- **Pass Rate:** 83%
- **Bugs Found:** 6 (1 Critical, 4 Major, 1 Minor)
