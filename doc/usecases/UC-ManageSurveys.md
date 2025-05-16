Use Case: Manage survey.
=================================
**Actors**: Instructor, Administor

**Scope**: Software system

**Purpose**: Enable instructors to create, edit, and delete surveys for students.

**Type**: Primary 

**Overview**: This use case describes how an instructor manages surveys within the system.  
the instructor can create new surveys, edit existing ones, and delete those that are no longer needed.  
the system provides an intuitive interface to easily manage surveys to ensure they remain up-to-date  
and relevant to participant needs. This process facilitates the collection of relevant data  
and preparation of surveys for effective delivery.


Typical course of events:
----------------------

| Actor Action | System Response |
|:--------------|:----------------|
| 1. The Instructor navigates to the survey management section of the system. | 2. The system displays a list of existing surveys created by the instructor, along with options to create a new survey, edit an existing one, or delete a survey. |
| 3. The Instructor chooses to either:
3a. The Instructor selects the "Create New Survey" option. | 4. The system presents the Instructor with an interface to define survey details such as title, description, opening date, and closing date. |
| 3b. The Instructor selects a survey from the list. |  7. The system displays the selected survey with options to modify its details (title, dates) and questions. |
| 3c. The Instructor selects a survey from the list and chooses the "Delete" option. | 10. The system prompts the Instructor for confirmation to delete the selected survey |
| 5. The Instructor enters the survey details and proceeds to add questions. | 6. The system provides tools for the Instructor to create different types of questions (e.g., multiple choice, text-based), define answer options, and mark questions as mandatory or optional. |
| 8. The Instructor modifies the survey details or questions as needed. | 9. The system saves the changes made by the Instructor. |
| 11. The Instructor confirms the deletion. | 12. The system removes the survey from the list. |
| 13. The Instructor may choose to preview the survey before finalizing it. | 14. The system displays a preview of the survey as it would appear to the respondents. |
| 15. The Instructor reviews the preview and either:<br>    (15a) Decides the survey is ready and proceeds to make it available.<br>    (15b) Identifies a need for further edits and navigates back to the editing interface. | 16. The system provides options for the Instructor to manage survey distribution (e.g., generate a link, send invitations). |
| 17. The Instructor chooses a method of distribution. | 18. The system generates the survey link or initiates the invitation process. |
| 19. Respondents access and complete the survey. | 20. The system collects and stores the survey responses. |
| 21. The Instructor navigates to the survey results/reporting section. | 22. The system displays a summary or detailed view of the collected responses, potentially with options for analysis and export. |



Alternative Courses:
-----------
3a: The Instructor attempts to create a new survey without entering a title. The system displays an error message prompting for a title.

3b: The Instructor attempts to edit a survey that is currently active (within its opening and closing dates). <br>   The system displays a warning message indicating that some modifications might affect ongoing responses and requires confirmation to proceed.


3c: The Instructor attempts to delete a survey that has received student responses. <br>   The system displays a warning message indicating that deleting the survey will also remove all associated responses and requires confirmation. 

4a: The Instructor enters invalid date formats for the opening or closing date.  <br>  The system displays an error message indicating the correct date format. 

6a: The Instructor attempts to create a multiple-choice question without providing any answer options. <br>  The system displays an error message requiring at least one answer option.

6b: The Instructor tries to mark more than one answer as correct for a single-choice question. <br>  The system prevents this and might display a message clarifying the question type.

8a: The Instructor modifies a question type (e.g., changes a multiple-choice to a text-based question)  that already has responses.  <br>  The system displays a warning that this change might invalidate existing answers for that question and requires confirmation. 

9a: The system fails to save the changes due to a technical issue. <br> The system displays an error message and might suggest retrying.

12a: The Instructor cancels the deletion request. <br> The system returns to the list of surveys without deleting the selected survey.

14a: During the survey preview, the system encounters an error rendering a specific question type. <br> The system displays a generic error message for that section and advises the instructor to review the question setup.
   

Section:MANAGING QUESTION TYPES
-----------
| Actor Action | System Response |
|:--------------|:----------------|
| 1. While creating or editing a survey, the Instructor chooses to add a new question. | 2. The system presents a selection of available question types (e.g., Multiple Choice, True/False, Short Answer, Essay). |
| 3. The Instructor selects a question type. | 4. The system displays the specific interface for defining the selected question type (e.g., for Multiple Choice, fields to enter the question text and answer options). |   
| 5. The Instructor enters the question text and relevant options | 6. The system saves the question and allows the Instructor to add more questions or finalize the survey structure. |  