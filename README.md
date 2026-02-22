# Fast-API-Tasks

**Fast-API-Tasks** is a web application created with Fast API for managing users and tasks.

### Requirements 🗒️

- Python 3.10.12. It is recommended to use [pyenv](https://github.com/pyenv/pyenv) to install the desired Python interpreter version more easily.
- Installation of libraries.
- A .env file created in the root directory with the environment variables.

---

### Architecture and Stack 🛠️

The architecture used is based on Clean Architecture, where the database and API layers are isolated from the business rules.
Main frameworks and libraries:

- FastAPI
- Pydantic
- SQLAlchemy

---

### Running the Code ⚙️

It is recommended to create a virtualenv to isolate the application dependencies. With the virtual environment created and activated, run the following command:

```jsx
pip install -r requirements.txt
```

---


### Main Commands 💻

To run the application locally on localhost:8000:

```jsx
python main.py
```

At http://localhost:8000/docs you can check the documentation of the existing endpoints.

To create the database tables:

```jsx
python create_tables.py
```


### Endpoints 🔄

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
