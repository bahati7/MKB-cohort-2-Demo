# User: [Name of Actor]
=========================

**Description**: A brief overview of this user type and their role within the system.

**Required Skills**:
* Bullet point list of the technical or conceptual skills this actor needs to interact with the system effectively.
* ...

**Special Considerations**:
* Bullet point list of any unique needs, limitations, or important factors to keep in mind for this actor.
* ...

**Goals**:
* Bullet point list of the primary objectives this actor tries to achieve by using the system.
* ...

**Responsibilities**:
* Bullet point list of the key tasks and duties this actor performs within the context of the application.
* ...

**Interactions with Use Cases**:
* Bullet point list of the use cases this actor typically interacts with.
    * [Link to Use Case Name.md] - Brief description of the interaction.
    * [Link to Another Use Case Name.md] - Brief description of the interaction.
    * ...

**Potential Roles within the System**:
* Bullet point list of the different roles this actor might have within the system, especially if role-based permissions are considered.
* ...

**Example (for Student):**

# User: Student
=========================

**Description**: An individual enrolled in a course or session who provides feedback on their learning experience.

**Required Skills**:
* Basic digital literacy (navigating web interfaces, filling out forms).
* Ability to read and understand survey questions.

**Special Considerations**:
* May have varying levels of technical proficiency.
* May access the platform from different devices (desktop, mobile).
* Motivation to provide honest and constructive feedback may vary.
* Data privacy concerns regarding their responses.

**Goals**:
* To provide feedback on their learning experience.
* To potentially review their past feedback.

**Responsibilities**:
* Logging into the platform.
* Locating and selecting relevant surveys.
* Answering survey questions honestly and thoughtfully.
* Submitting completed surveys.

**Interactions with Use Cases**:
* [./usecases/ProvideFeedback.md] - Provides their responses to learning experience questions.
* [./usecases/ReviewPastFeedback.md] - Views their previously submitted feedback.
* [./usecases/ManageUserAccounts.md] - Creates and accesses their account.
* [./usecases/ExperiencePersonalizedSurvey.md] - Interacts with surveys tailored to them.

**Potential Roles within the System**:
* Authenticated User
* Feedback Provider