## Sample Defect Report

**Title:** Quiz Result page displays "Attempt to read property 'completed_post_survey' on null" error for Theme 4 quiz (Status code 500).  
**Status:** Closed  
**Reported By:** Aarya Rajbhandari  
**Date:** May 6, 2025  
**Assignee:** John Doe

**Label:** Bug, Quiz, Learner, Dev, Backend

---

### Environment
- **Version:** Beta 1.4.5  
- **Environment:** Dev  
- **Module:** Learner Quiz (Theme 4)  
- **User Role:** Learner  

---

### Severity
High  

### Priority
High 

---
### Description
When a learner completes all competencies in Theme 4 and navigates to the result page, the system throws the following error:
"Attempt to read property 'completed_post_survey' on null"

---

### Steps to Reproduce
1. Login as a learner  
2. Navigate to "Theme 4" from the dashboard
3. Complete all competencies quizzes in Theme 4 
4. Click on "View Results" button at the bottom of the competencies list page 

---

### Actual Result
The result page fails to load and "Attempt to read property 'completed_post_survey' on null" error token was displayed. 
Status code 500 for quiz_outcome

---

### Expected Result
Result page should display quiz outcome successfully, and no backend error should be visible to the user.  

---

### Attachments

DEF 101 - Learner- Quiz -> Theme 4 Result - Null Property Error.png 

---




