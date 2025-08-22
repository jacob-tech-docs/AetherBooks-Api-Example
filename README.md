# AetherBooks-Api-Example
API Example using a fictional AetherBooks api. 

# AetherBooks API Documentation

## 📚 Introduction

**AetherBooks** is a fictional REST API that allows developers to integrate digital book management and user checkout features into their Salesforce-connected applications. The API supports retrieving book metadata, managing user checkouts, and tracking loan history.

This documentation outlines the core features, authentication method, error handling, and best practices for using the AetherBooks API.

---

## 🌐 Base URL

All endpoints listed in this documentation are relative to this base URL.

---

## 🔐 Authentication

All requests must include an **OAuth 2.0 Bearer Token** in the `Authorization` header.

### Example:

Tokens are managed via your connected Salesforce org's OAuth app.

---

## ⚠️ Error Handling

The AetherBooks API uses standard HTTP status codes for errors. Responses include a JSON payload with more context.

| Status Code | Meaning             | Description                          |
|-------------|---------------------|--------------------------------------|
| 400         | Bad Request         | Malformed or missing parameters      |
| 401         | Unauthorized        | Invalid or missing auth token        |
| 404         | Not Found           | Resource not found                   |
| 429         | Too Many Requests   | Rate limit exceeded                  |
| 500         | Server Error        | Unexpected error on the server side  |

### Error Example:
```json
{
  "error": "Unauthorized",
  "message": "Missing or invalid token."
}


📘 Endpoints

1. Get All Books

Retrieve a paginated list of books available in the library.
	•	Method: GET
	•	URL: /books
	•	Headers:

Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json

Example Request:
GET /books?page=1&size=10 HTTP/1.1
Authorization: Bearer abc123

Example Response:
{
  "data": [
    {
      "id": "bk_001",
      "title": "Shadow over Etheria",
      "author": "Lina Veyra",
      "available": true
    },
    ...
  ],
  "pagination": {
    "page": 1,
    "size": 10,
    "totalPages": 5
  }
}

Possible Errors:
	•	401 Unauthorized
	•	429 Too Many Requests
