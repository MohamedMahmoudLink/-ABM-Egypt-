
# Task Manager API ABM Egypt

## Project Description
This project is a simple **Task Manager API** built using **Laravel** and **Sanctum** for authentication. It allows users to add, update, delete, and view tasks associated with their account. The API is secured using **Sanctum** for token-based authentication.

## Requirements

- **PHP** 8.0 or higher
- **Composer** 2.x or higher
- **Laravel** 11.x or higher
- **MySQL** or compatible database

## Installation Steps

### 1. Clone the Project

First, clone the project from the Git repository:

```bash
git clone https://github.com/MohamedMahmoudLink/-ABM-Egypt-.git
```

### 2. Install Dependencies

Navigate to the project folder and install the dependencies using **Composer**:

```bash
cd task-manager-api
composer install
```

### 3. Set Up the Environment

Copy the `.env.example` file to `.env`:

```bash
cp .env.example .env
```

Open the `.env` file and configure the database settings (`DB_*`) to match your environment.

### 4. Generate the Application Key

Generate the application key for Laravel:

```bash
php artisan key:generate
```

### 5. Set Up the Database

Ensure that your database exists, then run the migrations to create the necessary tables:

```bash
php artisan migrate
```

### 6. Install Sanctum

If Sanctum is not installed yet, install it via Composer:

```bash
composer require laravel/sanctum
```

Publish the Sanctum configuration:

```bash
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
```

## API Endpoints

### 1. **POST /api/register**
- **Description**: Register a new user.
- **Inputs**: `name`, `email`, `password`
- **Response**: The newly created user data along with the authentication token.

### 2. **POST /api/login**
- **Description**: Log in a user and receive an authentication token.
- **Inputs**: `email`, `password`
- **Response**: A token for the authenticated user.

### 3. **POST /api/logout**
- **Description**: Log out the user by invalidating the authentication token.
- **Response**: A success message.

### 4. **GET /api/tasks**
- **Description**: List all tasks for the logged-in user.
- **Response**: A list of tasks associated with the user.

### 5. **POST /api/tasks**
- **Description**: Create a new task.
- **Inputs**: `title`, `status` (pending, in-progress, completed)
- **Response**: The created task data.

### 6. **PUT /api/tasks/{task}**
- **Description**: Update an existing task.
- **Inputs**: `title`, `status`
- **Response**: The updated task data.

### 7. **DELETE /api/tasks/{task}**
- **Description**: Delete a task.
- **Response**: A success message or failure message.

---

## Authentication

The API uses **Sanctum** for authentication.

### How to Register

To register a new user, make a **POST** request to `/api/register` with the following data:

```json
{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123"
}
```

### How to Log In

Once registered, you can log in to your account by making a **POST** request to `/api/login` with the following data:

```json
{
    "email": "john@example.com",
    "password": "password123"
}
```

The response will include an authentication token. For example:

```json
{
    "token": "your_jwt_token_here"
}
```

### How to Access Protected Routes

For any protected route (e.g., creating, updating, or deleting tasks), you must pass the token in the **Authorization** header:

```plaintext
Authorization: Bearer your_jwt_token_here
```

Example of making a request to list tasks:

```bash
curl -X GET http://localhost/api/tasks -H "Authorization: Bearer your_jwt_token_here"

POSTMAN
```

---

## Troubleshooting

If you encounter any issues, feel free to check the [GitHub Issues](https://github.com/your-repository/task-manager-api/issues) or open a new issue for assistance.
