Use Case: Analyze Survey Feedback
=================================
**Primary Actor**: Instructor  

**Scope**: Software system  

**Purpose**: Enable instructors to aggregate and visualize students’ survey responses to gain actionable insights.  

**Type**: Primary  

**Preconditions**:
- The instructor is logged into the system.
- At least one survey has been completed by students.
- The instructor has permission to analyze results for the selected survey.

**Postconditions**:
- Aggregated statistics and charts are generated and displayed.
- Any filters or date ranges applied are saved for the instructor’s next session (optional).
- The system logs the analysis action for auditing.

**Overview**:  
The instructor navigates to the “Survey Analysis” section from their dashboard. They select a survey from a list of completed surveys. The system calculates key metrics (e.g., average ratings, distribution of answers, response rates) and renders interactive charts (bar charts, pie charts, trend lines). The instructor can apply filters (by date range, question type, or student cohort), drill down into individual questions, and export the results (PDF, CSV, or image).  

Typical Course of Events:
-------------------------

| Actor Action                                                           | System Response                                                                                                 |
|:------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------|
| 1. The Instructor selects “Survey Analysis” from the dashboard.         | 2. The system displays a list of surveys with completion counts and response rates.                             |
| 3. The Instructor chooses “Midterm Course Survey – Spring 2025.”       | 4. The system computes aggregates (averages, distributions) and displays summary statistics and charts.        |
| 5. The Instructor applies a filter (e.g., date range May 1–May 31).     | 6. The system updates the charts and tables to reflect only responses submitted within the selected range.     |
| 7. The Instructor clicks on a chart element (e.g., rating “4 stars”).   | 8. The system drills down to show the list of student comments or detailed responses contributing to that data point. |
| 9. The Instructor clicks “Export Report.”                               | 10. The system generates a PDF (or CSV) containing the charts and underlying data, then prompts for download.   |

Alternative Courses:
--------------------
1a. **No responses available**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system displays “No feedback responses yet” and suggests returning later.  

5a. **Filter yields no data**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system shows “No responses match the selected criteria” and offers to clear filters.  

7a. **Drill-down permission denied**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system displays “Access Denied” for detailed view and logs the attempt.  

Section: Generating and Exporting Statistics
--------------------------------------------
| Actor Action                                  | System Response                                                                                         |
|:----------------------------------------------|:--------------------------------------------------------------------------------------------------------|
| 1. The Instructor selects “Generate Statistics.” | 2. The system calculates key metrics (mean, median, mode, response rate) and updates the dashboard.     |
| 3. The Instructor chooses “Download CSV.”      | 4. The system packages the raw aggregated data into a CSV and initiates the download.                  |

Security and Privacy Considerations:
-----------------------------------
- Only instructors with appropriate roles may access analytical tools for their own surveys.  
- Aggregated data is anonymized by default; identifying information is only available if explicitly permitted.  
- All data in transit and at rest is encrypted to ensure confidentiality.  
- Analysis and export actions are logged (actor ID, timestamp, survey ID) for audit trails.  
- Retention and archival policies apply to exported reports to comply with data protection regulations.  

<!-- PlantUML diagram  -->

@startuml AnalyzeSurveyFeedback
' Use Case: Analyze Survey Feedback
' Actor: Instructor
' Purpose: Aggregate & visualize survey results
left to right direction
skinparam packageStyle rectangle

actor Instructor

rectangle "Survey Analysis Module" {
  
  usecase "Select Survey" as UC_Select
  usecase "Compute Aggregates" as UC_Aggregate
  usecase "Display Charts & Stats" as UC_Display
  usecase "Apply Filters" as UC_Filter
  usecase "Drill-Down Details" as UC_Drill
  usecase "Export Analysis Report" as UC_Export

  UC_Aggregate .> UC_Select : <<include>>
  UC_Display .> UC_Aggregate : <<include>>
  UC_Filter .> UC_Display  : <<extend>>
  UC_Drill .> UC_Display   : <<extend>>
  UC_Export .> UC_Display  : <<include>>
}

Instructor --> UC_Select
Instructor --> UC_Filter
Instructor --> UC_Drill
Instructor --> UC_Export

note right of UC_Display
  • Bar, pie, line charts  
  • Summary tables  
end note

note left of UC_Export
  • PDF/CSV output  
  • Includes charts & raw data  
end note

@enduml
