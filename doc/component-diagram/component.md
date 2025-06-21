# Component Diagram

This component diagram presents the architecture of the MKB Survey Application. It shows the main functional blocks (components) of the system and how they interact with each other and with external services.

---

## Purpose

The goal of this diagram is to visualize how the system is structured in terms of major components such as user interfaces, core services, authentication, database, and external dependencies. It also clarifies the relationships between components and helps guide development and collaboration.

---

## Components Overview

### Frontend Components

- **Web User Interface (UI)**  
  Presents the front-end to users (students, instructors, and admins).  
  It communicates with backend services through API calls and responsible for displaying forms, dashboards, and dynamic interactions.

### Backend Core Services

- **Authenticating Service**  
  Handles login, sign-up, logout, and session management.  
  Manages user sessions using JWT or secure cookies.  
  May support external auth providers.

- **User Management Service**  
  Manages user accounts (create, update, delete).  
  Assigns roles such as student, instructor, or admin.  
  Validates user data and manages permissions.

- **Survey Management Service**  
  Creates, modifies, and deletes surveys.  
  Handles business logic related to questions, types of responses, and survey status (active/draft/closed).  
  Interacts with the survey data store.

- **Feedback and Reporting Service**  
  Collects feedback submitted by students.  
  Generates statistics and reports (e.g., CSV, PDF exports).  
  May provide insights to instructors or admins.

- **Notification Service**  
  Sends notifications to users (email confirmations, survey reminders, etc.).  
  Connects to an external messaging service to deliver emails or SMS.

### Database Layer

- **Application Database (MySQL)**  
  Central data store for:
  - User accounts
  - Survey definitions
  - Feedback responses
  - Generated reports  
    Ensures data integrity, security, and persistence.

### External Dependencies

- **Email/SMS Gateway (External Cloud Service)**  
  An external third-party service used to send notifications triggered by the Notification Service.  
  Examples include SendGrid, Mailgun, Firebase, or Twilio.

---

## Example Workflow

1. A student logs in via the Web UI, which sends their credentials to the Authenticating Service.
2. Upon successful login, they are redirected to the Student Home Screen.
3. They complete a survey form; the data is passed to the Feedback and Reporting Service.
4. The feedback is stored in the Application Database.
5. A notification is triggered and handled by the Notification Service.
6. The Notification Service communicates with the Email/SMS Gateway to deliver the message to the instructor.

---

## Component Diagram

```
@startuml
!theme cyborg

skinparam database {
  BackgroundColor #ffffff
  BorderColor #333333
  RoundCorner 30
}
skinparam shadowing true
skinparam arrowColor #3366cc
skinparam componentBorderColor #666666
skinparam defaultTextAlignment center

title Component Diagram - Survey System

' Define components
component "Web User Interface" as UI
component "User Management Service" as UserMgmt
component "Authenticating Service" as Auth
component "Survey Management Service" as SurveyMgmt
component "Feedback and Reporting Service" as FeedbackReport
component "Notification Service" as Notification
database "Application Database" as DB

cloud "External Systems" {
  [Email/SMS Gateway]
}

' Relationships (Primary Interactions)
UI --> Auth
UI --> UserMgmt
UI --> SurveyMgmt
UI --> FeedbackReport

Auth --> DB
FeedbackReport --> DB
SurveyMgmt --> DB
UserMgmt --> DB
Notification --> DB
Notification --> [Email/SMS Gateway]

' Service-to-Service interactions
SurveyMgmt ..> Notification
Auth ..> Notification

@enduml


```

![Component Diagram](image-2.png)

---

## Notes

- This version intentionally maintains a simplified structure, based on the initial component diagram shared by THEOPHILEACHIZA, while integrating the external dependency proposed by Philemon.
- The representation of internal vs external components is for visualization purposes only and does not imply fixed architectural boundaries. The final implementation may evolve based on technical constraints or deployment choices.
- The Notification Service remains optional for the MVP but is included for completeness.
- In future iterations, we may further separate frontend/backend layers visually and introduce components such as API Gateway, Analytics Services, or Admin Logs.
