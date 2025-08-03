
````markdown
# ✅ Task API (ToDo List with Authentication)

A RESTful API built with **FastAPI** for personal task management. It allows user registration, login, task creation and management with **JWT-based authentication**. Perfect for learning CRUD operations, authentication, and API design.

---

## 🚀 Features

- User registration and login (JWT)
- Full CRUD for tasks (create, list, update, delete)
- Filter tasks by status (pending, done)
- Route protection with authentication
- Integration with SQLite or PostgreSQL database

---

## 📦 Technologies Used

- **Python 3.11+**
- **FastAPI**
- **Pydantic**
- **SQLite** (can be switched to PostgreSQL)
- **JWT Authentication (OAuth2)**
- **Uvicorn** (ASGI server)

---

## 🔐 Authentication Endpoints

### 📌 POST `/auth/register`

**Description:** Register a new user.

**Payload:**
```json
{
  "username": "anabelmo",
  "email": "ana@email.com",
  "password": "123456"
}
````

**Response:**

```json
{
  "message": "User successfully registered"
}
```

---

### 📌 POST `/auth/login`

**Description:** User login and JWT token generation.

**Payload:**

```json
{
  "email": "ana@email.com",
  "password": "123456"
}
```

**Response:**

```json
{
  "access_token": "<jwt_token_here>",
  "token_type": "bearer"
}
```

---

## 📋 Task Endpoints

> ⚠️ All endpoints below require JWT authentication via header:

```
Authorization: Bearer <access_token>
```

---

### 📌 POST `/tasks`

**Description:** Create a new task.

**Payload:**

```json
{
  "title": "Study FastAPI",
  "description": "Complete the lesson on authentication",
  "due_date": "2025-08-05T23:59:00",
  "status": "pending"
}
```

**Response:**

```json
{
  "id": 1,
  "title": "Study FastAPI",
  "description": "Complete the lesson on authentication",
  "due_date": "2025-08-05T23:59:00",
  "status": "pending",
  "owner_id": 1
}
```

---

### 📌 GET `/tasks`

**Description:** List all tasks of the authenticated user.

**Optional Query Parameter:**

```
/tasks?status=pending
```

**Response:**

```json
[
  {
    "id": 1,
    "title": "Study FastAPI",
    "description": "Complete the lesson on authentication",
    "due_date": "2025-08-05T23:59:00",
    "status": "pending"
  }
]
```

---

### 📌 GET `/tasks/{id}`

**Description:** Get details of a specific task.

**Response:**

```json
{
  "id": 1,
  "title": "Study FastAPI",
  "description": "Complete the lesson on authentication",
  "due_date": "2025-08-05T23:59:00",
  "status": "pending"
}
```

---

### 📌 PUT `/tasks/{id}`

**Description:** Update a task.

**Payload:**

```json
{
  "title": "Study FastAPI",
  "description": "Update the description",
  "due_date": "2025-08-06T12:00:00",
  "status": "done"
}
```

**Response:**

```json
{
  "message": "Task successfully updated"
}
```

---

### 📌 DELETE `/tasks/{id}`

**Description:** Delete a task.

**Response:**

```json
{
  "message": "Task successfully deleted"
}
```

---

## 🧠 What You'll Learn from This Project

* Building RESTful APIs with FastAPI
* JWT Authentication with OAuth2 Password Flow
* Data modeling and validation using Pydantic
* Full CRUD with protected routes
* Filters, query parameters, and user-based data management
* Practical database use (SQLite/PostgreSQL)

---

## ▶️ How to Run Locally

1. **Clone the repository:**

```bash
git clone https://github.com/yourusername/todo-api.git
cd todo-api
```

2. **Create a virtual environment and install dependencies:**

```bash
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

3. **Start the server:**

```bash
uvicorn main:app --reload
```

---

## 📄 License

This project is licensed under the MIT License. Feel free to use and modify it.

---

## 🙋‍♂️ Author

Developed by **Anabelmo Feijó** — passionate about technology, APIs, and practical solutions for everyday problems.

```