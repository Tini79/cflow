---
title: API User Connectivity
description: Complete API reference for managing User connectivity through CRUD operations
sidebar_position: 14
---

# User Connectivity API Endpoints

This page provides an overview of the available API endpoints for managing User Connectivity through CRUD operations.

## 1. Get User Connectivity List

Retrieve user connectivity list.

**Endpoint:** `GET /GetUserConnectivityList`

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUserConnectivityList',
  headers:{
    'Authorization': `Bearer ${token}`
  }
};

axios.request(config)
.then((response) => {
  console.log('User Connectivity list retrieved successfully');
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
      "id": 1,
      "hotel_code": "CKR",
      "username": "Admin",
      "password": "admin123456",
      "created_at": "2024-11-11T22:08:56Z",
      "created_by": "SYSTEM",
      "updated_at": "2024-11-11T14:10:49Z",
      "updated_by": ""
    }
  ]
}
```

#### Response Field Details
**Result**: An array containing user connectivity records returned by the API.
  - `id`: The internal identifier for this user connectivity record.
  - `hotel_code`: The code identifying which hotel this user belongs to.
  - `username`: The authentication username used by the PMS when establishing a connection to the Cakrahub Channel Manager backend.
  - `password`: The authentication password paired with the PMS username, used to securely authorize every request sent from the PMS to the Cakrahub Channel Manager backend.
  - `created_at`: Timestamp indicating when the hotel record was created (ISO 8601 format).
  - `created_by`: The user or system that created the record.
  - `updated_at`: Timestamp indicating when the user connectivity record was last updated.
  - `updated_by`: The user who last updated the record.

## 2. Get User Connectivity By Id

Retrieve one user connectivity by id.

**Endpoint:** `GET /GetUserConnectivity/{id}`

**Parameters:**
- `id`: user Connectivity id

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUserConnectivity/1',
  headers:{
    'Authorization': `Bearer ${token}`
  }
};

axios.request(config)
.then((response) => {
  console.log('User Connectivity retrieved successfully');
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
    "id": 1,
    "hotel_code": "CKR",
    "username": "Admin",
    "password": "admin123456",
    "created_at": "2024-11-11T22:08:56Z",
    "created_by": "SYSTEM",
    "updated_at": "2024-11-11T14:10:49Z",
    "updated_by": ""
  }
}
```

#### Response Field Details
**Result**: An object containing hotel/user connectivity record returned by the API.
  - `id`: Internal identifier for this user connectivity record in your system.
  - `hotel_code`: The code identifying which hotel this user belongs to.
  - `username`: The authentication username used by the PMS when establishing a connection to the Cakrahub Channel Manager backend.
  - `password`: The authentication password paired with the PMS username, used to securely authorize every request sent from the PMS to the Cakrahub Channel Manager backend.
  - `created_at`: Timestamp indicating when the hotel record was created (ISO 8601 format).
  - `created_by`: The user or system that created the record.
  - `updated_at`: Timestamp indicating when the user connectivity record was last updated.
  - `updated_by`: The user who last updated the record.

## 3. Create User Connectivity

Create a new user connectivity.

**Endpoint:** `POST /InsertUserConnectivity`

**Request Body:**

```json
{
  "hotel_code": "CKR",
  "username": "Admin",
  "password": "admin123456",
}
```

#### Request Body Field Details
- `hotel_code`: A unique code used to identify the hotel within the system.
- `username`: The authentication username used by the PMS when establishing a connection to the Cakrahub Channel Manager backend.
- `password`: The authentication password paired with the PMS username, used to securely authorize every request sent from the PMS to the Cakrahub Channel Manager backend.
  
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_code": "CKR",
  "username": "Admin",
  "password": "admin123456",
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/InsertUserConnectivity',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${token}`
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

## 4. Update User Connectivity

Update a user connectivity.

**Endpoint:** `PUT /UpdateUserConnectivity`

**Request Body:**

```json
{
  "id": 1,
  "hotel_code": "CKR",
  "username": "Admin",
  "password": "admin123456",
}
```

#### Request Body Field Details
- `id`: The internal identifier for this hotel record.
- `hotel_code`: A unique code used to identify the hotel within the system.
- `username`: The authentication username used by the PMS when establishing a connection to the Cakrahub Channel Manager backend.
- `password`: The authentication password paired with the PMS username, used to securely authorize every request sent from the PMS to the Cakrahub Channel Manager backend.

---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "id": 1,
  "hotel_code": "CKR",
  "username": "Admin",
  "password": "admin123456",
});

let config = {
  method: 'put',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/UpdateUserConnectivity',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${token}`
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

## 5. Set New User Connectivity

This is used by the PMS to update its API credentials for connecting to the Cakrahub Channel Manager backend. The PMS provides its current credentials and a new password to securely replace the old one, ensuring continued authenticated access.

**Endpoint:** `POST /SetNewUserConnectivity`

**Request Body:**

```json
{
  "hotel_code": "HTL9001",
  "username": "pms_connection",
  "old_password": "OldPass123!",
  "new_password": "NewSecurePass456!"
}
```

#### Request Body Field Details
- `hotel_code`: The unique identifier of the hotel requesting the password update.
- `username`: The PMS username associated with the connection to the Cakrahub Channel Manager backend. This is used to authenticate the PMS client.
- `old_password`: The current password used by the PMS to authenticate with the Cakrahub backend. This is required to verify that the password change request is valid.
- `new_password`: The new password that will replace the old one. This will be used for future authentication between the PMS and the Cakrahub backend.
  
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_code": "HTL9001",
  "username": "pms_connection",
  "old_password": "OldPass123!",
  "new_password": "NewSecurePass456!"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/SetNewUserConnectivity',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${token}`
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

## 6. Delete User Connectivity

Delete a user connectivity.

**Endpoint:** `DELETE /DeleteUserConnectivity/{id}`

**Parameters:**
- `id`: User connectivity id

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/DeleteUserConnectivity/1',
  'Authorization': `Bearer ${token}`
};

axios.request(config)
.then((response) => {
  console.log('User Connectivity deleted successfully');
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