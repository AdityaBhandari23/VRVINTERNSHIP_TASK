# VRVINTERNSHIP_TASK

# Django JWT Authentication API

This is a Django-based REST API project that implements user authentication and role-based permissions using **JWT (JSON Web Tokens)**. It supports user registration, login, logout, and role-based access control for endpoints.

---

## Features
1. **User Registration:** Register users with different roles (`director`, `hod`, `student`).
2. **Login:** Obtain JWT `access` and `refresh` tokens for authentication.
3. **Logout:** Blacklist tokens for secure logout.
4. **Role-Based Access:** Restrict endpoints based on user roles.
5. **CRUD for Articles:** Authorized users can create, update, view, and delete articles.

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
   git clone <repository_url>
   cd <repository_folder>
