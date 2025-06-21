Use Case: Manage Classes and Instructors
=================================
**Primary Actor**: Administrator  

**Scope**: Software system  

**Purpose**: Enable administrators to create and maintain class schedules, assign instructors to classes, and facilitate communication between instructors and students.  

**Type**: Primary  

**Preconditions**:
- The administrator is logged into the system with the “Admin” role.
- Instructor and class data have been imported or created in the system.
- Course catalog is available and up-to-date.

**Postconditions**:
- Classes have valid schedules with assigned instructors.
- Instructors and enrolled students receive notifications of assignments and schedule changes.
- All changes are logged for auditing.

**Overview**:  
From the Admin Dashboard, the administrator navigates to “Class Management.” They can create new class offerings (linking to courses), define meeting times and locations, and assign one or more instructors. The admin can also modify existing schedules—reschedule sessions, reassign instructors, or cancel classes. Upon any change, the system notifies affected instructors and enrolled students via email and in-app alerts. The administrator can view a calendar or list view of all classes, filter by date, instructor, or course, and export schedules (PDF/CSV).

Typical Course of Events:
-------------------------

| Actor Action                                                                 | System Response                                                                                                        |
|:-----------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|
| 1. The Administrator selects “Class Management” from the dashboard.          | 2. The system displays a calendar and list view of existing classes with filters for date, course, and instructor.    |
| 3. The Administrator clicks “Create New Class.”                              | 4. The system presents a form to select course, define schedule (dates/times), location, and choose instructor(s).    |
| 5. The Administrator fills in the details and clicks “Save.”                 | 6. The system validates inputs, creates the class record, and assigns the instructor(s).                              |
| 7. The system triggers notifications to assigned instructor(s) and students enrolled in the course.            |
| 8. The system logs the creation event with timestamp, admin ID, and class ID. |

Alternative Courses:
--------------------
1a. **Invalid Schedule Conflict**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system detects that the chosen time/location conflicts with another class, displays an error, and suggests alternate slots.  

5a. **Instructor Unavailable**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system warns that the instructor has another assignment at that time and prompts the admin to choose a different instructor or time.  

7a. **Notification Failure**  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system logs the failed delivery and retries; if still unsuccessful, alerts the administrator of undelivered notices.

Section: Editing and Cancelling Classes
---------------------------------------
| Actor Action                                     | System Response                                                                                  |
|:-------------------------------------------------|:-------------------------------------------------------------------------------------------------|
| 1. The Administrator selects an existing class.   | 2. The system loads current details into an editable form.                                       |
| 3. The Administrator updates schedule or instructor. | 4. The system validates changes, updates the class record, sends update notifications, and logs the event. |
| 5. The Administrator clicks “Cancel Class.”       | 6. The system marks the class as canceled, notifies instructor(s) and students, and logs the cancellation.   |

Security and Privacy Considerations:
-----------------------------------
- Only users with the “Administrator” role may create, edit, or cancel classes.  
- All schedule changes are transmitted over HTTPS and stored in an encrypted database.  
- Notification messages omit sensitive personal data; they include only relevant class details.  
- Every modification is logged (actor ID, timestamp, changed fields) for full auditability.  
- Retention policies govern archival of past class schedules according to institutional regulations.  

<!-- PlantUML diagram  -->
@startuml ManageClassesInstructors
' Use Case: Manage Classes and Instructors
' Actor: Administrator
' Purpose: Create schedules & assign instructors
left to right direction
skinparam packageStyle rectangle

actor Administrator

rectangle "Class Management Module" {
  
  usecase "Create Class Offering" as UC_Create
  usecase "Assign Instructor" as UC_Assign
  usecase "Modify Schedule" as UC_Modify
  usecase "Cancel Class" as UC_Cancel
  usecase "Notify Stakeholders" as UC_Notify <<include>>
  
  UC_Assign .> UC_Create  : <<include>>
  UC_Modify .> UC_Notify : <<include>>
  UC_Cancel .> UC_Notify : <<include>>
}

Administrator --> UC_Create
Administrator --> UC_Modify
Administrator --> UC_Cancel

note right of UC_Assign
  • Checks instructor availability  
  • Prevents conflicts  
end note

note left of UC_Notify
  • Email & in-app alert  
  • Logs delivery status  
end note

@enduml
