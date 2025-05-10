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
| 1. This use case begins when a Student, Instructor, or Administrator wants to access the platform. | |
| 2. The Actor accesses the login interface and enters their username and password. | 3. The system checks if the account exists. |
|4. If the account does not exist, the actor is prompted to create one. | The system redirects the user to the registration interface. |
|5. If the account exists, the system verifies the provided credentials | 6. If the credentials are correct, the system logs the user in and redirects them to their role-specific dashboard (student dashboard, instructor dashboard, or admin panel). |
|7. | If the password is incorrect, the system increments the login attempt counter. |
|8. | After 3 failed attempts, the system temporarily (1 minutes)  locks the account and displays an error message with the option to reset password, after 5 failed attempts the system temporarily (3 minutes ) locks the account and also displays an error message. |


Alternative Courses:
-----------
1a. the user chooses to register a new account instead of logging in.  
- The system redirects them to the registration form where they provide required information.
2a. Invalid credentials (first to fifth failed attempt)
- The system displays an error message: "Incorrect username or password".
- The attempt is logged as failed.
- The user is allowed to retry up to 5 times.
2b. Exceeded maximum login attemps (e.g., 5 consecutive failures)
- The system temporarilly locks the account for a predefined period (e.g., 3 consecutive failures: 1 minutes and 5 consecutive failures: 3 minutes).
- An alert message is shown: "Too many failed attempts.Please try again in x minutes."
- Optionnally, the system notifies the administrator or logs a security flag.

Section: Forgotten Password Recovery
-----------
| Actor Action | System Response |
|:--------------|:----------------|
| 1. The Actor clicks “Forgot password?” on the login screen.| |
| 2. The Actor enters their registered email address. | 3. The system checks if the email exists. |
|4. |If valid, the system sends a secure password reset link to the email.|
|5. The Actor clicks the link in their inbox. | 6. The system opens a secure page to reset the password. |
|7. The Actor submits the new password. | 8. The system updates the password and confirms the change. |
|9. |The Actor is redirected to the login page with a success message. |
