# Bug Report — BUG-003

---

## Bug Summary

| Field              | Details                                                       |
|--------------------|---------------------------------------------------------------|
| **Bug ID**         | BUG-003                                                       |
| **Title**          | Leave balance does not update correctly after leave approval  |
| **Module**         | Leave Management                                              |
| **Reported By**    | QA Intern                                                     |
| **Date Reported**  | April 7, 2026                                                 |
| **Severity**       | Critical                                                      |
| **Priority**       | High                                                          |
| **Status**         | Open                                                          |
| **Test Case Ref**  | TC-LVE-004                                                    |
| **Environment**    | Chrome (Latest), Windows 11, OrangeHRM Demo                   |
| **Build/Version**  | OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/)   |

---

## Description

After an admin **approves** a leave request, the employee's **remaining leave balance** does not immediately reflect the deduction. The balance displayed in the **Leave Entitlement / My Leave** section still shows the original unused balance, even though the leave has been approved and should have been deducted.

This is the **most critical bug** found during testing as it directly impacts HR operations and payroll accuracy.

---

## Steps to Reproduce

1. Log in as **Admin**
2. Navigate to **Leave → My Leave** — note the current **Annual Leave** balance (e.g., 14 days)
3. Navigate to **Leave → Apply**
4. Select Leave Type: `Annual Leave`
5. Enter From Date: **2 days from today** (future weekday)
6. Enter To Date: **4 days from today** (2 working days)
7. Click **Apply** — leave is submitted successfully
8. Log in as Admin and navigate to **Leave → Leave List**
9. Approve the leave request
10. Navigate back to **Leave → My Leave** or **Entitlement & Usage**
11. Observe the remaining balance

---

## Expected Result

- Leave balance should decrease by the number of approved leave days
- If the original balance was **14 days** and **2 days** were approved, the new balance should show **12 days**

---

## Actual Result

- Balance still shows **14 days** (unchanged)
- The approved leave is listed, but the entitlement balance is not recalculated
- Hard page refresh also does not fix the balance display

---

## Impact

- **Severity: Critical** — Incorrect leave balance affects payroll processing and HR decision-making
- Employees may apply for more leave than they are entitled to
- Managers may make incorrect staffing decisions based on wrong availability data

---


## Suggested Fix

The leave balance should be recalculated and synced in real-time when a leave is approved. This likely requires a backend fix to properly subtract approved leave days from the entitlement record and trigger a UI refresh.
