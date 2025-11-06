---
title: API Export File
description: Complete API reference for managing Export File
sidebar_position: 17
---

# Export Excel File API Endpoints

Used to export excel file on Cakrahub Channel Manager system.

**Endpoint:** `POST /ReadExcelFile`

**Request Body:**

```json
{
  "file": {
    "filename": "booking_data.xlsx",
    "type": "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
    "content": "UEsDBBQABgAIAAAAIQD...base64content..." 
  },
  "hotel_code": "HTL123"
}
```

#### Request Body Field Details
- `file`: The uploaded file object (e.g., CSV, Excel, or JSON) containing the data to be processed. Sent as multipart/form-data.
- `hotel_code`: The unique identifier of the hotel associated with the uploaded file. This helps the backend know which hotel the file belongs to.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "file": {
    "filename": "booking_data.xlsx",
    "type": "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
    "content": "UEsDBBQABgAIAAAAIQD...base64content..." 
  },
  "hotel_code": "HTL123"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/ReadExcelFile',
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