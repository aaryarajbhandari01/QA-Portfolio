### Sample Defect Report

**Title:** Signup allows a password with only spaces instead of showing a validation error  
**Status:** New  
**Reported By:** Aarya Rajbhandari  
**Date:** 24 March 2026 

**Assignee:** Unassigned  

**Label:** Bug, Signup, High 

---

## Environment
- **Platform:** Web and Mobile
- **Version:** Latest  
- **Environment:** Test  
- **Module:** Signup  
- **User Role:** New User  

---

## Severity
High  

## Priority
High  

---

## Related Test Case

- TC12_Signup_OnlySpacesInPassword // Find this test case in Test-Cases/Figma/Sample Test Case - Figma(Signup_Login).xls 
---

## Description
When a user attempts to sign up using a password that contains only whitespace characters (7 blank spaces), the system does not validate the input correctly and allows the user to sign up successfully.

---

## Steps to Reproduce
1. Navigate to "https://www.figma.com"  
2. Click on "Get started"  
3. Enter a valid email address  
4. Enter 7 blank spaces ("       ") in the password field  
5. Click "Continue with email"  

---

## Actual Result
"Password should contain atleast one special character and number" error message was not displayed, and the user is able to sign up using the password with only seven white spaces.
The user also receives a verification email. 

---

## Expected Result
"Password should contain atleast one special character and number" error message should be displayed when entering passwords containing only whitespaces, and verification email should not be sent.

---

## Attachments

DEF 1: TC12_Signup_OnlySpacesInPassword[Signup allows password with only spaces].png 

---
