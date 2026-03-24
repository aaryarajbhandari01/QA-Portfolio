# Figma - Sample Test Case

This module includes manual test cases designed for:
- Figma's Login/Signin functionality
- Input validation
- Error handling
- Equivalence Partitioning  
- Boundary Value Analysis  
- Negative Testing  
- Positive Testing  
- Authentication
- Security (SQL Injection, XSS)

Files:
- Figma-Login-TestCases.xlsx
- Figma-Signup-TestCases.xlsx

# Test Suite: Login

## Test Case Summary

| TC ID | Scenario | Type | Priority |
|------|--------|------|----------|
| TC01 | Navigate via URL | Functional | High |
| TC02 | Navigate via Navbar | Functional | High |
| TC03 | Valid Login | Functional | High |
| TC04 | Email with Leading Space | Functional | High |
| TC05 | Email with Trailing Space | Functional | High |
| TC06 | Empty Email | Functional | High |
| TC07 | Empty Password | Functional | High |
| TC08 | Invalid Email | Functional | High |
| TC09 | Invalid Password | Functional | High |
| TC10 | Login via Google | Functional | High |
| TC11 | Cancel Google Login | Functional | High |
| TC12 | SQL Injection | Security | High |
| TC13 | XSS Attack | Security | High |
| TC14 | Back Button After Logout | Security | High |
| TC15 | Multiple Login Sessions | Security | Medium |

---
# Test Suite: Signup

## Test Case Summary

| TC ID | Scenario | Type | Priority |
|------|--------|------|----------|
| TC01 | Navigate to Signup | Functional | High |
| TC02 | Signup via Google | Functional | High |
| TC03 | Restore Deleted Account | Functional | High |
| TC04 | Deny Google Permission | Functional | High |
| TC05 | Cancel Google Signup | Functional | High |
| TC06 | Empty Email | Functional | High |
| TC07 | Invalid Email | Functional | High |
| TC08 | Empty Password | Functional | High |
| TC09 | Short Password | Functional | High |
| TC10 | Missing Special Character | Functional | High |
| TC11 | Missing Number | Functional | High |
| TC12 | Only Spaces Password | Functional | High |
| TC13 | Email Notification | Functional | High |
| TC14 | Verified Email | Functional | High |
| TC15 | Expired Verification Link | Functional | High |
| TC16 | Duplicate Email | Functional | High |

---
# Future Improvements

- Add Automation (Selenium / Playwright)  
- Link test cases with bug reports  
- Convert into TestRail / Jira format  
---
