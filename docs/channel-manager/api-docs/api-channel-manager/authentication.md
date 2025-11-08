---
title: Authentication
description: Complete API reference for managing authentication on Channel Manager
sidebar_position: 3
---

# Authentication API Endpoints

Authentication endpoints such as login, registration, and password reset handle user credential management and account access. Depending on the specific endpoint, the request may require a `token` (sent in the token header), `Basic Authentication` (using credentials obtained from the PMS Connectivity menu), or `no authentication` at all. Each endpoint defines its own security requirements to ensure proper and secure account handling.

## 1. Create One Year Token

This API endpoint is used to issue a long-lived access token that allows a client or user to access protected API endpoints for up to one year without needing to repeatedly authenticate.

**Endpoint:** `POST /CreateOneYearTokenUser`

**Request Body:**

```json
{
  "username": "System",
  "password": "pasword123"
}
```

#### Request Body Field Details
- `username`: The identifier for the user account that is attempting to authenticate.
- `password`: The secret credential paired with the username to verify identity.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "username": "System",
  "password": "pasword123"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/CreateOneYearTokenUser',
  headers: {
    'Content-Type': 'application/json',
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

## 2. Login

The Login API is used to authenticate a user by validating their credentials.

**Endpoint:** `POST /Login`

**Request Body:**

```json
{
  "username": "System",
  "password": "pasword123"
}
```

#### Request Body Field Details
- `username`: The identifier for the user account that is attempting to authenticate.
- `password`: The secret credential paired with the username to verify identity.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "username": "System",
  "password": "pasword123"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/Login',
  headers: {
    'Content-Type': 'application/json',
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

## 3. Request to Change Password

This API endpoint is used to initiate the password-change process.
The user provides their registered email address, and the system sends a password-reset or change-password link/code to that email. This ensures that only the rightful owner of the account can proceed with updating their password.

**Endpoint:** `POST /ForgetPassword`

**Request Body:**

```json
{
  "username": "Ana",
}
```

#### Request Body Field Details
- `username`: The identifier for the user account that is attempting to authenticate.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "username": "Ana",
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/ForgetPassword',
  headers: {
    'Content-Type': 'application/json',
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

## 4. Check Access to Reset Password

This endpoint is used to verify the validity and expiration of a password reset link. The reset link contains a token, which must be provided in the request to this API.

**Endpoint:** `GET /CheckAccessToResetPass`

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/CheckAccessToResetPass',
  headers:{
    'Authorization': `Bearer ${token}`
  }
};

axios.request(config)
.then((response) => {
  console.log('Failed verify token');
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
  "Result": null
}
```

## 5. Confirm Reset Password

Reset the user’s password after the reset token has been verified.

**Endpoint:** `PUT /ConfirmForgetPassword`

**Request Body:**

```json
{
  "password": "newpassword123",
}
```

#### Request Body Field Details
- `password`: New password
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "password": "newpassword123",
});

let config = {
  method: 'put',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/ConfirmForgetPassword',
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

## 6. Change Password

This endpoint allows an authenticated user to update their password while logged in.

**Endpoint:** `POST /ChangePassword`

**Request Body:**

```json
{
  "username": "Admin",
  "old_password": "oldpassword123",
  "new_password": "newpassword123",
  "confirm_password": "newpassword123",
}
```

#### Request Body Field Details
- `username`: The identifier of the user account requesting the password change. This is typically the account currently logged in.
- `old_password`: The current password of the user.
- `new_password`: The new password the user wants to set.
- `confirm_password`: A repeat of the new password to ensure the user has typed it correctly.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "username": "Admin",
  "old_password": "oldpassword123",
  "new_password": "newpassword123",
  "confirm_password": "newpassword123",
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/ChangePassword',
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