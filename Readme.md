# Task Management API

## Overview

This project is a task management api built using Django and Django REST Framework. It allows users to create and manage tasks within different houses. Each house can have multiple task lists, and each task list can contain multiple tasks. Users can also attach files to tasks and manage their profiles.

## Features

- **User Authentication**: Users can register, log in, and manage their profiles.
- **House Management**: Users can create houses, join or leave houses, and manage house members.
- **Task Management**: Users can create task lists, add tasks to lists, and update task statuses.
- **File Attachments**: Users can attach files to tasks.
- **Permissions**: Custom permissions to ensure that only authorized users can edit or view certain resources.

## Detailed Explanation

### User Management

- **Models**: The `Profile` model in users/models.py extends the default Django `User` model with additional fields.
- **Serializers**: The `UserSerializer` and `ProfileSerializer` in users/serializers.py handle the serialization and deserialization of user and profile data.
- **ViewSets**: The `UserViewSet` and `ProfileViewSet` in users/viewsets.py provide the API endpoints for user and profile management.
- **Permissions**: Custom permissions in users/permissions.py ensure that users can only edit their own profiles.

### House Management

- **Models**: The `House` model in house/models.py represents a house.
- **Serializers**: The `HouseSerializer` in house/serializers.py handles the serialization of house data.
- **ViewSets**: The `HouseViewSet` in house/viewsets.py provides the API endpoints for house management.
- **Permissions**: Custom permissions in house/permissions.py ensure that only house managers can edit house details.

### Task Management

- **Models**: The `TaskList`, `Task`, and `Attachment` models in task/models.py represent task lists, tasks, and file attachments, respectively.
- **Serializers**: The `TaskListSerializer`, `TaskSerializer`, and `AttachmentSerializer` in task/serializers.py handle the serialization of task-related data.
- **ViewSets**: The `TaskListViewSet`, `TaskViewSet`, and `AttachmentViewSet` in task/viewsets.py provide the API endpoints for task management.
- **Permissions**: Custom permissions in task/permissions.py ensure that only authorized users can edit or view tasks and attachments.
- **Signals**: Signals in task/signals.py update house points and task list statuses when tasks are saved.

### API Routing

- **Routers**: Routers in task/router.py, house/router.py, and users/router.py register the viewsets with the API.
- **URLs**: The main URL configuration in task_app/urls.py includes the API routes for authentication, user management, house management, and task management.

## Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/task_app.git
   cd task_app
   ```

2. Create a virtual environment and activate it:
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the dependencies:
   ```sh
   pip install -r requirements.txt
   ```

4. Apply the migrations:
   ```sh
   python manage.py migrate
   ```

5. Run the development server:
   ```sh
   python manage.py runserver
   ```

## Usage

- Access the admin panel at `http://127.0.0.1:8000/admin/` to manage users, houses, and tasks.
- Use the API endpoints to interact with the application on browsable api:
```bash
http://127.0.0.1:8000/api/accounts/users/
http://127.0.0.1:8000/api/accounts/house/
http://127.0.0.1:8000/api/accounts/task/
```

