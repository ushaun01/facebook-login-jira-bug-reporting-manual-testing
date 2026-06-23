
📋 Project Summary:
 
This repository contains a small manual testing suite for the Facebook login functionality.

The testing includes manual test case documentation, execution results, and defect tracking and bug reporting using Jira

The goal is to validate login behavior for positive and negative scenarios and to record results.

---
📊 Test Execution Summary:

Total Test Cases: 4

Passed: 3

Failed: 1

Blocked / Not Run: 0

---

🧪 Test Execution Summary

| Test Case ID | Description | Expected Result | Actual Result | Status |

| TC_Login001 | Login with valid credentials | Successful Login | Unsuccessful Login | ❌ Fail |

| TC_Login002 | Valid username, invalid password | Error message displayed | As expected | ✅ Pass |

| TC_Login003 | Invalid username, valid password | Error message displayed | As expected | ✅ Pass |

| TC_Login004 | Invalid username and password | Error message displayed | As expected | ✅ Pass |

---
🐞 Defect Logged (Jira)

Issue Title: Login Failed with Valid Credentials

Test Case ID: TC_FB_01

Description:

Click on login

Enter valid email and password

Click on submit

Login failed

Expected Result: Login successful

Actual Result: Login failed

Status: ❌ Failed

Environment: www.demoapp@xyz

---
Suggested next steps:

Check for any error messages on the page.

Reconfirm the test credentials are correct.

Try the same steps in another browser.

---
🧰 Test Artifacts

Test Case Document: Facebook Login Functionality Test Case.xlsx

Bug Report: Jira_Report.png

Test Type: Functional Testing

Testing Approach: Positive and Negative testing

---
📅 Project Timeline

| Activity | Date |

| Test Case Creation | 07-Jul-2025 |

| Test Execution | 13-Jul-2025 |

| Review | 15-Jul-2025 |

| Jira Bug Logged | 16-Jul-2025 |

---
📈 Tools Used

Test Case Management: Excel

Bug Tracking: Jira

Environment: Web Application (Facebook)

Browser Used: Chrome

---

👩‍💻 Author

Name: Usha Umesh Nazare

Role: QA Tester | Manual Testing

Tools: Jira | Excel | Web Testing






Manual Testing of Facebook Login Functionality with documented test cases, execution results, and Jira bug tracking for validating positive and negative scenarios.
