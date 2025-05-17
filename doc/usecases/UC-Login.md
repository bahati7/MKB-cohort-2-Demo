# Use Case: Login

## Actors
- **Student**: Logs in to access and complete surveys.  
- **Instructor**: Logs in to manage class activities and analyze feedback.  
- **Administrator**: Logs in to configure, monitor, and manage the platform.  

## Scope
Survey Management Software System.

## Purpose
To securely authenticate users (students, instructors, administrators), ensure account protection through login attempt limits, and redirect them to their personalized dashboards based on their roles.

## Type
Primary

## Overview
This use case describes how different users log into the system. It ensures secure authentication and role-based access. If a user does not yet have an account, they are guided to create one. Failed login attempts are tracked, and security measures like temporary account lockout are enforced to prevent brute-force attacks.

---

## Preconditions
- The user has access to the login interface.
- The system is connected to the authentication database.
- The user has already registered OR will be offered to register.

## Postconditions
- The user is successfully logged in and redirected to their dashboard.  
OR  
- The user is locked out temporarily after too many failed login attempts.  
OR  
- The user is redirected to create a new account if no account exists.

## Supplemental Requirements
- Secure password storage (hashed, salted).  
- Session timeout policy.  
- Audit logs for login attempts and failures.  
- CAPTCHA or similar protection may be added after 3+ failed attempts.

---

## Typical Course of Events
| Actor Action | System Response |
|:--------------|:----------------|
| 1. This use case begins when a Student, Instructor, or Administrator wants to access the platform. | |
| 2. The actor accesses the login interface and enters their username and password. | 3. The system checks if the account exists. |
| 4. If the account does not exist, the actor is prompted to create one. | The system redirects the user to the registration interface. |
| 5. If the account exists, the system verifies the provided credentials. | 6. If the credentials are correct, the system logs the user in and redirects them to their role-specific dashboard. |
| 7. If the password is incorrect, the system increments the login attempt counter. | 8. After 3 failed attempts, the system locks the account temporarily (1 minute) and displays an error with a reset option. After 5 failed attempts, the account is locked for 3 minutes and an alert is shown. |

---

## Alternative Courses



> **Clarification:**  

---

## Section: Forgotten Password Recovery
