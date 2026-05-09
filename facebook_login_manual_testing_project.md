# Facebook Login Functionality — Manual Testing Project

> Ready-to-upload GitHub project. Includes: Test Plan, Test Scenarios, Detailed Test Cases, Test Data, Bug Report template, Traceability Matrix, Test Execution Report, and README with upload instructions.

---

## Repository Structure (suggested)

```
facebook-login-manual-testing/
├─ README.md
├─ TestPlan.md
├─ TestScenarios.md
├─ TestCases.csv
├─ TestData.csv
├─ TraceabilityMatrix.md
├─ BugReport_Template.md
├─ TestExecutionReport.md
├─ Checklist.md
└─ LICENSE.md
```

---

## README

**Project:** Facebook Login Functionality — Manual Testing

**Purpose:** Provide a complete manual test deliverable pack for Facebook login functionality so it can be uploaded directly to GitHub and used by testers.

**Contents:** Test plan, scenarios, cases, test data, templates, and guidance to run manual tests.

**How to use:** Clone repository → review `TestPlan.md` → run test cases from `TestCases.csv` → file bugs using `BugReport_Template.md` → update `TestExecutionReport.md`.

---

## Test Plan (Summary)

**Scope:** Login page of Facebook (https://www.facebook.com) — valid/invalid authentication flows, UI elements, security & input validation, password recovery link, account lock behavior, Remember Me functionality, accessibility checks, and error messages.

**Out of Scope:** Signup/registration flow, posting, profile, and third-party integrations beyond authentication (unless required by an SSO test case).

**Test Types:** Functional, Negative, Usability, Security (basic), Localization (if applicable), Compatibility (browser), Accessibility.

**Environment:**
- OS: Windows 10/11, macOS, Android (emulator), iOS (simulator)
- Browsers: Chrome (latest), Firefox (latest), Edge (latest), Safari (latest)
- Network: Normal, Slow (simulated), Offline

**Roles & Responsibilities:**
- Test Lead: coordinates test execution
- Manual Tester: executes cases and logs defects
- Reviewer: verifies test artifacts and closure

**Entry Criteria:** Test environment available, test data prepared, test artifacts reviewed.

**Exit Criteria:** All critical defects fixed & retested, test execution completed for planned cases, test summary prepared.

---

## Test Scenarios (high-level)

1. Navigate to login page
2. Login with valid email/phone and valid password
3. Login with valid email/phone and invalid password
4. Login with invalid email/phone
5. Empty email/phone or password fields
6. Password visibility toggle (show/hide)
7. Remember Me / Keep me logged in behavior
8. Forgot Password link flow
9. Account locked after multiple failed attempts
10. Input validation (special chars, SQL injection attempts)
11. Two-factor / security checkpoint flows (if triggered)
12. UI responsiveness on different screen sizes
13. Accessibility: keyboard navigation, label association
14. Error messages content and localization
15. Login using phone number (format variations)

---

## Detailed Test Cases (CSV-ready)

Below is a sample set of test cases. Save as `TestCases.csv` (comma-separated). Column headers: `TC_ID,Title,Preconditions,Steps,Test Data,Expected Result,Priority,Status,Comments`.

```
TC001,Open Login Page,None,1. Open browser 2. Navigate to https://www.facebook.com,,Login page loads with Email/Phone and Password fields visible,High,Not Executed,

TC002,Valid Login with Email,Test account exists,1. Enter valid email 2. Enter valid password 3. Click Log In,user: test.user@example.com | pass: ValidPass123,User should be logged in and redirected to home/feed,High,Not Executed,

TC003,Valid Login with Phone,Test account uses phone,1. Enter valid phone 2. Enter valid password 3. Click Log In,user: +919876543210 | pass: ValidPass123,User should be logged in and redirected to home/feed,High,Not Executed,

TC004,Invalid Password,Account exists,1. Enter valid email 2. Enter wrong password 3. Click Log In,user: test.user@example.com | pass: WrongPass,Login fails with appropriate error message (e.g., "The password you’ve entered is incorrect"),High,Not Executed,

TC005,Empty Fields,None,1. Leave both fields empty 2. Click Log In,,Validation should prevent login and show error messages or highlights,Medium,Not Executed,

TC006,Empty Email,Password filled,1. Leave email empty 2. Enter password 3. Click Log In,password: ValidPass123,Validation message for email required,Medium,Not Executed,

TC007,Empty Password,Email filled,1. Enter email 2. Leave password empty 3. Click Log In,email: test.user@example.com,Validation message for password required,Medium,Not Executed,

TC008,Password Visibility Toggle,None,1. Enter password 2. Click show/hide icon,,Password characters toggle between masked and visible,Low,Not Executed,

TC009,Remember Me Functionality,None,1. Check Keep me logged in 2. Login successfully 3. Close browser 4. Reopen browser and navigate to FB,,User remains logged in (or cookie behavior matches product requirement),Medium,Not Executed,

TC010,Forgot Password Link,None,1. Click Forgot Password 2. Follow recovery steps,,Password reset flow opens and allows account recovery,High,Not Executed,

TC011,SQL Injection Attempt,None,1. Put "' OR '1'='1" in email field 2. Put random password 3. Click Log In,,Application must NOT allow injection; sanitized input and error,High,Not Executed,

TC012,Account Lockout after Multiple Failures,Account exists,1. Enter correct email 2. Enter wrong password repeatedly (e.g., 10 times) 3. Observe behavior,,Account temporarily locked or CAPTCHA appears as per product policy,High,Not Executed,

TC013,Login with Long Input,None,1. Enter 500+ characters in email field 2. Click Log In,,Input validation or max-length enforcement and graceful error,Low,Not Executed,

TC014,Localization of Error Messages,Locale set to other language,1. Trigger error (wrong password) 2. Observe message,,Error message displays in selected locale where supported,Low,Not Executed,

TC015,Accessibility: Keyboard Navigation,None,1. Use Tab to focus inputs 2. Use Enter to submit,,All interactive elements reachable by keyboard and ARIA-labels present,Low,Not Executed,
```

> Add or edit test cases according to the product requirement or latest Facebook UI changes.

---

## Test Data (sample) — Save as `TestData.csv`

```
ID,Type,Value,Notes
TD001,ValidEmail,test.user@example.com,Use a real or sandbox account owned by test team
TD002,ValidPhone,+919876543210,Use test phone or virtual number where allowed
TD003,ValidPassword,ValidPass123,
TD004,InvalidPassword,WrongPass,
TD005,SQLInjection,' OR '1'='1",
TD006,LongString,aaaaaaaa...(500 chars),
```

> Do not commit real personal credentials to public repos. Replace sensitive data with placeholders or use environment variables / secrets.

---

## Traceability Matrix (brief)

```
Requirement_ID,Requirement_Description,Linked_TestCases
R1,Page loads with login form,TC001
R2,Normal login works,TC002,TC003
R3,Input validation,TC005,TC006,TC007,TC013
R4,Security - injection protection,TC011
R5,Password recovery,TC010
R6,Account lockout/CAPTCHA,TC012
```

---

## Bug Report Template (`BugReport_Template.md`)

**Project:** Facebook Login Functionality

- **Bug ID:** AUTO or BR-001
- **Title:** Short descriptive title
- **Reported By:** Tester name
- **Date:** YYYY-MM-DD
- **Environment:** OS / Browser / Device
- **Preconditions:** e.g., Test account exists
- **Steps to Reproduce:** 1. ... 2. ...
- **Test Data:** email / phone / password used
- **Actual Result:** What happened
- **Expected Result:** What should happen
- **Severity:** Blocker / Critical / Major / Minor / Trivial
- **Priority:** P0 / P1 / P2
- **Attachments:** Screenshots, logs
- **Status:** New / Open / Fixed / Closed
- **Comments:** Additional notes

---

## Test Execution Report (sample) — `TestExecutionReport.md`

**Test Cycle:** Login_Functionality_Sanity

**Period:** YYYY-MM-DD to YYYY-MM-DD

**Environment:** Browsers and OS used

**Total Test Cases:** 15

**Executed:** X

**Pass:** Y

**Fail:** Z

**Blocked:** A

**Defects Raised:** N (list bug IDs)

**Summary:** Short summary of execution, key findings, and recommendation.

---

## Checklist (`Checklist.md`)

- [ ] Test environment ready
- [ ] Test data prepared (no real credentials committed)
- [ ] Test cases reviewed and approved
- [ ] Regression cases selected
- [ ] Accessibility checks included
- [ ] Defects logged in bug tracker

---

## Security & Privacy Note

**DO NOT** commit real user credentials, PII, or secret tokens to a public GitHub repository. Use placeholders (e.g., `TEST_USER_EMAIL`) and provide instructions to maintainers for how to configure private test accounts or CI secrets.

Example guidance for repository maintainers (include in README):

```
1. Create a private file `secrets.example` containing placeholders.
2. Add `secrets.example` to repo and add `secrets` to .gitignore.
3. Store real credentials in your CI secret store or private vault.
```

---

## How to upload to GitHub (quick steps)

1. Create a new repository on GitHub named `facebook-login-manual-testing`.
2. Clone it locally:
   ```bash
   git clone https://github.com/<your-username>/facebook-login-manual-testing.git
   cd facebook-login-manual-testing
   ```
3. Copy the files into the folder (or create the files from the markdown content in this project).
4. Initialize and push:
   ```bash
   git add .
   git commit -m "Add manual testing artifacts for Facebook login functionality"
   git push origin main
   ```

---

## License

This project is provided under the MIT License. Create a `LICENSE.md` with the MIT text or choose your preferred license.

---

## Next steps / Customization suggestions

- Add more test cases for multi-factor authentication flows or CAPTCHAs if your test accounts trigger them.
- Add browser compatibility matrix and results for each browser/version.
- Convert `TestCases.csv` to a XLSX or test management system import format if you use one (TestRail, Zephyr).
- Add sample screenshots (in `assets/screenshots/`) after executing tests — keep them non-sensitive.

---

*Prepared for quick upload to GitHub. Edit any placeholder values and remove this note before publishing.*

