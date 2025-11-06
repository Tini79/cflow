---
title: API Management User
description: Complete API reference for managing User through CRUD operations
sidebar_position: 10
---

# Management User API Endpoints

This page provides an overview of the available API endpoints for managing User through CRUD operations.

## 1. Get User List

Retrieve user list.

**Endpoint:** `GET /GetUserList`

**Query Parameters:**
- `Index`: The column index selected as the target for the query.
- `Text`: The text value used for filtering.

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUserList'
};

axios.request(config)
.then((response) => {
  console.log('User list retrieved successfully');
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
      "code": "JONY",
      "email": "jony@mail.com",
      "is_active": 1,
      "user_group_code": "S",
      "created_at": "2025-02-10T09:13:55Z",
      "created_by": "system",
      "updated_at": "0001-01-01T00:00:00Z",
      "updated_by": "",
    }
  ]
}
```

#### Response Field Details
**Result**: An array containing user records returned by the API.
  - `code`: The unique user identifier or username.
  - `email`: The user’s registered email address.
  - `is_active`: Indicates whether the user account is active (1 = active, 0 = inactive).
  - `user_group_code`: The role or group assigned to the user.
  - `created_at`: The timestamp showing when the user account was created.
  - `created_by`: The user or system that created the account.
  - `updated_at`: The timestamp of the latest update.
  - `updated_by`: The user who last updated the account.

## 2. Get User By Code

Retrieve one user by code.

**Endpoint:** `GET /GetUserByCode/{user_code}`

**Parameters:**
- `user_code`: User code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUserByCode/JONY'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('User retrieved successfully');
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
    "code": "JONY",
    "email": "jony@mail.com",
    "id": 32,
    "is_active": 1,
    "password": "user_password",
    "user_api_key": "user_api_key",
    "user_group_code": "S"
  }
}
```

#### Response Field Details
**Result**: An object containing user record returned by the API.
  - `code`: The unique user identifier or username.
  - `email`: The user’s registered email address.
  - `id`: The internal numeric ID assigned to the user.
  - `is_active`: Indicates whether the user account is active (1 = active, 0 = inactive).
  - `password`: The user’s stored password value.
  - `user_api_key`: The API key assigned to the user for system access.
  - `user_group_code`: The role or user group classification.

## 3. Get User Group Combolist

Retrieve user group combolist.

**Endpoint:** `GET /GetUserGroupComboList`

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUserGroupComboList'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('User group combolist retrieved successfully');
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
        "name": "System"
    },
    {
        "code": "U",
        "name": "User"
    }
  ]
}
```

#### Response Field Details
**Result**: An object containing hotel/property records returned by the API.
  - `code`: The identifier of the user group.
  - `name`: The display name or description of the user group.


## 4. Create User API

Register a new user account in the system.

**Endpoint:** `POST /Register`

**Request Body:**

```json
{
  "code": "geqeqiwif",
  "email": "hodefa@mailinator.com",
  "password": "TvqjdB3Vy8dE59BrNX4rFA==",
  "user_api_key": "Pa$$w0rd!",
  "is_active": 0,
  "user_group_code": "S"
}
```

#### Request Body Field Details
- `code`: Internal short code or identifier for the user record.
- `email`: User's email address used for login.
- `password`: The user credential value.
- `user_api_key`: API key assigned to the user for programmatic access. Sensitive token used to authenticate API requests on behalf of the user.
- `is_active`: Numeric flag indicating whether the account is active.
  - **1** = active/enabled
  - **0** = inactive/disabled.
- `user_group_code`: Code representing the user’s group or role. Used to determine permissions and access levels inside the application.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
    "code": "geqeqiwif",
    "email": "hodefa@mailinator.com",
    "password": "TvqjdB3Vy8dE59BrNX4rFA==",
    "user_api_key": "Pa$$w0rd!",
    "is_active": 0,
    "user_group_code": "S"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/Register',
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

## 5. Update User API

Update a user account in the system.

**Endpoint:** `POST /UpdateUser`

**Request Body:**

```json
{
  "id": 21,
  "email": "marketing@mail.com",
  "is_active": 1,
  "password": "old_password",
  "user_api_key": "user_api_key",
  "user_group_code": "U",
}
```

#### Request Body Field Details
- `id`: The internal identifier for the user record.
- `email`: User's email address used for login.
- `password`: The user credential value.
- `user_api_key`: API key assigned to the user for programmatic access. Sensitive token used to authenticate API requests on behalf of the user.
- `is_active`: Numeric flag indicating whether the account is active.
  - **1** = active/enabled
  - **0** = inactive/disabled.
- `user_group_code`: Code representing the user’s group or role. Used to determine permissions and access levels inside the application.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "id": 21,
  "email": "marketing@mail.com",
  "is_active": 1,
  "password": "old_password",
  "user_api_key": "user_api_key",
  "user_group_code": "U",
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/UpdateUser',
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

## 6. Delete User

Delete a user.

**Endpoint:** `DELETE /DeleteUser/{user_code}`

**Parameters:**
- `user_code`: User code to delete

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/DeleteUser/JONY'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('User deleted successfully');
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