---
title: API Rate Plans
description: Complete API reference for managing Rate Plans through CRUD operations
sidebar_position: 5
---

# Rate Plans API Endpoints

This page provides an overview of the available API endpoints for managing Rate Plans through CRUD operations.

## 1. Get Rate Plan List

Retrieve rate plan list.

**Endpoint:** `GET /GetRatePlansList`

**Query Parameters:**
- `HotelCode`: Hotel code
- `PageNumber`: Hotel code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetRatePlansList?HotelCode=CKR&PageNumber=1'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Rate Plan list retrieved successfully');
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
      "rate_plan_name": "TESTING 6",
      "rate_plan_code": "TST6",
      "ota_rate_name": "TESTING 6",
      "inv_code": "JOYK",
      "currency_code": "IDR",
      "meal_type": "none",
      "occupancy": 2,
      "default_rate": "0.00",
      "hotel_code": "CKR",
      "id": "",
      "rate_plan_id": "",
      "room_type_id": "",
      "rate_plan_status": "",
      "created_by": "Channel Manager",
      "created_at": "2025-08-22T14:28:37+08:00",
      "updated_by": "CM12",
      "updated_at": "2025-08-22T14:28:37+08:00",
      "pagination": {
        "total": 0,
        "limit": 0,
        "page": 0
      }
    }
  ],
  "Pagination": {
    "total": 0,
    "limit": 0,
    "page": 0
  }
}
```

#### Response Field Details
**Result**: An array containing rate plan records returned by the API
  - `id`: Internal ID of the rate plan record.
  - `rate_plan_id`: Unique rate plan ID provided by the channel manager or external system.
  - `room_type_id`: Identifier of the room type associated with this rate plan.
  - `rate_plan_name`: The internal name of the rate plan used within the system.
  - `rate_plan_code`: Unique system code that identifies the rate plan.
  - `ota_rate_name`: The rate plan name displayed on OTA channels.
  - `inv_code`: Inventory or room code associated with this rate plan.
  - `currency_code`: Currency used for this rate plan (ISO 4217 format, e.g., IDR).
  - `meal_type`: Indicates the meal inclusion type for the rate plan.
  - `occupancy`: Maximum number of guests allowed for this rate plan.
  - `default_rate`: The base or initial price set for the rate plan.
  - `hotel_code`: Identifier of the hotel to which this rate plan belongs.
  - `rate_plan_status`: Status of the rate plan.
    - **"M"** = Mapped
    - **"N"** = Not mapped / New
  - `created_by`: Indicates who created the rate plan record.
  - `created_at`: Timestamp showing when the record was created.
  - `updated_by`: The user or system that last updated the rate plan.
  - `updated_at`: Timestamp showing when the record was last updated.
  - `pagination`: Pagination metadata for the specific result item (total, limit, page).

## 2. Get Rate Plan By Code

Retrieve one rate plan by code.

**Endpoint:** `GET /GetRatePlan/{hotel_code}/{room_type_code}/{rate_plan_code}`

**Parameters:**
- `hotel_code`: Hotel code
- `room_type_code`: Room Type code
- `rate_plan_code`: Rate Plan code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetRatePlan/CKR/JOYQ/HM'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Rate Plan retrieved successfully');
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
  "Result": {
    "rate_plan_name": "Free Free",
    "rate_plan_code": "HM",
    "ota_rate_name": "",
    "inv_code": "JOYQ",
    "currency_code": "IDR",
    "meal_type": "none",
    "occupancy": 3,
    "default_rate": "100000.00",
    "hotel_code": "",
    "id": "61",
    "rate_plan_id": "acc4b93e-ffcb-4e5a-b6d2-11322e9629ed",
    "room_type_id": "a39bd4ed-a421-46ff-a9a0-a594d176f3bf",
    "rate_plan_status": "M",
    "created_by": "",
    "created_at": "2025-02-14T10:35:22+08:00",
    "updated_by": "admin_user",
    "updated_at": "2025-02-14T10:35:22+08:00",
    "pagination": {
      "total": 0,
      "limit": 0,
      "page": 0
    }
  }
}
```

#### Response Field Details
**Result**: An object containing rate plan records returned by the API.
  - `rate_plan_name`: The internal name of the rate plan.
  - `rate_plan_code`: Unique code used to identify this rate plan.
  - `ota_rate_name`: The rate plan name used on OTA platforms (empty if not mapped).
  - `inv_code`: The inventory/room code linked to this rate plan.
  - `currency_code`: Currency used for the rate (ISO 4217).
  - `meal_type`: Indicates the type of meal included with the rate plan.
  - `occupancy`: Maximum number of guests allowed under this rate plan.
  - `default_rate`: The base/default price for the rate plan.
  - `hotel_code`: Code of the hotel this rate plan belongs to (empty if not mapped).
  - `id`: Internal ID of the rate plan record inside your system.
  - `rate_plan_id`: Unique rate plan ID from the channel manager.
  - `room_type_id`: The unique ID of the room type associated with this rate plan.
  - `rate_plan_status`: Mapping status of the rate plan.
    - **"M"** = Mapped
    - **"N"** = Not mapped / New
  - `created_by`: The user or system that created the record (empty if unknown or system-generated).
  - `created_at`: Timestamp when the record was created.
  - `updated_by`: The user or system that last updated the record.
  - `updated_at`: Timestamp of the last update.
  - `pagination`: Pagination metadata for this result object:
  - `total`: Total number of items
  - `limit`: Items per page
  - `page`: Current page number

## 3. Get Unlisted Rate Plan Combolist

Retrieve one rate plan by code.

**Endpoint:** `GET /GetUnlistedRatePlanList`

**Query Parameters:**
- `HotelCode`: Unique code identifying the hotel.
- `OTARateID`: Unique ID of the rate plan provided by Channex.
- `RoomTypeID`: Unique ID of the associated room type provided by Channex.

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUnlistedRatePlanList?HotelCode=CKR&OTARateID=&RoomTypeID=6cb0a7e0-b97e-4beb-bfaf-3d6fa4119391'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Unlisted rate plan combolist retrieved successfully');
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
      "rate_plan_name": "Standard Flexible",
      "rate_plan_code": "STDFLX",
      "ota_rate_name": "Standard Flexible Rate",
      "inv_code": "DLX01",
      "currency_code": "IDR",
      "meal_type": "none",
      "occupancy": 3,
      "default_rate": "750000.00",
      "hotel_code": "HTL001",
      "id": "91",
      "rate_plan_id": "efdf9c50-e751-4633-b868-108b93c29641",
      "room_type_id": "a39bd4ed-a421-46ff-a9a0-a594d176f3bf",
      "rate_plan_status": "M",
      "created_by": "admin_user",
      "created_at": "2025-02-15T09:42:11+08:00",
      "updated_by": "admin_user",
      "updated_at": "2025-02-15T09:42:11+08:00",
      "pagination": {
          "total": 1,
          "limit": 10,
          "page": 1
      }
    }
  ]
}
```

#### Response Field Details
**Result**: An object containing unlisted rate plan records returned by the API.
  - `id`: Internal system ID referring to this rate plan record in your database.
  - `rate_plan_id`: Unique rate plan identifier provided by the channel manager (e.g., Channex) for mapping and synchronization.
  - `room_type_id`: ID of the room type associated with this rate plan.
  - `rate_plan_name`: The name of the rate plan as used internally in the system. Usually the display name visible to hotel staff.
  - `rate_plan_code`: A system-generated or manually assigned code that uniquely identifies the rate plan.
  - `ota_rate_name`: The name of the rate plan as displayed on OTA platforms. This may differ from the internal name depending on channel requirements.
  - `inv_code`: Inventory or room code associated with this rate plan. Used to link the rate plan to a room type in the channel manager or OTA.
  - `currency_code`: The currency used for pricing in this rate plan (ISO 4217 format, e.g., IDR, USD, EUR).
  - `meal_type`: Specifies the meal inclusion for this rate plan.
  - `occupancy`: Maximum number of guests allowed under this rate plan.
  - `default_rate`: The base or starting price for the rate plan. Often used when no dynamic pricing is set.
  - `hotel_code`: Unique code representing the hotel associated with this rate plan.
  - `rate_plan_status`: Indicates mapping status of the rate plan.
    - **"M"** → Mapped / Connected
    - **"N"** → Not mapped / New
  - `created_by`: Identifier of the user or system process that created the record.
  - `created_at`: Timestamp for when this rate plan was created (ISO 8601 format).
  - `updated_by`: The user or system that last updated the record.
  - `updated_at`: Timestamp for the most recent update to this rate plan.
  - `pagination`: Metadata describing pagination for the response:
    - `total`: Total number of items
    - `limit`: Maximum items allowed per page
    - `page`: Current page number

## 4. Create Rate Plan

Create a new rate plan.

**Endpoint:** `POST /InsertRatePlan`

**Request Body:**

```json
{
  "rate_plan_code": "DBH ",
  "rate_plan_name": "Deborah Harvey",
  "hotel_code": "CKR",
  "username": "System",
  "inv_code": "JOYQ",
  "currency_code": "BRL",
  "rate_plan_status": "N",
  "occupancy": 1,
  "default_rate": 0,
}
```

#### Request Body Field Details
- `rate_plan_code`: A system-generated or assigned code used to uniquely identify the rate plan.
- `rate_plan_name`: The internal name of the rate plan as defined in the system.
- `hotel_code`: A unique code used to identify the hotel within the system.
- `username`: The user or system responsible for creating or modifying the rate plan.
- `inv_code`: The inventory or room code linked to the rate plan.
- `currency_code`: The currency used for the rate plan’s pricing (ISO 4217 format).
- `rate_plan_status`: Indicates the mapping status of the rate plan.
    - **"M"** → Mapped (already connected)
    - **"N"** → Not mapped / new property
- `occupancy`: The maximum number of guests allowed for this rate plan.
- `default_rate`: The base price of the rate plan when no additional pricing rules apply.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "rate_plan_code": "DBH",
  "rate_plan_name": "Deborah Harvey",
  "hotel_code": "CKR",
  "username": "System",
  "inv_code": "JOYQ",
  "currency_code": "BRL",
  "rate_plan_status": "N",
  "occupancy": 1,
  "default_rate": 0,
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/InsertRatePlan',
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

## 5. Update Rate Plan

Update a rate plan.

**Endpoint:** `PUT /UpdateRatePlan`

**Request Body:**

```json
{
  "id": "19",
  "rate_plan_code": "DBH",
  "rate_plan_name": "Deborah Harvey",
  "hotel_code": "CKR",
  "username": "System",
  "inv_code": "JOYQ",
  "currency_code": "BRL",
  "rate_plan_status": "N",
  "occupancy": 0,
  "default_rate": 0,
}
```

#### Request Body Field Details
- `id`: The internal identifier for this hotel record.
- `rate_plan_code`: A system-generated or assigned code used to uniquely identify the rate plan.
- `rate_plan_name`: The internal name of the rate plan as defined in the system.
- `hotel_code`: A unique code used to identify the hotel within the system.
- `username`: The user or system responsible for creating or modifying the rate plan.
- `inv_code`: The inventory or room code linked to the rate plan.
- `currency_code`: The currency used for the rate plan’s pricing (ISO 4217 format).
- `rate_plan_status`: Indicates the mapping status of the rate plan.
    - **"M"** → Mapped (already connected)
    - **"N"** → Not mapped / new property
- `occupancy`: The maximum number of guests allowed for this rate plan.
- `default_rate`: The base price of the rate plan when no additional pricing rules apply.

---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "id": "19",
  "rate_plan_code": "DBH",
  "rate_plan_name": "Deborah Harvey",
  "hotel_code": "CKR",
  "username": "System",
  "inv_code": "JOYQ",
  "currency_code": "BRL",
  "rate_plan_status": "N",
  "occupancy": 0,
  "default_rate": 0,
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/UpdateRatePlan',
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

## 6. Delete Rate Plan

Delete a rate plan.

**Endpoint:** `DELETE /DeleteRatePlan/{hotel_code}/{room_type_code}/{rate_plan_code}`

**Parameters:**
- `hotel_code`: Hotel code to delete
- `room_type_code`: Room type code to delete
- `rate_plan_code`: Rate plan code to delete

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/DeleteRatePlan/CKR/JOYQ/HM'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Rate Plan deleted successfully');
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

## 7. Delete Internal Rate Plan

Delete the mapping between PMS rate plan and the corresponding rate plan in Channex.

**Endpoint:** `DELETE /DeleteRatePlanInternalOnly/{hotel_code}/{room_type_code}/{rate_plan_code}`

**Parameters:**
- `hotel_code`: Hotel code to delete
- `room_type_code`: Room type code to delete
- `rate_plan_code`: Rate plan code to delete

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/DeleteRatePlanInternalOnly/CKR/JOYQ/HM'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Rate Plan deleted successfully');
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