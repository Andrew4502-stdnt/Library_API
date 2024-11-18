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

# Notes

- **Environment Variables**: Sensitive information such as database credentials and JWT secret keys should be stored in environment variables to enhance security.
- **Error Handling**: The API provides meaningful error messages to help with debugging and user feedback. Ensure proper error handling is implemented on the client side.
- **Rate Limiting**: Implement rate limiting to protect the API from abuse and ensure fair usage among all users.
- **CORS Configuration**: Configure Cross-Origin Resource Sharing (CORS) appropriately to control which domains can access the API.
- **Logging**: Maintain logs of API requests and errors to monitor usage patterns and troubleshoot issues effectively.
- **Data Validation**: All incoming data should be validated to prevent SQL injection, XSS attacks, and other security vulnerabilities.
- **Testing**: Regularly perform unit and integration tests to ensure the API endpoints function as expected and maintain reliability.
- **Documentation**: Keep the API documentation up-to-date with any changes to endpoints, payloads, or responses to ensure developers have accurate information.
