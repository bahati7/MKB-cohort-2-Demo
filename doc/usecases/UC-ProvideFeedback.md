Use Case: Provide Feedback
=================================
**Actors**: Student

**Scope**: Software system

**Purpose**: Allow students to complete and submit their responses to surveys.

**Type**: Primary

**Overview**:  
Students log in to the system and access their personalized dashboard, where they can view a list of available surveys assigned to them. They select a survey, read the instructions, and respond to each question, which may include multiple-choice, rating scales, or open-ended responses. Students can review and edit their answers before submitting. Upon submission, the system securely stores the feedback for future analysis and may provide a confirmation message. If a student leaves a survey incomplete, their progress is saved for later completion.

Typical Course of Events:
----------------------

| Actor Action | System Response |
|:--------------|:----------------|
| 1. The Student logs in and accesses their dashboard. | 2. The system authenticates the Student and displays the dashboard with available surveys. |
| 3. The Student reviews the list and selects a survey to complete. | 4. The system displays the selected survey, including instructions and questions. |
| 5. The Student responds to each question, navigating through the survey. | 6. The system records each response as it is entered and allows navigation between questions. |
| 7. The Student reviews their answers and submits the completed survey. | 8. The system validates that all required fields are filled, confirms submission, and securely stores the feedback for future analysis. |

Alternative Courses:
-----------
1a. No surveys are available:  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system informs the Student that no surveys are currently available.

5a. The Student exits the survey before completion:  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system automatically saves the Student's progress, allowing them to resume later.

7a. Required questions are not answered:  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system prompts the Student to complete all required fields before allowing submission.

Section: Submitting Feedback
-----------
| Actor Action | System Response |
|:--------------|:----------------|
| 1. The Student completes all questions in the survey. | 2. The system checks that all required fields are filled and highlights any missing responses. |
| 3. The Student submits the survey. | 4. The system confirms successful submission, stores the data securely, and may display a thank-you message or feedback summary. |

Security and Privacy Considerations:
-----------
- All feedback is stored securely and access is restricted to authorized personnel.
- Student responses are anonymized or pseudonymized where appropriate to protect privacy.
- The system complies with relevant data protection regulations.

