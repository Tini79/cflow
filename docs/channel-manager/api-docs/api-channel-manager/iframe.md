---
title: API IFrame
description: Complete API reference for generating IFrame
sidebar_position: 15
---

# IFrame and Webhook API Endpoints

This page provides an overview of the available API endpoints for generating IFrame .

## 1. Generate Iframe

Generate Iframe.

**Endpoint:** `POST /GenerateIFrame`


**Request Body:**

```json
{
  "module": "bookings",
  "hotel_code": "CKR"
}
```

#### Request Body Field Details
- `module`: Specifies the module name associated with the request or data.
- `hotel_code`: The unique code identifying the hotel.

```javascript
const axios = require('axios');

let data = JSON.stringify({
    "module": "bookings",
    "hotel_code": "CKR"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GenerateIFrame',
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
  "Result": "https://app.channex.io/auth/exchange?oauth_session_key=83b7efa3-f184-4396-a7f7-443fa6edb9a0&app_mode=headless&redirect_to=/bookings&property_id=9be07265-0dcd-452e-a946-4403645231ca"
}
```