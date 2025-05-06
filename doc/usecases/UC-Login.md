Use Case: Login.
=================================
**Actors**: Student, Instructor, Administrator.

**Scope**: Survey Management Software System.

**Purpose**: To securely authenticate users (students, instructors, administrators) and redirect them to their personalized dashboard according to their roles.

**Type**: Primary.

**Overview**: This use case describes the process through which users log into the system. The system authenticates them based on their credentials and grants them access to a personalized dashboard where they can perform tasks specific to their roles. Each actor interacts with the login module in a way that initiates their workflow within the system, whether it's completing a survey, managing course content, or overseeing platform activity.

Typical course of events:
----------------------

| Actor Action | System Response |
|:--------------|:----------------|
| 1. This use case begins when a Student, Instructor, or Administrator attempts to log into the platform. | |
| 2. The Actor accesses the login interface and enters their username and password. | 3. The system verifies the provided credentials. |
|4. |If credentials are valid, the system identifies the role of the user.|
|5. | The system redirects the user to their personalized dashboard (student dashboard, instructor dashboard, or admin panel). |
|6. | The system logs the login activity for audit and security purposes. |


Alternative Courses:
-----------
1a. ...

3a. ...

3b. ...

Section: A subsection of the use case, e.g. Paying by cash
-----------
| Actor Action | System Response |
|:--------------|:----------------|
| 1. ...| |
| 2. ... | 3. ... |
|4. ||
|5. | 6. |
