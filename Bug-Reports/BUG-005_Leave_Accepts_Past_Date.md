# Bug Report — BUG-005

---

## Bug Summary

| Field              | Details                                                            |
|--------------------|--------------------------------------------------------------------|
| **Bug ID**         | BUG-005                                                            |
| **Title**          | Leave application accepts past dates without validation error      |
| **Module**         | Leave Management                                                   |
| **Severity**       | Major                                                              |
| **Priority**       | High                                                               |
| **Status**         | Open                                                               |
| **Test Case Ref**  | TC-LVE-002                                                         |
| **Environment**    | Chrome (Latest), Windows 11, OrangeHRM Demo                        |
| **Build/Version**  | OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/)        |

---

## Description

The **Leave → Apply** form allows employees to submit leave applications using **past dates** without displaying any validation error. The system accepts and records the past-dated leave request as if it were valid, which is logically incorrect — an employee cannot retroactively apply for leave in HR workflows.

---

## Steps to Reproduce

1. Log in to OrangeHRM (Admin or Employee)
2. Navigate to **Leave → Apply**
3. Select Leave Type: `Annual Leave`
4. In the **From Date** field, manually type or select: `01/15/2024` *(a past date)*
5. In the **To Date** field, enter: `01/15/2024`
6. Click the **Apply** button
7. Observe whether a validation error appears

---

## Expected Result

- The system should prevent past-date leave submission
- A validation error message should display:
  > *"Leave start date cannot be in the past"*
- The **Apply** button should be disabled or the form should not submit

---

## Actual Result

- The leave form accepts the past date without any warning or error
- The leave application is submitted and appears in **My Leave** with "Pending Approval" status
- Admin can also approve this past-dated leave — no server-side check either

---

## Impact

- **Data Integrity:** Past-dated leaves appear in the system, distorting attendance and leave records
- **Payroll Risk:** Approved past leaves may incorrectly affect payroll calculations
- **Compliance Risk:** In regulated industries, retroactive leave applications require special approvals — this bypasses that control entirely

---


## Suggested Fix

- Add client-side date validation to disable or warn on past date selection in the date picker
- Add server-side validation to reject leave applications with past start dates
- Exception: If the business requires retroactive leave (e.g., sick leave filed late), implement a special approval workflow rather than silently accepting all past dates
