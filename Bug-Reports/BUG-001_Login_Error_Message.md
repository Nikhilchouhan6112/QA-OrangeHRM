# Bug Report — BUG-001

---

## Bug Summary

| Field              | Details                                                    |
|--------------------|------------------------------------------------------------|
| **Bug ID**         | BUG-001                                                    |
| **Title**          | Misleading error message on login with locked/invalid user |
| **Module**         | Login / Authentication                                     |
| **Reported By**    | QA Intern                                                  |
| **Date Reported**  | April 6, 2026                                              |
| **Severity**       | Major                                                      |
| **Priority**       | High                                                       |
| **Status**         | Open                                                       |
| **Test Case Ref**  | TC-LOG-002, TC-LOG-003                                     |
| **Environment**    | Chrome (Latest), Windows 11, OrangeHRM Demo                |
| **Build/Version**  | OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/)|

---

## Description

When a user attempts to log in with an **invalid username** or **incorrect password**, the system displays the same generic error message:

> *"Invalid credentials"*

However, the message does not distinguish between:
- A completely invalid/non-existent username
- A correct username but wrong password

This generic messaging, while secure by design, becomes **misleading** in a shared/demo environment where testers expect some contextual feedback. More critically, no account lockout mechanism is triggered after multiple failed attempts — a security concern.

---

## Steps to Reproduce

1. Open the application: https://opensource-demo.orangehrmlive.com/
2. Enter username: `Admin`
3. Enter password: `wrongpassword123`
4. Click the **Login** button
5. Observe the error message
6. Repeat steps 2–4 **5+ times consecutively**

---

## Expected Result

- Clear error message guiding the user on the type of error
- After multiple failed attempts (e.g., 5), the account should be **temporarily locked** and a message like *"Account locked. Please contact your administrator."* should appear

---

## Actual Result

- The same *"Invalid credentials"* message is shown after every attempt
- **No lockout** occurs after multiple failed login attempts — the login form remains accessible indefinitely

---

## Impact

- Security vulnerability: Brute-force attacks are possible since there is no lockout mechanism
- Poor user guidance due to non-specific error messages

---


## Additional Notes

This bug affects the security posture of the application. For a production system, account lockout after N failed attempts is a standard security requirement (OWASP recommendation).
