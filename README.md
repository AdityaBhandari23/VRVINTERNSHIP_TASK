# VRVINTERNSHIP_TASK

# Django JWT Authentication API

This is a Django-based REST API project that implements user authentication and role-based permissions using **JWT (JSON Web Tokens)**. It supports user registration, login, logout, and role-based access control for endpoints.

---

## Features
1. **User Registration:** Register users with different roles (`director`, `hod`, `student`).
2. **Login:** Obtain JWT `access` and `refresh` tokens for authentication.
3. **Logout:** Blacklist tokens for secure logout.
4. **Role-Based Access:** Restrict endpoints based on user roles.

---

## Technologies Used
- Python 3.8+
- Django 4.2
- Django REST Framework
- Simple JWT (for authentication)
- SQLite (default database)

---

## Installation and Setup

### Prerequisites
- Python 3.8 or above
- pip (Python package manager)

### Steps to Run the Project
1. Clone the repository:
   ```bash
   git clone <https://github.com/AdityaBhandari23/VRVINTERNSHIP_TASK.git>
   cd VRVINTERNSHIP_TASK

### Create a virtual environment:
```
python -m venv venv
source venv/bin/activate    # For Linux/Mac
venv\Scripts\activate       # For Windows
```

### Install dependencies:
pip install -r requirements.txt

### Apply migrations:
```
python manage.py makemigrations
python manage.py migrate
```
### Start the server:
```
python manage.py runserver
```  

# Django JWT Authentication API

This project provides a REST API with role-based authentication using **Django REST Framework** and **JWT (JSON Web Tokens)**. The API allows users to register, login, access the dashboard, and perform article management based on their roles.

## API Endpoints

### 1. User Registration
- **Endpoint:** `/api/auth/register/`
- **Method:** `POST`
- **Payload:**
- **Role options:** "director", "hod", "student"
```json
{
    "username": "john_doe",
    "email": "john@example.com",
    "password": "strong_password",
    "role": "student"   
}
```
Response:
```
json

{
    "id": 1,
    "username": "john_doe",
    "email": "john@example.com",
    "role": "student"
}
```
### 2. User Login
Endpoint: /api/auth/login/
Method: POST
Payload:
```
{
    "username": "john_doe",
    "password": "strong_password"
}
```
Response:
json
```
{
    "refresh": "<refresh_token>",
    "access": "<access_token>",
    "user": {
        "id": 1,
        "username": "john_doe",
        "email": "john@example.com",
        "role": "student"
    }
}
```
### 3. Logout
Endpoint: /api/auth/logout/
Method: POST
Headers:
Authorization: Bearer <access_token>
Payload:
json
```
{
    "refresh": "<refresh_token>"
}
```
Response:
json
```
{
    "message": "Logged out successfully."
}
```
### 4. Access Dashboard
Endpoint: /api/dashboard/
Method: GET
Headers:
Authorization: Bearer <access_token>
Response for Role student:
json
```
{
    "message": "Welcome to the dashboard!",
    "user": "john_doe"
}
```
Response if Unauthorized:
json
```
{
    "detail": "You do not have permission to perform this action."
}
```
### 5. Articles (HOD Access Only)
List/Create Articles
Endpoint: /api/articles/
Method: GET (List), POST (Create)

Authorization: Bearer <access_token>
Payload (for POST):
json
```
{
    "title": "New Article",
    "content": "This is the content of the article."
}
```

Retrieve/Update/Delete Article
Endpoint: /api/articles/<id>/
Method: GET, PUT, DELETE

### Role-Based Permissions
**Director:** Full access to all resources.

**HOD:** Can manage articles and access the dashboard.

**Student:** Can only access the dashboard.

## Testing with Postman
Import the API collection in Postman.
Perform POST requests for registration and login.
Use the provided access_token to access protected routes (set in the Authorization header).
Test logout with the refresh_token.
## Troubleshooting
Invalid Token:
Ensure tokens are not expired.
Check if the token has been blacklisted.
# Permission Denied:
Confirm the user role matches the endpoint's required permissions.

   
