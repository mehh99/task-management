# Task Management API

## Overview
The Task Management API is a RESTful web service that enables users to manage their tasks efficiently. It provides features for user authentication, task creation, retrieval, updating, and deletion. This API is designed to facilitate task management for individuals or teams.

## Features
- **User Authentication**: Secure login using token-based authentication.
- **Task Management**:
  - Create new tasks with descriptions and due dates.
  - Retrieve a list of all tasks.
  - Update existing tasks, including changing descriptions and due dates.
  - Delete tasks when they are no longer needed.
  
## Technologies Used
- Python 3.x
- Django 5.x
- Django REST Framework
- SQLite (or any other database of your choice)

## Getting Started

### Prerequisites
Before you begin, ensure you have the following installed:
- Python 3.x
- pip (Python package installer)

## API Endpoints

### Authentication

- **POST /signin/**
  - **Description**: Authenticates a user and returns a token.
  - **Request Body**:
    ```json
    {
      "username": "your_username",
      "password": "your_password"
    }
    ```
  - **Response**:
    ```json
    {
      "authenticated": true,
      "token": "Token your_token_here"
    }
    ```
  - **Responses on Failure**:
    ```json
    {
      "authenticated": false,
      "token": null
    }
    ```

### Task Management Endpoints

- **GET /all/**
  - **Description**: Retrieve all tasks.
  - **Authorization**: Requires token authentication.

- **POST /new/**
  - **Description**: Create a new task.
  - **Authorization**: Requires token authentication.
  - **Request Body**:
    ```json
    {
      "description": "Task description",
      "due_in": 5 // Due date in days from today
    }
    ```
  - **Response**:
    ```json
    {
      "done": true
    }
    ```

- **POST /update/**
  - **Description**: Update an existing task.
  - **Authorization**: Requires token authentication.
  - **Request Body**:
    ```json
    {
      "task_id": 1,
      "description": "Updated task description",
      "due_in": 3 // Due date in days from today
    }
    ```
  - **Response**:
    ```json
    {
      "done": true
    }
    ```

- **DELETE /delete/**
  - **Description**: Delete a task.
  - **Authorization**: Requires token authentication.
  - **Request Body**:
    ```json
    {
      "task_id": 1
    }
    ```
  - **Response**:
    ```json
    {
      "done": true
    }
    ```
    ### Task Completion Endpoint

- **POST /complete/**
  - **Description**: Mark a task as completed.
  - **Authorization**: Requires token authentication.
  - **Request Body**:
    ```json
    {
      "task_id": 1 // ID of the task to mark as completed
    }
    ```
  - **Response**:
    ```json
    {
      "done": true
    }
    ```
  - **Responses on Failure**:
    ```json
    {
      "error": "Task not found" // If the task with the specified ID does not exist
    }
    ```
    ```json
    {
      "error": "NOT NULL constraint failed: todo_task.due" // If the due date is not provided when required
    }
    ```


## Error Handling
Common error responses include:
- **400 Bad Request**: Returned when the request body is malformed.
- **401 Unauthorized**: Returned when authentication fails.
- **403 Forbidden**: Returned when access is denied.
- **404 Not Found**: Returned when a task with the specified ID does not exist.
- **500 Internal Server Error**: Returned for unexpected server errors.


