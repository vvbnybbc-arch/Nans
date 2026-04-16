# API Documentation

## Overview
This API provides access to various functionalities of the Nans system. 

## Base URL
All requests are made to `https://api.nans.example.com/v1`. 

## Authentication

### Method
The API requires token-based authentication. Obtain your API key from the developer portal and include it in the headers of your requests.

### Header Example
```http
Authorization: Bearer YOUR_API_KEY
```

## Endpoints

### 1. Get User Information
- **Endpoint:** `/user`
- **Method:** `GET`
- **Description:** Retrieve information about the currently authenticated user.
- **Response Example:**
  ```json
  {
    "id": 1,
    "username": "user123",
    "email": "user@example.com"
  }
  ```

### 2. Update User Information
- **Endpoint:** `/user`
- **Method:** `PUT`
- **Description:** Update information for the authenticated user.
- **Request Body Example:**
  ```json
  {
    "email": "newemail@example.com"
  }
  ```
- **Response Example:**
  ```json
  {
    "success": true,
    "message": "User information updated successfully."
  }
  ```

### 3. List All Items
- **Endpoint:** `/items`
- **Method:** `GET`
- **Description:** Retrieve a list of all items.
- **Response Example:**
  ```json
  [
    {
      "id": 1,
      "name": "Item 1"
    },
    {
      "id": 2,
      "name": "Item 2"
    }
  ]
  ```

### 4. Create a New Item
- **Endpoint:** `/items`
- **Method:** `POST`
- **Description:** Create a new item.
- **Request Body Example:**
  ```json
  {
    "name": "New Item"
  }
  ```
- **Response Example:**
  ```json
  {
    "success": true,
    "item": {
      "id": 3,
      "name": "New Item"
    }
  }
  ```

### 5. Delete an Item
- **Endpoint:** `/items/{id}`
- **Method:** `DELETE`
- **Description:** Delete an item by ID.
- **Response Example:**
  ```json
  {
    "success": true,
    "message": "Item deleted successfully."
  }
  ```

## Usage Examples
### cURL Example for Getting User Information
```bash
curl -H "Authorization: Bearer YOUR_API_KEY" https://api.nans.example.com/v1/user
```

### cURL Example for Creating a New Item
```bash
curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{ "name": "New Item" }' https://api.nans.example.com/v1/items
```

## Best Practices
- Always use HTTPS to ensure data is encrypted in transit.
- Use pagination when retrieving large sets of data to avoid performance issues.
- Keep your API keys secret and do not expose them in client-side code.
- Monitor your API usage to stay within any limits set by the API provider.