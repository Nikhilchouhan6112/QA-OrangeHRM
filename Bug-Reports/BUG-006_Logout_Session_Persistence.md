# Bug Report — BUG-006

---

## Bug Summary

| Field              | Details                                                            |
|--------------------|--------------------------------------------------------------------|
| **Bug ID**         | BUG-006                                                            |
| **Title**          | Browser back button allows access to dashboard after logout        |
| **Module**         | Login / Authentication                                             |
| **Reported By**    | QA Intern                                                          |
| **Date Reported**  | April 8, 2026                                                      |
| **Severity**       | Major                                                              |
| **Priority**       | High                                                               |
| **Status**         | Open                                                               |
| **Test Case Ref**  | TC-LOG-010                                                         |
| **Environment**    | Chrome (Latest), Windows 11, OrangeHRM Demo                        |
| **Build/Version**  | OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/)        |

---

## Description

After a user logs out of OrangeHRM, pressing the **browser's Back button** briefly loads the previously visited authenticated page (e.g., Dashboard). Although the system eventually redirects back to the login page after a short delay, there is a **window of time** during which the authenticated content is visible and potentially interactable.

This is a **session management vulnerability** — authenticated pages should be immediately inaccessible upon logout, with no cached version rendered by the browser.

---

## Steps to Reproduce

1. Open: https://opensource-demo.orangehrmlive.com/
2. Log in with valid credentials: `Admin / admin123`
3. Navigate to the **Dashboard** — observe the URL (e.g., `/web/index.php/dashboard/index`)
4. Click on the user avatar (top-right corner)
5. Click **Logout**
6. Confirm you are on the **Login page**
7. Immediately press the **browser Back button** (or `Alt + Left Arrow`)
8. Observe what happens

---

## Expected Result

- The browser should **NOT** display any authenticated content after logout
- User should be immediately redirected to the login page with a message such as:
  > *"Your session has expired. Please log in again."*
- Previously cached pages should not be accessible

---

## Actual Result

- The **Dashboard page loads briefly** after pressing the back button
- Authenticated content (menu items, employee data widgets) is **visible for 1–2 seconds**
- After that, the page redirects to login — but the brief exposure is a security concern

---

## Impact

- **Security Risk:** On a shared computer (e.g., office, library), another person could press Back after the user logs out and briefly view sensitive HR data
- Violates **session invalidation best practices** (OWASP A07: Identification and Authentication Failures)
- In a production HR system, this could expose sensitive employee information

---


## Suggested Fix

- Implement proper **cache-control headers** (`Cache-Control: no-store, no-cache`) on all authenticated pages
- On the server side, **invalidate the session token immediately** upon logout
- Use JavaScript to clear browser history state on logout:
  ```javascript
  history.pushState(null, null, window.location.href);
  window.onpopstate = function() { history.go(1); };
  ```
- Ensure all authenticated routes check session validity on every page load
