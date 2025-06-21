Use Case: Analyze System
=================================
**Primary Actor**: Administrator  

**Scope**: Software system  

**Purpose**: Generate comprehensive reports on survey creation, user participation, system usage trends, and performance metrics to support continuous improvement.  

**Type**: Primary  

**Preconditions**:
- The administrator is logged into the system with reporting privileges.
- The system has collected data on surveys, responses, user logins, and key performance indicators.
- Reporting module is configured and accessible.

**Postconditions**:
- A report is generated, displayed, and optionally exported.
- The system logs the report generation event (actor ID, timestamp, report parameters).
- Generated reports may be scheduled for future automatic delivery.

**Overview**:  
The administrator navigates to the “System Analytics” section. They select report types—such as “Survey Creation Trends,” “Response Rates,” “User Activity,” or “Performance Metrics.” The system aggregates relevant data over selectable time frames and presents interactive dashboards with tables, charts (e.g., line graphs for trends, bar charts for counts, heat maps for usage peaks), and summary statistics. The administrator can drill down into specific metrics, apply filters (date ranges, user roles, survey types), and export the full report in PDF, CSV, or Excel formats. Reports can also be scheduled to run automatically at regular intervals and emailed to designated recipients.

Typical Course of Events:
-------------------------

| Actor Action                                                               | System Response                                                                                                          |
|:-----------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------|
| 1. The Administrator selects “System Analytics” from the dashboard.         | 2. The system displays available report categories and recent report history.                                           |
| 3. The Administrator chooses “User Participation Report.”                   | 4. The system prompts for time frame (e.g., last 30 days) and optional filters (roles, survey type).                    |
| 5. The Administrator clicks “Generate Report.”                              | 6. The system aggregates data, builds charts and tables, and displays the interactive report dashboard.                  |
| 7. The Administrator drills down into “Daily Active Users” chart.           | 8. The system shows a detailed table of daily user counts and highlights peak usage days.                               |
| 9. The Administrator clicks “Export PDF.”                                   | 10. The system compiles the dashboard into a PDF document and prompts for download or schedules delivery.                |

Alternative Courses:
--------------------
1a. **Insufficient Data**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system detects < minimum data threshold > is not met and displays “Not enough data to generate this report,” suggesting alternative time frames.  

5a. **Invalid Filter Selection**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system highlights incorrect filter parameters (e.g., future date range) and prevents report generation until corrected.  

9a. **Export Failure**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system logs the error, notifies the administrator of the failure, and retries export or provides a download link.

Section: Scheduling Reports
----------------------------
| Actor Action                                         | System Response                                                                                                         |
|:-----------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| 1. The Administrator clicks “Schedule Report.”       | 2. The system presents options for frequency (daily, weekly, monthly), time, and recipient list.                         |
| 3. The Administrator configures schedule and saves.  | 4. The system validates settings, registers the scheduled job, and confirms setup with a success message.               |

Security and Privacy Considerations:
-----------------------------------
- Only administrators with “Analytics” role may access reporting dashboards and exports.  
- Sensitive data in reports is anonymized or pseudonymized by default; detailed user identifiers require explicit permission.  
- All report generation and export actions occur over encrypted channels; exported files are protected (e.g., password-protected PDFs).  
- Audit logs capture report type, parameters, actor ID, and timestamps for compliance oversight.  
- Data retention policies govern the archival or purge of old report data in accordance with institutional and regulatory requirements.  

<!-- PlantUML diagram  -->
@startuml AnalyzeSystem
' Use Case: Analyze System
' Actor: Administrator
' Purpose: Generate usage & performance reports
left to right direction
skinparam packageStyle rectangle

actor Administrator

rectangle "System Analytics Module" {
  
  usecase "Select Report Type" as UC_Select
  usecase "Configure Parameters" as UC_Configure
  usecase "Generate Report" as UC_Generate
  usecase "View Dashboard" as UC_Dashboard
  usecase "Schedule Reports" as UC_Schedule
  usecase "Export Report" as UC_Export

  UC_Configure .> UC_Select   : <<include>>
  UC_Generate  .> UC_Configure: <<include>>
  UC_Dashboard .> UC_Generate : <<include>>
  UC_Export    .> UC_Dashboard: <<include>>
  UC_Schedule  .> UC_Generate : <<extend>>
}

Administrator --> UC_Select
Administrator --> UC_Schedule
Administrator --> UC_Export

note right of UC_Dashboard
  • Interactive charts & tables  
  • Trend lines, heat maps  
end note

note left of UC_Schedule
  • Frequency: daily/weekly/etc.  
  • Recipient list & time  
end note

@enduml
