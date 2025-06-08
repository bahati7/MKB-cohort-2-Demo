# Use Case: Reset Password 

## Actors
- **Student:** Requests password reset to regain access.  
- **Instructor:** Uses password recovery to log back into the platform.  
- **Administrator:** Recovers access through password reset (with enhanced fallback procedures).  

## Scope:  
Student Survey Application  

## Purpose:  
To help users securely reset their password when they forget or lose access.  

## Type:  
Primary  

## Overview:  
This use case outlines the steps involved when a user initiates a password reset request, validates ownership via email, and updates their password securely.

## Use Case Diagram
``` plantuml
@startuml Reset Password Use Case Diagram

' Title
title Reset Password Use Case Diagram

' left to right direction

' Actors
actor Student
actor Instructor
actor Administrator

' Use Cases
rectangle "MKB - Survey Web Application" {
    usecase "Access Password\nReset Interface" as UC1
    usecase "Enter Registered\nEmail Address" as UC2
    usecase "Check Email\nExists in Database" as UC3
    usecase "Display Error:\nEmail Not Found" as UC4
    usecase "Send Password\nReset Link" as UC5
    usecase "Open Secure\nReset Form" as UC6
    usecase "Update Password\nin Database" as UC7
    usecase "Redirect to\nLogin Page" as UC8
}

' Actor Relations
Student --> UC1
Instructor --> UC1
Administrator --> UC1

' Use Case Flow
UC1 --> UC2
UC2 --> UC3
UC3 -.-|> UC4 : if email not found
UC3 --> UC5 : if email found
UC5 --> UC6
UC6 --> UC7
UC7 --> UC8

' Notes
note left of UC4
User is advised to register if no account exists.
end note

note right of UC5
Link expires after 15 minutes and is single-use only.
end note

note bottom of UC8
User receives confirmation and is prompted to log in.
end note

caption This diagram describes the password reset workflow for all users.

@enduml
```
## Visual representation
![Login Use Case Diagram](UC-Password_Recovery.png)

## Typical Course of Events
| Actor Action | System Response|
|:--------|:-------|
| 1. The user clicks “Forgot Password?” on the login page. | |  
| 2. The user enters their registered email address.| 3. The system verifies that the email exists in the database.|  
| 4.| If valid, the system sends a secure reset link to the user’s email.|  
| 5. The user clicks the reset link.| 6. The system displays a secure password reset form.|  
| 7. The user enters a new password and submits.| 8. The system validates and updates the password.|  
| 9.| A confirmation message is shown and the user is redirected to the login page.|  

## Alternative Courses
3a. Email Not Registered  
→ Message: "No account found for this email."  
→ Prompt user to retry or create a new account.  

4a. Email Delivery Failure  
→ Message: "We were unable to send the reset link. Please try again later."  
→ System logs the failure; retry option available.  

## Admin Special Case
→ If an Administrator cannot receive emails:  
→ Instructions are shown to reset password manually via database access (e.g., cPanel or phpMyAdmin).  
→ Admin must hash the new password using the system’s hashing standard.  

## Related Use Cases
[Login Use Case Diagram](../UC-Login_new.md) (General Use case)  
[Create Account Use Case Diagram](UC-Create_Account.md) (Sub-use case)