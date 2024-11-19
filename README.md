# Library Management API

This API allows interaction with a library database, providing functionalities for managing user authentication and database queries. Built with the Slim framework and uses JWT for secure communication.

---

## API Endpoints

### 1. **User Registration**

- **Endpoint**: `/user/register`
- **Method**: `POST`
- **Payload**:
  ```json
  {
    "username": "Andrew45",
    "password": "password"
  }
  ```
- **Response**:
  - **Success**:
    ```json
    {
      "status": "success",
      "data": null
    }
    ```
  - **Failure**:
    ```json
    {
      "status": "fail",
      "data": "Username already exists"
    }
    ```

### 2. **User Authentication**

- **Endpoint**: `/user/authenticate`
- **Method**: `POST`
- **Payload**:
  ```json
  {
    "username": "Andrew45",
    "password": "password"
  }
  ```
- **Response**:
  - **Success**:
    ```json
    {
      "status": "success",
      "token": "JWT_TOKEN",
      "data": null
    }
    ```
  - **Failure**:
    - Incorrect username or password:
      ```json
      {
        "status": "fail",
        "data": { "title": "Incorrect username/password" }
      }
      ```

### 3. **Update User Account**

- **Endpoint**: `/book-author/update`
- **Method**: `PUT`
- **Headers**:
  - `Authorization`: `Bearer JWT_TOKEN`
- **Payload**:
  ```json
  {
    "bookId": 20,
    "bookTitle": "Math",
    "authorId": 20,
    "authorName": "Andrew"
  }
  ```
- **Response**:
  - **Success**:
    ```json
    {
      "status": "success",
      "token": "NEW_JWT_TOKEN",
      "data": null
    }
    ```
  - **Failure**:
    - User not found or invalid input:
      ```json
      {
        "status": "fail",
        "data": "User not found"
      }
      ```

### 4. **Delete User Account**

- **Endpoint**: `/book-author/delete`
- **Method**: `DELETE`
- **Headers**:
  - `Authorization`: `Bearer JWT_TOKEN`
- **Payload**:
  ```json
  {
    "bookId": 20,
    "authorId": 20
  }
  ```
- **Response**:
  - **Success**:
    ```json
    {
      "status": "success",
      "data": "User account deleted"
    }
    ```
  - **Failure**:
    - User ID not provided or user not found:
      ```json
      {
        "status": "fail",
        "data": "User ID not provided / User not found"
      }
      ```

---

# Overview

## Libraries and Tools

- **Slim Framework**: Handles API routes.
- **JWT (JSON Web Token)**: Used for user authentication.

## Database Setup

- Contains database connection details such as:
  - Server name
  - Username
  - Password
- Connects to a **MySQL database**.

## Main Functions

1. **Connect to Database**:
   - Establishes a connection to the database using PDO.
2. **Create Tokens**:
   - Generates secure tokens for user identification.
   - Tokens expire after one hour.
3. **Token Handling**:
   - Likely includes functionality to validate or update tokens (not fully visible).

## App Setup

- Initializes the **Slim app**.
- Prepares the app for handling incoming requests.

---

# Things to Note

1. **Sensitive Info**:
   - Database details and JWT secrets are hardcoded.
   - **Recommendation**: Store sensitive information in environment variables.
2. **Expandable**:
   - This file provides the basic setup.
   - Additional routes or features can be added as needed.
