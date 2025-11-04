---
title: Management User API
description: Complete API reference for Channel Manager integrations
sidebar_position: 10
---

## 3. Create User API

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
