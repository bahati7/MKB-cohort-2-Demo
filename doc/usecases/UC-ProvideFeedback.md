Use Case: Provide Feedback
=================================
**Actors**: Student

**Scope**: Software system

**Purpose**: Allow students to complete and submit their responses to surveys.

**Type**: Primary

**Overview**: Students access available surveys from their dashboard, respond to the questions, and submit their feedback. The system securely stores the data for future analysis.

Typical course of events:
----------------------

| Actor Action | System Response |
|:--------------|:----------------|
| 1. This use case begins when the Student accesses their dashboard to view available surveys. | 2. The system displays the list of available surveys. |
| 3. The Student selects a survey and starts responding to the questions. | 4. The system records the responses as they are entered. |
| 5. The Student submits the completed survey. | 6. The system securely stores the feedback for future analysis. |

Alternative Courses:
-----------
1a. No surveys are available:  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system informs the Student that no surveys are currently available.

3a. The Student exits the survey before completion:  
&nbsp;&nbsp;&nbsp;&nbsp;1. The system saves the progress for later completion.

Section: Submitting Feedback
-----------
| Actor Action | System Response |
|:--------------|:----------------|
| 1. The Student completes all questions in the survey. | 2. The system validates that all required fields are filled. |
| 3. The Student submits the survey. | 4. The system confirms successful submission and stores the data securely. |
