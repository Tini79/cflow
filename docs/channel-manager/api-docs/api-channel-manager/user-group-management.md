---
title: API User Group Management
description: Complete API reference for managing User Group through CRUD operations
sidebar_position: 11
---

# User Group Management API Endpoints

This page provides an overview of the available API endpoints for managing User Group through CRUD operations.

## 1. Get User Group  List

Retrieve user group list.

**Endpoint:** `GET /GetUserGroupList`

**Query Parameters:**
- `Index`: The column index selected as the target for the query.
- `Text`: The text value used for filtering.

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUserGroupList'
};

axios.request(config)
.then((response) => {
  console.log('User group list retrieved successfully');
})
.catch((error) => {
  console.log(error);
});
```

**Example Response:**

```json
{
  "StatusCode": 0,
  "Message": "Success",
  "Result": [
    {
      "code": "S",
      "name": "System",
      "created_at": "2024-02-29T23:04:00Z",
      "created_by": "System",
      "updated_at": "0001-01-01T00:00:00Z",
      "updated_by": ""
    },
    {
      "code": "U",
      "name": "User",
      "created_at": "2024-03-04T13:00:38Z",
      "created_by": "admin123",
      "updated_at": "0001-01-01T00:00:00Z",
      "updated_by": ""
    }
  ]
}
```

#### Response Field Details
**Result**: An array containing user records returned by the API.
  - `code`: The identifier for the user group.
  - `name`: The display name of the user group.
  - `created_at`: The timestamp showing when the user account was created.
  - `created_by`: The user or system that created the account.
  - `updated_at`: The timestamp of the latest update.
  - `updated_by`: The user who last updated the account.

## 2. Get User Group By Code

Retrieve one user group by code.

**Endpoint:** `GET /GetUserGroupByCode/{user_group_code}`

**Parameters:**
- `user_group_code`: User group code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUserGroupByCode/S'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('User group retrieved successfully');
})
.catch((error) => {
  console.log(error);
});
```

**Example Response:**

```json
{
  "StatusCode": 0,
  "Message": "",
  "Result": {
    "code": "S",
    "name": "System",
  }
}
```

#### Response Field Details
**Result**: An object containing user record returned by the API.
  - `code`: The unique user identifier or username.
  - `name`: The user’s registered name.

## 3. Create User Group API

Register a new user group in the system.

**Endpoint:** `POST /InsertUserGroup`

**Request Body:**

```json
{    
  "code": "A",
  "name": "Admin",
}
```

#### Request Body Field Details
- `code`: Internal short code or identifier for the user record.
- `name`: The user’s registered name.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
    "code": "A",
    "name": "Admin",
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/InsertUserGroup',
  headers: {
    'Content-Type': 'application/json',
    'token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
  },
  data : data
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});
```

---

**Example Response:**

```json
{
  "StatusCode": 0,
  "Message": "Success",
  "Result": null
}
```

## 4. Update User API

Update a user group in the system.

**Endpoint:** `POST /UpdateUserGroup`

**Request Body:**

```json
{    
  "code": "A",
  "name": "Admin",
}
```

#### Request Body Field Details
- `code`: Internal short code or identifier for the user record.
- `name`: The user’s registered name.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({    
  "code": "A",
  "name": "Admin",
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/UpdateUserGroup',
  headers: {
    'Content-Type': 'application/json',
    'token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
  },
  data : data
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});
```

---

**Example Response:**

```json
{
  "StatusCode": 0,
  "Message": "Success",
  "Result": null
}
```

## 5. Delete User Group

Delete a user group.

**Endpoint:** `DELETE /DeleteUserGroup/{user_group_code}`

**Parameters:**
- `user_group_code`: User group code to delete

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/DeleteUserGroup/JONY'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('User group deleted successfully');
})
.catch((error) => {
  console.log(error);
});
```

---

**Example Response:**

```json
{
  "StatusCode": 0,
  "Message": "Success",
  "Result": null
}
```