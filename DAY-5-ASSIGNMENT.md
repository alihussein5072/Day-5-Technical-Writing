# DAY 5 – TECHNICAL WRITING ASSIGNMENT

**Program:** Power Learn Project (PLP)  
**Module:** Technical Writing  
**Assignment:** Day 5  
**Date:** 25 November 2026

---

# EXERCISE A: USER MANUAL PROCEDURE

## Topic: How to Create a GitHub Repository and Make Your First Commit

### 1. Introduction

GitHub is an online platform used by developers to store, manage, and share software projects. It uses Git, a version control system that tracks changes made to files over time.

This procedure explains how a beginner can create a GitHub repository, connect it to a local computer, and make the first commit.

### 2. Prerequisites

Before starting, ensure that you have:

1. A computer with Windows, Linux, or macOS installed.
2. A stable internet connection.
3. A GitHub account.
4. Git installed on your computer.
5. Basic computer literacy.
6. A text editor such as Visual Studio Code or Notepad.

### 3. Step-by-Step Procedure

**Step 1: Open GitHub**

Action: Open your web browser and visit https://github.com/.

Expected result: The GitHub homepage appears.

**Step 2: Sign in to GitHub**

Action: Enter your GitHub username or email address and password.

Expected result: Your GitHub dashboard opens.

**Step 3: Create a new repository**

Action: Click the plus (+) icon and select New repository.

Expected result: The repository creation page appears.

**Step 4: Enter the repository name**

Action: Type `my-first-project` in the repository name field.

Expected result: The repository name appears in the field.

**Step 5: Add a description**

Action: Enter a short description of your project.

Expected result: The description appears in the description field.

**Step 6: Select repository visibility**

Action: Choose Public or Private.

Expected result: Your preferred visibility option is selected.

**Step 7: Create the repository**

Action: Click Create repository.

Expected result: GitHub creates the repository and displays its main page.

**Step 8: Open the terminal**

Action: Open Command Prompt, PowerShell, or Git Bash.

Expected result: A terminal window appears.

**Step 9: Create a project folder**

Action: Run:

```bash
mkdir my-first-project
```

Expected result: A new folder named my-first-project is created.

**Step 10: Enter the project folder**

Action: Run:

```bash
cd my-first-project
```

Expected result: The terminal moves into the project folder.

**Step 11: Initialize Git**

Action: Run:

```bash
git init
```

Expected result: Git initializes an empty local repository.

**Step 12: Create a README file**

Action: Run:

```bash
echo "# My First Project" > README.md
```

Expected result: A README.md file is created.

**Step 13: Stage the file**

Action: Run:

```bash
git add README.md
```

Expected result: The README.md file is added to the staging area.

**Step 14: Make the first commit**

Action: Run:

```bash
git commit -m "Initial commit"
```

Expected result: Git records the first snapshot of the project.

**Step 15: Connect the local repository to GitHub**

Action: Run the following command, replacing USERNAME with your GitHub username:

```bash
git remote add origin https://github.com/USERNAME/my-first-project.git
```

Expected result: The local repository is connected to the GitHub repository.

**Step 16: Rename the branch**

Action: Run:

```bash
git branch -M main
```

Expected result: The current branch is named main.

**Step 17: Upload the project**

Action: Run:

```bash
git push -u origin main
```

Expected result: Your project files are uploaded to GitHub.

### 4. Screenshot Description

The screenshot should show the GitHub repository after a successful upload.

It should include:

- Repository name.
- README.md file.
- Main branch.
- Initial commit message.
- Repository URL.

**Figure 1: GitHub repository showing the successfully uploaded project.**

### 5. Troubleshooting

**Common error: Git is not recognized as an internal or external command.**

Cause: Git may not be installed or its installation directory may not be added to the system PATH.

Solution:

1. Download Git from https://git-scm.com/.
2. Install Git using the recommended settings.
3. Close and reopen the terminal.
4. Run:

```bash
git --version
```

5. Confirm that Git displays its installed version.

### 6. Conclusion

Creating a GitHub repository and making the first commit helps beginners understand version control and project management. By following these steps, a student can create a repository, track project changes, and upload files to GitHub.

---

# EXERCISE B: API REFERENCE ENTRY

## Topic: Create a New Task in a Project Management Application

### 1. Introduction

An API (Application Programming Interface) allows different software applications to communicate and exchange information.

The Create Task API endpoint allows an authenticated user to create a new task within a project management application.

### 2. Endpoint Information

| Property | Description |
|---|---|
| API Name | Create Task API |
| HTTP Method | POST |
| Endpoint | `/api/v1/projects/{project_id}/tasks` |
| Authentication | Required |
| Content Type | application/json |
| Response Format | JSON |

### 3. Description

This endpoint creates a new task under a specified project.

An authenticated user sends a POST request containing task details. The application validates the information, saves the task in the database, and returns the newly created task with its unique ID and creation date.

### 4. Request Parameters

#### A. Path Parameters

| Parameter | Data Type | Requirement | Description |
|---|---|---|---|
| project_id | Integer | Required | Unique ID of the project where the task will be created. |

Example:

```text
/api/v1/projects/105/tasks
```

#### B. Query Parameters

This endpoint does not require any query parameters.

#### C. Request Body Parameters

| Parameter | Data Type | Requirement | Description |
|---|---|---|---|
| title | String | Required | Name or title of the task. |
| description | String | Optional | Additional information about the task. |
| assignee_id | Integer | Required | Unique ID of the assigned user. |
| due_date | String (Date) | Required | Deadline in YYYY-MM-DD format. |
| priority | String | Required | Priority level: low, medium, or high. |

### 5. Required Request Headers

| Header | Requirement | Description |
|---|---|---|
| Authorization | Required | Contains the user's authentication token. |
| Content-Type | Required | Specifies that the request body is JSON. |
| Accept | Optional | Specifies that the client expects a JSON response. |

Example:

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json
Accept: application/json
```

### 6. Example Request

**HTTP Request:**

```http
POST /api/v1/projects/105/tasks HTTP/1.1
Host: api.projectmanager.com
Authorization: Bearer abc123xyz789
Content-Type: application/json
Accept: application/json
```

**Request Body (JSON):**

```json
{
  "title": "Prepare Financial Report",
  "description": "Prepare and submit the monthly financial performance report.",
  "assignee_id": 204,
  "due_date": "2026-12-15",
  "priority": "high"
}
```

**Explanation:**

- title: Specifies the name of the task.
- description: Explains what the task involves.
- assignee_id: Identifies the assigned user.
- due_date: Specifies the completion deadline.
- priority: Indicates the urgency of the task.

### 7. Successful Response

When the task is successfully created, the API returns HTTP status code `201 Created`.

**Example Response Body:**

```json
{
  "success": true,
  "message": "Task created successfully.",
  "data": {
    "id": 501,
    "project_id": 105,
    "title": "Prepare Financial Report",
    "description": "Prepare and submit the monthly financial performance report.",
    "assignee_id": 204,
    "due_date": "2026-12-15",
    "priority": "high",
    "status": "pending",
    "created_at": "2026-11-25T16:30:00Z"
  }
}
```

**Explanation of the response:**

| Field | Description |
|---|---|
| success | Indicates whether the operation was successful. |
| message | Provides a confirmation message. |
| id | Unique identification number assigned to the task. |
| project_id | Identifies the project containing the task. |
| title | Name of the created task. |
| description | Additional task information. |
| assignee_id | ID of the assigned user. |
| due_date | Task completion deadline. |
| priority | Task priority level. |
| status | Current task status. |
| created_at | Date and time when the task was created. |

### 8. HTTP Response Codes

| Status Code | Name | Explanation |
|---|---|---|
| 201 | Created | The task has been successfully created. |
| 400 | Bad Request | The request contains invalid data or incorrectly formatted JSON. |
| 401 | Unauthorized | The user has not provided a valid authentication token. |
| 403 | Forbidden | The authenticated user does not have permission to create tasks. |
| 404 | Not Found | The specified project or assigned user does not exist. |
| 409 | Conflict | The request conflicts with an existing resource or project rule. |
| 415 | Unsupported Media Type | The request does not use the supported JSON content type. |
| 422 | Unprocessable Entity | The submitted information fails validation. |
| 429 | Too Many Requests | The user has exceeded the API request limit. |
| 500 | Internal Server Error | An unexpected server-side error prevents task creation. |
| 503 | Service Unavailable | The API service is temporarily unavailable. |

### 9. Validation Rules

The API should enforce the following validation rules:

1. The task title must not be empty.
2. The description is optional.
3. The assignee ID must belong to an existing user.
4. The due date must follow the YYYY-MM-DD format.
5. The priority must be either low, medium, or high.
6. The project ID must identify an existing project.
7. The user must be authenticated and authorized to create tasks in the specified project.

### 10. Security Considerations

The API should follow appropriate security practices:

- Authentication: Require a valid access token.
- Authorization: Ensure users can only create tasks in projects where they have permission.
- Input validation: Validate all submitted information before saving it.
- Data protection: Use HTTPS to protect information during transmission.
- Error handling: Avoid exposing sensitive system information in error messages.

### 11. Conclusion

The Create Task API endpoint provides a structured way for authenticated users to create and manage tasks within a project management application. By using the POST method and JSON request format, the API receives task information, validates it, stores it, and returns a response indicating whether the operation was successful.

---

# END OF DAY 5 ASSIGNMENT
