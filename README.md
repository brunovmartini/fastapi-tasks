# FastAPI Tasks

**FastAPI Tasks** is a web application created with FastAPI for managing users and tasks.

### Requirements 🗒️

- Python 3.10.12. It’s recommended to use [pyenv](https://github.com/pyenv/pyenv) to easily install the desired Python version.
- A `.env` file created at the project root containing the required environment variables.
- Docker compose installed.

---

### Architecture ⚙️

The architecture used is based on Clean Architecture, where the database and API layers are isolated from the business rules.

---

### Stack 🛠️

Main frameworks and libraries:

- FastAPI
- Pydantic
- SQLAlchemy

---

### Application 💻

It is recommended to create a virtualenv to isolate the application dependencies. With the virtual environment created and activated, run the following command:

```jsx
pip install -r requirements.txt
```

Start the docker container with the following command:
```jsx
docker compose up -d
```

To create or update the database schema:

```jsx
alembic upgrade head
```

To run the application locally on localhost:8000:

```jsx
python main.py
```

---

### Documentation ️📖

At http://localhost:8000/docs you can check the documentation of the existing endpoints.

---

### Endpoints 🌐

**POST /users/signup**

Creates a new user.

Request Body
```jsx
{
  "email": "user@example.com",
  "name": "string",
  "last_name": "string",
  "password": "string"
}
```

Successful Response

```jsx
{
  "id": 0,
  "email": "user@example.com",
  "name": "string",
  "last_name": "string"
}
```

---

**POST /users/login**

Logs in the user.


Request body in Form-data
```jsx
"username": "user@example.com"
"password": "string"
```

Successful Response

```jsx
{
  "id": 0,
  "email": "user@example.com",
  "name": "string",
  "last_name": "string",
  "access_token": "string",
  "token_type": "string"
}
```
---

**GET /users/{user_id}**

Returns the data of a user.

Successful Response

```jsx
{
  "id": 0,
  "email": "user@example.com",
  "name": "string",
  "last_name": "string"
}
```

---

**GET /users/logged**

Returns the data of the logged-in user.

Authorization
```jsx
{
    'Authorization': 'Bearer {token}'
}
```

Successful Response

```jsx
{
  "id": 0,
  "email": "user@example.com",
  "name": "string",
  "last_name": "string",
  "access_token": "string",
  "token_type": "string"
}
```

---

**GET /tasks/{task_id}**

Returns the data of a specific task.

Successful Response

```jsx
{
  "id": 0,
  "title": "string",
  "description": "string",
  "user_id": 0
}
```

---

**GET /tasks**

Returns the tasks of the logged-in user.

Authorization
```jsx
{
    'Authorization': 'Bearer {token}'
}
```

Successful Response

```jsx
[
  {
    "id": 0,
    "title": "string",
    "description": "string",
    "user_id": 0
  }
]
```

---

**POST /tasks**

Creates a task and links it to the logged-in user.

Authorization
```jsx
{
    'Authorization': 'Bearer {token}'
}
```

Request Body
```jsx
{
  "title": "string",
  "description": "string"
}
```

Successful Response

```jsx
[
  {
    "id": 0,
    "title": "string",
    "description": "string",
    "user_id": 0
  }
]
```

---

**PUT /tasks/{task_id}**

Edits a task of the logged-in user.

Authorization
```jsx
{
    'Authorization': 'Bearer {token}'
}
```

Request Body
```jsx
{
  "title": "string",
  "description": "string"
}
```

Successful Response

```jsx
[
  {
    "id": 0,
    "title": "string",
    "description": "string",
    "user_id": 0
  }
]
```

---

**DELETE /tasks/{task_id}**

Deletes a task of the logged-in user.

Authorization
```jsx
{
    'Authorization': 'Bearer {token}'
}
```
