# Bug Report — BUG-002

---

## Bug Summary

| Field              | Details                                                       |
|--------------------|---------------------------------------------------------------|
| **Bug ID**         | BUG-002                                                       |
| **Title**          | No input validation on Employee First Name field (accepts numbers & special characters) |
| **Module**         | Employee Management (PIM)                                     |
| **Reported By**    | QA Intern                                                     |
| **Date Reported**  | April 6, 2026                                                 |
| **Severity**       | Major                                                         |
| **Priority**       | High                                                          |
| **Status**         | Open                                                          |
| **Test Case Ref**  | TC-EMP-010                                                    |
| **Environment**    | Chrome (Latest), Windows 11, OrangeHRM Demo                   |
| **Build/Version**  | OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/)   |

---

## Description

The **First Name** and **Last Name** fields in the **Add Employee** form do not validate that the input contains only alphabetical characters. A user can enter **numbers, special characters, or symbols** as an employee name, and the system will save the record without any warning or error.

This is a **data integrity** issue — employee names in an HR system should only consist of valid alphabetic characters.

---

## Steps to Reproduce

1. Log in to OrangeHRM with Admin credentials
2. Navigate to **PIM → Add Employee**
3. In the **First Name** field, type: `1234!@#`
4. In the **Last Name** field, type: `Test`
5. Click the **Save** button
6. Observe the result

---

## Expected Result

- System should display a validation error:
  > *"Employee name should only contain alphabetic characters"*
- Record should **NOT** be saved

---

## Actual Result

- No validation error is displayed
- The employee record is **saved successfully** with the invalid name `1234!@# Test`
- The invalid name appears in the Employee List

---

## Impact

- Data integrity issue: HR database can contain invalid/garbage employee records
- May cause issues with payroll, reports, or system integrations that expect valid name formats
- Poses risk of XSS or injection if special characters aren't sanitized server-side

---


## Additional Notes

This validation should be implemented at both the **frontend** (real-time) and **backend** (on submit) levels. Suggested regex pattern: `^[A-Za-z\s\-']+$`
