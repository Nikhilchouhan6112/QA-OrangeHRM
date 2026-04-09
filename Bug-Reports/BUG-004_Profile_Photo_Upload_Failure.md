# Bug Report — BUG-004

---

## Bug Summary

| Field              | Details                                                       |
|--------------------|---------------------------------------------------------------|
| **Bug ID**         | BUG-004                                                       |
| **Title**          | Employee profile photo upload fails intermittently            |
| **Module**         | Employee Management (PIM)                                     |
| **Reported By**    | QA Intern                                                     |
| **Date Reported**  | April 7, 2026                                                 |
| **Severity**       | Minor                                                         |
| **Priority**       | Medium                                                        |
| **Status**         | Open                                                          |
| **Test Case Ref**  | TC-EMP-008                                                    |
| **Environment**    | Chrome (Latest), Windows 11, OrangeHRM Demo                   |
| **Build/Version**  | OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/)   |

---

## Description

When attempting to upload a profile photo for an employee, the image upload is **intermittent** — sometimes the photo saves correctly and is displayed on the profile, but other times clicking **Save** results in the default avatar being shown again, with no error message displayed.

There is no feedback to the user indicating whether the upload succeeded or failed silently.

---

## Steps to Reproduce

1. Log in as **Admin**
2. Navigate to **PIM → Employee List**
3. Click on any existing employee name
4. On the employee's profile page, click the **profile photo/avatar area**
5. Select a valid `.jpg` file under 1MB from your system
6. Click **Save**
7. Navigate away from the page and return to the employee's profile
8. Observe whether the photo is displayed

---

## Expected Result

- The uploaded photo should persist and display on the employee profile after saving
- A success/failure notification should appear immediately after clicking Save

---

## Actual Result

- The photo uploads and appears to be saved (success toast sometimes shown)
- After navigating away and returning, the default avatar is displayed instead of the uploaded photo
- No error message is displayed when the upload silently fails

---

## Frequency

- Reproducible approximately **3 out of 5 times** (60% failure rate)
- Behavior appears non-deterministic — likely a server-side issue

---

## Impact

- Poor user experience — no feedback on save failure
- HR records may be incomplete with missing employee photos
- Lack of error messaging leaves users confused

---


## Additional Notes

- Tested with multiple image files (JPG, PNG) under 1MB — issue persists
- Issue may be related to the shared nature of the demo server (file storage limits or concurrent users)
- Suggested fix: Add explicit success/failure toast notification; verify server-side file persistence logic
