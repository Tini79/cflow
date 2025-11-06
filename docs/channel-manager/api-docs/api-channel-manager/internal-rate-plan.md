---
title: API Internal Rate Plan
description: Complete API reference for managing Internal Rate Plan through CRUD operations
sidebar_position: 11
---

# Internal Rate Plan API Endpoints

This page provides an overview of the available API endpoints for managing Internal Rate Plan through CRUD operations. It also specifies that all data handled in these endpoints originates from the PMS (Property Management System), ensuring synchronization between the PMS and the internal system.

## 1. Get Internal Rate Plan  List

Retrieve internal rate plan list.

**Endpoint:** `GET /GetInternalRatePlanList/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code

**Query Parameters:**
- `Index`: The column index selected as the target for the query.
- `Text`: The text value used for filtering.

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetInternalRatePlanList'
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
      "hotel_code": "HTL567",
      "id": 121,
      "rate_plan_code": "RBFXDELX",
      "rate_plan_name": "ROOM BREAKFAST FLEXIBLE DELUXE",
      "room_code": "DLX#KING:RBFXDELX",
      "room_name": "DELUXE KING ROOM BREAKFAST FLEXIBLE",
      "room_occupancy": 3,
      "room_type_code": "DLX#KING",
      "room_type_name": "DELUXE KING",
      "created_at": "2025-06-15T10:22:19Z",
      "created_by": "System",
      "updated_at": "2025-06-20T14:55:02Z",
      "updated_by": "System"
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
**Result**: An array containing user records returned by the API.
  - `hotel_code`: The unique code identifying the hotel.
  - `id`: The internal ID assigned to this room–rate plan mapping.
  - `rate_plan_code`: The code of the rate plan linked to this room type.
  - `rate_plan_name`: The full name or description of the rate plan.
  - `room_code`: A combined code representing the room type and rate plan.
  - `room_name`: The full descriptive name of the room and rate plan.
  - `room_occupancy`: Maximum number of guests allowed in the room.
  - `room_type_code`: The code representing the room type.
  - `room_type_name`: The display name of the room type.
  - `created_at`: The timestamp indicating when the record was created.
  - `created_by`: The user or system responsible for creating the record.
  - `updated_at`: The timestamp indicating the latest update to the record.
  - `updated_by`: The user who performed the most recent update.
  - `pagination`: Pagination metadata for the specific result item (total, limit, page).

## 2. Get Internal Rate Plan By Code

Retrieve one internal rate plan by code.

**Endpoint:** `GET /GetInternalRatePlan/{id}`

**Parameters:**
- `id`: Internal rate plan id

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetInternalRatePlan/1'
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
    "hotel_code": "HTL900",
    "cm_rate_plan_code": "RBFXSUP",
    "cm_rate_plan_name": "Room Breakfast Flexible Superior",
    "id": 152,
    "rate_plan_code": "RBFXSUP",
    "rate_plan_name": "ROOM BREAKFAST FLEXIBLE SUPERIOR",
    "room_code": "SUP#KING:RBFXSUP",
    "room_name": "SUPERIOR KING ROOM BREAKFAST FLEXIBLE",
    "room_occupancy": 3,
    "room_type_code": "SUP#KING",
    "room_type_name": "SUPERIOR KING",
    "created_at": "2025-06-10T09:15:22Z",
    "created_by": "System",
    "updated_at": "2025-06-12T14:40:18Z",
    "updated_by": "System"
  }
}
```

#### Response Field Details
**Result**: An object containing user record returned by the API.
  - `hotel_code`: Unique code identifying the hotel.
  - `cm_rate_plan_code`: The rate plan code received from the Channel Manager (CM).
  - `cm_rate_plan_name`: The name of the rate plan coming from the CM.
  - `id`: Internal system ID for this rate-plan mapping.
  - `rate_plan_code`: The internal rate plan code stored in the system.
  - `rate_plan_name`: The internal descriptive name of the rate plan.
  - `room_code`: Combined code representing the room type and rate plan.
  - `room_name`: Full descriptive name of the room type and the attached rate plan.
  - `room_occupancy`: Maximum allowed guests for the room.
  - `room_type_code`: Internal code representing the room type.
  - `room_type_name`: Display name of the room type.
  - `created_at`: Timestamp of when the record was created.
  - `created_by`: The user who created the record.
  - `updated_at`: Timestamp of the last modification.
  - `updated_by`: The user who last updated the record.

## 3. Get Rate Plan Combolist by Room Type

Retrieve rate plan combolist by room type.

**Endpoint:** `GET /GetRatePlanComboListByRoomType`

**Query Parameters:**
- `HotelCode`: Identifies the hotel associated with the currently logged-in user.
- `RoomTypeCode`: Identifies the room type linked to the currently logged-in user or the room type being referenced in the request.

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetRatePlanComboListByRoomType?HotelCode=CKR&RoomTypeCode=HM'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Property combolist retrieved successfully');
})
.catch((error) => {
  console.log(error);
});
```

**Example Response:**

```json
[
  {
    "name": "Deluxe King",
    "code": "DLX-KING",
    "title": "Deluxe King Room Type",
    "room_type_id": "RT-00123",
    "room_type_code": "DLX#KING"
  }
]
```

#### Response Field Details
**Result**: An object containing hotel/property records returned by the API.
  - `code`: The unique code associated with the item; often used as the value stored or processed in the system.
  - `title`: Additional descriptive text or label that provides more context about the item.
  - `room_type_id`: Internal system ID referencing the room type related to this item.
  - `room_type_code`: The internal or PMS room-type code associated with this item.

## 4. Create Internal Rate Plan API

Create a new internal rate plan in the system.

**Endpoint:** `POST /InsertInternalRatePlan/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code

**Request Body:**

```json
{
  "hotel_code": "HTL900",
  "id_internal_rate_plan": 4501,
  "internal_room_type_code": "DLX#KING",
  "internal_room_type_name": "Deluxe King",
  "internal_rate_plan_code": "RBFXDLX",
  "internal_rate_plan_name": "Room Breakfast Flexible Deluxe",
  "mapping_code": "MAP-DLX-RBFX"
}
```

#### Request Body Field Details
- `hotel_code`: The unique code identifying the hotel where this mapping belongs.
- `id_internal_rate_plan`: The internal system ID of the rate plan.
- `internal_room_type_code`: The internal code representing the room type.
- `internal_room_type_name`: The display name of the internal room type.
- `internal_rate_plan_code`: The internal code representing the rate plan.
- `internal_rate_plan_name`: The display name of the internal rate plan.
- `mapping_code`: A unique code representing the mapping between the room type and the rate plan.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_code": "HTL900",
  "id_internal_rate_plan": 4501,
  "internal_room_type_code": "DLX#KING",
  "internal_room_type_name": "Deluxe King",
  "internal_rate_plan_code": "RBFXDLX",
  "internal_rate_plan_name": "Room Breakfast Flexible Deluxe",
  "mapping_code": "MAP-DLX-RBFX"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/InsertInternalRatePlan',
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

Update a internal rate plan in the system.

**Endpoint:** `POST /UpdateInternalRatePlan/{id}`

**Parameters:**
- `id`: Internal rate plan id

**Request Body:**

```json
{
  "internal_room_type_code": "DLX#KING",
  "internal_room_type_name": "Deluxe King",
  "internal_rate_plan_code": "RBFXDLX",
  "internal_rate_plan_name": "Room Breakfast Flexible Deluxe",
  "room_type_code": "CM-DLX-KING",
  "room_type_name": "Deluxe King CM",
  "cm_rate_plan_code": "CM-RBFX-DLX",
  "cm_rate_plan_name": "CM Room Breakfast Flexible Deluxe",
  "mapping_code": "MAP-DLX-RBFX-001"
}
```

#### Request Body Field Details
- `internal_room_type_code`: The internal room type code stored in the PMS.
- `internal_room_type_name`: The display name of the room type in the PMS.
- `internal_rate_plan_code`: The internal rate plan code defined in the PMS.
- `internal_rate_plan_name`: The display name of the rate plan in the PMS.
- `room_type_code`: The room type code coming from the Channel Manager.
- `room_type_name`: The room type name as defined in the Channel Manager.
- `cm_rate_plan_code`: The rate plan code coming from the Channel Manager.
- `cm_rate_plan_name`: The rate plan name as defined in the Channel Manager.
- `mapping_code`: A unique identifier used to link (map) PMS internal room types & rate plans to their corresponding CM room types & rate plans.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "internal_room_type_code": "DLX#KING",
  "internal_room_type_name": "Deluxe King",
  "internal_rate_plan_code": "RBFXDLX",
  "internal_rate_plan_name": "Room Breakfast Flexible Deluxe",
  "room_type_code": "CM-DLX-KING",
  "room_type_name": "Deluxe King CM",
  "cm_rate_plan_code": "CM-RBFX-DLX",
  "cm_rate_plan_name": "CM Room Breakfast Flexible Deluxe",
  "mapping_code": "MAP-DLX-RBFX-001"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/UpdateInternalRatePlan',
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

## 5. Delete Internal Rate Plan

Delete a internal rate plan.

**Endpoint:** `DELETE /DeleteInternalRatePlan/{id}`

**Parameters:**
- `id`: Internal rate plan id to delete

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/DeleteInternalRatePlan/8'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Property deleted successfully');
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