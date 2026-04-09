# Test Cases — Leave Management Module

**Module:** Leave Management
**Application:** OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/)
**Total Test Cases:** 10

---

## TC-LVE-001: Apply for Leave with Valid Data

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-001                                                              |
| **Title**         | Apply for leave with all valid inputs                                   |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Positive                                                                |
| **Priority**      | High                                                                    |
| **Preconditions** | Admin/Employee is logged in; navigate to Leave → Apply                  |
| **Test Steps**    | 1. Navigate to **Leave → Apply** <br> 2. Select Leave Type: `Annual Leave` <br> 3. Enter **From Date**: a future weekday <br> 4. Enter **To Date**: same or later weekday <br> 5. Enter comment (optional) <br> 6. Click **Apply** |
| **Expected Result** | Leave request is submitted; success message is displayed              |
| **Actual Result**   | Leave request submitted successfully with confirmation                |
| **Status**        | ✅ Pass                                                                  |
| **Remarks**       | —                                                                       |

---

## TC-LVE-002: Apply for Leave with Past Date

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-002                                                              |
| **Title**         | Apply for leave using a past date                                       |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Negative                                                                |
| **Priority**      | High                                                                    |
| **Preconditions** | Admin/Employee is logged in; navigate to Leave → Apply                  |
| **Test Steps**    | 1. Navigate to **Leave → Apply** <br> 2. Select Leave Type: `Annual Leave` <br> 3. Enter **From Date**: `01/01/2020` (past date) <br> 4. Enter **To Date**: `01/01/2020` <br> 5. Click **Apply** |
| **Expected Result** | Validation error: *"Date is in the past"* or similar message          |
| **Actual Result**   | System accepts past date and submits leave — no validation             |
| **Status**        | ❌ Fail                                                                  |
| **Remarks**       | **Bug Reported:** BUG-005 — Leave application accepts past dates        |

---

## TC-LVE-003: Apply for Leave with End Date Before Start Date

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-003                                                              |
| **Title**         | Apply for leave where To Date is before From Date                       |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Negative                                                                |
| **Priority**      | High                                                                    |
| **Preconditions** | Admin/Employee is logged in                                             |
| **Test Steps**    | 1. Navigate to **Leave → Apply** <br> 2. Select Leave Type: `Annual Leave` <br> 3. Enter **From Date**: `05/30/2026` <br> 4. Enter **To Date**: `05/01/2026` <br> 5. Click **Apply** |
| **Expected Result** | Validation error: *"To date should be after From date"*               |
| **Actual Result**   | Validation error is displayed                                         |
| **Status**        | ✅ Pass                                                                  |
| **Remarks**       | —                                                                       |

---

## TC-LVE-004: View Leave Balance

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-004                                                              |
| **Title**         | Verify that leave balance is displayed correctly                        |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Positive                                                                |
| **Priority**      | High                                                                    |
| **Preconditions** | Admin/Employee is logged in                                             |
| **Test Steps**    | 1. Navigate to **Leave → My Leave** or **Leave Entitlement** <br> 2. Observe the leave balance table for each leave type |
| **Expected Result** | Leave balance is shown correctly for each leave type                  |
| **Actual Result**   | Leave balances display inconsistently after applying a leave request   |
| **Status**        | ❌ Fail                                                                  |
| **Remarks**       | **Bug Reported:** BUG-003 — Leave balance not updating correctly        |

---

## TC-LVE-005: Apply Leave Without Selecting Leave Type

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-005                                                              |
| **Title**         | Submit leave application without selecting a leave type                 |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Negative                                                                |
| **Priority**      | Medium                                                                  |
| **Preconditions** | Admin/Employee is logged in; navigate to Leave → Apply                  |
| **Test Steps**    | 1. Navigate to **Leave → Apply** <br> 2. Leave the **Leave Type** dropdown unselected <br> 3. Enter valid From and To dates <br> 4. Click **Apply** |
| **Expected Result** | Validation error: *"Required"* next to Leave Type field               |
| **Actual Result**   | Validation error is shown                                             |
| **Status**        | ✅ Pass                                                                  |
| **Remarks**       | —                                                                       |

---

## TC-LVE-006: Cancel a Pending Leave Request

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-006                                                              |
| **Title**         | Cancel a leave request that is in Pending status                        |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Positive                                                                |
| **Priority**      | Medium                                                                  |
| **Preconditions** | At least one leave request is in **Pending Approval** status            |
| **Test Steps**    | 1. Navigate to **Leave → My Leave** <br> 2. Locate a leave in **Pending Approval** status <br> 3. Click **Cancel** on the record |
| **Expected Result** | Leave status changes to **Cancelled**                                 |
| **Actual Result**   | Leave status changes to Cancelled                                     |
| **Status**        | ✅ Pass                                                                  |
| **Remarks**       | —                                                                       |

---

## TC-LVE-007: Admin Approves a Leave Request

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-007                                                              |
| **Title**         | Admin approves a pending leave request                                  |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Positive                                                                |
| **Priority**      | High                                                                    |
| **Preconditions** | Admin is logged in; at least one leave request is pending               |
| **Test Steps**    | 1. Navigate to **Leave → Leave List** <br> 2. Find a leave in **Pending Approval** <br> 3. Click **Approve** |
| **Expected Result** | Leave status changes to **Approved**                                  |
| **Actual Result**   | Leave status changes to Approved                                      |
| **Status**        | ✅ Pass                                                                  |
| **Remarks**       | —                                                                       |

---

## TC-LVE-008: Admin Rejects a Leave Request

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-008                                                              |
| **Title**         | Admin rejects a pending leave request                                   |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Positive                                                                |
| **Priority**      | Medium                                                                  |
| **Preconditions** | Admin is logged in; at least one leave request is pending               |
| **Test Steps**    | 1. Navigate to **Leave → Leave List** <br> 2. Find a pending leave <br> 3. Click **Reject** |
| **Expected Result** | Leave status changes to **Rejected**                                  |
| **Actual Result**   | Leave status changes to Rejected                                      |
| **Status**        | ✅ Pass                                                                  |
| **Remarks**       | —                                                                       |

---

## TC-LVE-009: Apply for Leave on a Weekend

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-009                                                              |
| **Title**         | Apply for leave on a Saturday or Sunday                                 |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Negative / Boundary                                                     |
| **Priority**      | Medium                                                                  |
| **Preconditions** | Admin/Employee is logged in; navigate to Leave → Apply                  |
| **Test Steps**    | 1. Navigate to **Leave → Apply** <br> 2. Select Leave Type <br> 3. Set From Date and To Date to a Saturday/Sunday <br> 4. Click **Apply** |
| **Expected Result** | Message: *"Leave on non-working days will not be counted"* OR warning message |
| **Actual Result**   | Warning/info message shown indicating weekend selection                |
| **Status**        | ✅ Pass                                                                  |
| **Remarks**       | System handles weekend selection appropriately                          |

---

## TC-LVE-010: Search Leave Requests by Employee Name

| Field             | Details                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Test Case ID**  | TC-LVE-010                                                              |
| **Title**         | Search leave records by employee name in Leave List                     |
| **Module**        | Leave Management                                                        |
| **Test Type**     | Positive                                                                |
| **Priority**      | Low                                                                     |
| **Preconditions** | Admin is logged in; leave records exist                                 |
| **Test Steps**    | 1. Navigate to **Leave → Leave List** <br> 2. Enter an employee name in the search field <br> 3. Click **Search** |
| **Expected Result** | Filtered leave records for that employee are displayed                |
| **Actual Result**   | Correct records displayed                                             |
| **Status**        | ✅ Pass                                                                  |
| **Remarks**       | —                                                                       |

---

## Test Cases Summary — Leave Management Module

| Test Case ID | Title                                            | Status  |
|--------------|--------------------------------------------------|---------|
| TC-LVE-001   | Apply leave with valid data                      | ✅ Pass  |
| TC-LVE-002   | Apply leave with past date                       | ❌ Fail  |
| TC-LVE-003   | End date before start date                       | ✅ Pass  |
| TC-LVE-004   | View leave balance                               | ❌ Fail  |
| TC-LVE-005   | Apply without leave type                         | ✅ Pass  |
| TC-LVE-006   | Cancel pending leave                             | ✅ Pass  |
| TC-LVE-007   | Admin approves leave                             | ✅ Pass  |
| TC-LVE-008   | Admin rejects leave                              | ✅ Pass  |
| TC-LVE-009   | Apply leave on weekend                           | ✅ Pass  |
| TC-LVE-010   | Search leave by employee name                    | ✅ Pass  |

**Pass: 8 | Fail: 2 | Pass Rate: 80%**
