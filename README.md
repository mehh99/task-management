Task Management API
This API allows users to manage their tasks. Users can create, update, complete, and delete tasks. The API is secured with token authentication for safety.

Features
User Authentication: Utilizes token-based authentication for user security.
Task Management: Users can create, retrieve, update, and delete tasks.
Task Completion: Users can mark tasks as completed.
Technologies Used
Django
Django REST Framework
SQLite (or other databases)
Endpoints
1. Sign In
URL: /signin/
Method: POST
Body:
json
Copy code
{
    "username": "your_username",
    "password": "your_password"
}
Response:
json
Copy code
{
    "authenticated": true,
    "token": "Token your_token_here"
}
2. Get All Tasks
URL: /all/
Method: GET
Headers:
makefile
Copy code
Authorization: Token your_token_here
Response:
json
Copy code
{
    "tasks": [
        {
            "id": 1,
            "description": "Task description",
            "due": "2024-09-30",
            "is_completed": false
        }
    ]
}
3. Create New Task
URL: /new/
Method: POST
Headers:
makefile
Copy code
Authorization: Token your_token_here
Body:
json
Copy code
{
    "description": "Task description",
    "due": "2024-09-30"
}
Response:
json
Copy code
{
    "done": true
}
4. Update Task
URL: /update/
Method: POST
Headers:
makefile
Copy code
Authorization: Token your_token_here
Body:
json
Copy code
{
    "task_id": 1,
    "description": "New description",
    "due_in": 5  // Adds 5 days from today
}
Response:
json
Copy code
{
    "done": true
}
5. Complete Task
URL: /complete/
Method: POST
Headers:
makefile
Copy code
Authorization: Token your_token_here
Body:
json
Copy code
{
    "task_id": 1
}
Response:
json
Copy code
{
    "done": true
}
6. Delete Task
URL: /delete/
Method: DELETE
Headers:
makefile
Copy code
Authorization: Token your_token_here
Body:
json
Copy code
{
    "task_id": 1
}
Response:
json
Copy code
{
    "done": true
}
How to Run
Clone this repository.
Install dependencies:
bash
Copy code
pip install -r requirements.txt
Run migrations:
bash
Copy code
python manage.py migrate
Start the server:
bash
Copy code
python manage.py runserver
