## Sample Defect Report

**Title:** Clicking expired email verification link redirects to blank white screen instead of showing proper message  
**Status:** New  
**Reported By:** Aarya Rajbhandari  
**Date:** 24 March 2026  
**Assignee:** Unassigned  

**Label:** Bug, Signup, Email Verification, Priority: High  

---

### Environment
- **Version:** v.1.4.5  
- **Environment:** Production  
- **Module:** Signup - Email Verification  
- **User Role:** New User  

---

### Severity
Medium  

### Priority
High  

---

### Related Test Case
- TC15_Signup_ExpiredVerificationEmail // Find this test case in Test-Cases/Figma/Sample Test Case - Figma(Signup_Login).xls

---

### Description
When a user clicks on an expired email verification link, the system redirects to a blank white screen instead of showing "Email Verification Link Expired" with a button to resend the verification email.

---

### Pre-condition

- Complete Signup with email
- Verification link should expire

---

### Steps to Reproduce
1. Open the email used for signing up
2. Click on the expired verification link in the email  

---

### Actual Result
User is redirected to a blank white screen with no message.  

---

### Expected Result
User should be redirected to a page with the title "Email Verification Link Expired" with provide a button to resend the verification email. 

---

### Attachments

Design_Screenshot_Expired_Verification.png  
DEF 1: TC12_Signup_OnlySpacesInPassword[Signup allows password with only spaces].png

---
