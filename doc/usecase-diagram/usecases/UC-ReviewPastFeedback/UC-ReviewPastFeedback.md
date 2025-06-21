Use Case: Review Past Feedback
=================================
**Primary Actors**: Instructor, Student  
**Secondary Actor**: Administrator  

**Scope**: Software system  

**Purpose**: Allow users (students, instructors, administrators) to view the history of feedback submissions.

**Type**: Primary  

**Preconditions**:
- The user is logged into the system.
- At least one completed survey exists in the system.
- The user has permission to view the requested feedback (students see only their own; instructors see responses for surveys they created; administrators can view all).

**Postconditions**:
- The selected historical feedback is displayed to the user.
- The system logs the “view history” action for auditing.
- Any filters or search parameters used are saved for the user’s next session (optional).

**Overview**:  
Users navigate to the “Feedback History” area from their dashboard.  
- Students see a list of surveys they have completed, with date, title, and status.  
- Instructors see a list of surveys they authored, with counts of responses, date ranges, and links to individual student submissions or aggregated views.  
- Administrators access across all surveys and users.  

From the list, the actor can:  
1. Click a survey to view individual response details (each question and answer).  
2. Apply filters (by date range, survey title, student name for instructors/administrators).  
3. Export selected responses (CSV or PDF).  
4. Return to dashboard or switch view (e.g., aggregated statistics vs. raw responses).

Typical Course of Events:
-------------------------

| Actor Action                                                             | System Response                                                                                                            |
|:-------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| 1. The Actor selects “Feedback History” from the main menu/dashboard.   | 2. The system retrieves and displays the list of relevant completed surveys for that actor (with pagination if needed).   |
| 3. The Actor filters by survey title “Semester 1 Course Feedback.”      | 4. The system applies the filter and updates the list to show matching entries.                                            |
| 5. The Actor selects one entry (e.g., “Course ABC – June 2025”).        | 6. The system displays detailed responses: question text, student answer, date submitted.                                  |
| 7. The Actor clicks “Export CSV” (optional).                            | 8. The system generates and prompts download of a CSV file containing the displayed feedback data.                        |

Alternative Courses:
--------------------
1a. **No completed surveys found**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system displays a “No feedback found” message and suggests returning later or contacting the administrator.

3a. **Filter yields no results**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system shows “No matching feedback” and offers to clear filters.

5a. **Actor lacks permission for a detailed view**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system displays an “Access Denied” message and logs the attempt.

Section: Filtering and Exporting Feedback
-----------------------------------------
| Actor Action                                   | System Response                                                                                     |
|:-----------------------------------------------|:----------------------------------------------------------------------------------------------------|
| 1. The Actor enters a date range (e.g., May–June 2025). | 2. The system updates the list to include only surveys submitted within that period.                 |
| 3. The Actor selects “Download PDF Report.”    | 4. The system compiles a PDF with aggregated statistics and individual responses, then starts download. |

Security and Privacy Considerations:
-----------------------------------
- Only authorized actors can view or export feedback; role-based access control is enforced at every retrieval endpoint.  
- Student data is anonymized in aggregated exports unless the actor has explicit rights to identify (e.g., instructors for their own courses).  
- All views and exports are over HTTPS to ensure data in transit is encrypted.  
- Viewing and export actions are logged with timestamp, actor ID, and accessed survey ID for audit trails.  
- Retention policies apply: feedback older than the configured retention period is archived or purged according to data protection regulations.  

<!-- PlantUML diagram -->
@startuml ReviewPastFeedback
' Use Case: Review Past Feedback
' Actors: Student, Instructor, Administrator
' Purpose: Let actors view history of submitted feedback
left to right direction
skinparam packageStyle rectangle

actor Student
actor Instructor
actor Administrator

rectangle "Feedback History Module" {
  
  usecase "Authenticate User" as UC_Auth
  usecase "List Completed Surveys" as UC_List
  usecase "Filter/Search History" as UC_Filter
  usecase "View Response Details" as UC_Details
  usecase "Export Feedback" as UC_Export

  UC_List .> UC_Auth : <<include>>
  UC_Filter .> UC_List : <<include>>
  UC_Details .> UC_List : <<include>>
  UC_Export .> UC_Details : <<include>>
}

Student      --> UC_Auth
Instructor   --> UC_Auth
Administrator --> UC_Auth

UC_Auth      --> UC_List
Student      --> UC_List
Instructor   --> UC_List
Administrator --> UC_List

Student      --> UC_Filter
Instructor   --> UC_Filter
Administrator --> UC_Filter

Student      --> UC_Details
Instructor   --> UC_Details
Administrator --> UC_Details

Instructor   --> UC_Export
Administrator --> UC_Export

note right of UC_Filter
  • By date range, survey title  
  • Students see only own entries  
end note

note left of UC_Export
  • CSV, PDF formats  
  • Anonymization enforced per role  
end note

@enduml
