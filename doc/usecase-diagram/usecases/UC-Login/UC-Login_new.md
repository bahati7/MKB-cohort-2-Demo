# Use Case: Login

## Actors
- **Student**: Logs in to access and complete surveys.  
- **Instructor**: Logs in to manage class activities and analyze feedback.  
- **Administrator**: Logs in to configure, monitor, and manage the platform. 

## Scope:  
Student Survey Application

## Purpose:  
To securely authenticate users (students, instructors, administrators) and redirect them to their personalized dashboards based on their roles.

## Type:  
Primary

## Overview:  
This use case describes how different users gain access to the system. It focuses on validating credentials to ensure secure, role-based access. For details on account creation or password recovery, please refer to their dedicated use case documents.

## Use Case Diagram
``` plantuml
@startuml Login Use Case Diagram
' Title
title Login Use Case Diagram

' Direction
' left to right direction

' Actors
actor Student
actor Instructor
actor Administrator

' Use Cases
rectangle "MKB - Survey Web Application" {
  usecase "Access Login\nInterface" as UC1
  usecase "Enter\nCredentials" as UC2
  usecase "Verify\nAccount Exists" as UC3
  usecase "Redirect\nto Registration" as UC4
  usecase "Validate\nCredentials" as UC5
  usecase "Redirect\nto Specific Dashboard" as UC6
  usecase "Increment\nFailed Attemps" as UC7
  usecase "Lock\nAccount Temporarily" as UC8
  usecase "Display\nError Message" as UC9
  usecase "Forgot\nPassworrd" as UC10
}

' Actor Relations
Student --> UC1
Instructor --> UC1
Administrator --> UC1

' Use Case Flow
UC1 -.-|> UC10
UC1 --> UC2
UC1 -.-|> UC4
UC2 --> UC3
UC3 ..|> UC4 : if account doesn't exist
UC3 --> UC5 : if account exists
UC5 ------> UC6 : if credentials are valid
UC5 ...|> UC7 : credentials are invalid
UC5 -.-|> UC10 : credentials are invalid
UC7 ..|> UC8
UC7 --> UC9 : display warning

' Note for locking logic
note left of UC4
Registration system\n
See the registration diagram: sub_UC-Login/UC-Create_Account.md
end note

note bottom of UC8
After 3 failed attemps: lock for 1 minute\n
After 5 failed attemps: lock for 3 minutes\n
end note

note bottom of UC10
Recovery system.
See the Recovery diagram: sub_UC-Login/UC-Password_Recovery.md
end note

caption This diagram describes the global login process for all actors.

@enduml
```

Here's a visual representation of the Login use case:

![Login Use Case Diagram](UC-Login_new.png)

## Typical Course of Events

| Actor Action| System Response|
| ----------- | ----------- |
| 1. The use case begins when a user clicks on “Create Account.” | |
| 2. The user fills out the form (email and password). | 3. The system validates input format and required fields. |
| 4. | The system checks if the email is already used. |
| 5. | If valid and unique, the system securely stores the new user data. |
| 6. | The system sends a confirmation email (if required), then redirects the user to the login page. |

## Alternative Courses

2a. Invalid or Missing Input  
→ System displays an error and highlights invalid fields.  
→ User is prompted to correct the form.  

5a. Email Already Exists  
→ Message: "An account with this email already exists."  
→ Redirect or prompt to login or reset password.

5a. Password is incorrect  
→ Message: "Password prompted is wrong, please try again"  
→ Redirect or prompt to reset password.  

7a. Database or Network Error  
→ Message: "An error occurred. Please try again later."  
→ Retry available or log support incident.  

## Related Use Cases
[Create Account Use Case Diagram](sub_UC-Login/UC-Create_Account.md) (Sub-use case)
[Password Recovery Use Case Diagram](sub_UC-Login/UC-Password_Recovery.md) (Sub-use case)