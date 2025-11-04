---
title: API Room Types
description: Complete API reference for managing Room Types through CRUD operations
sidebar_position: 6
---

# Room Types API Endpoints

This page provides an overview of the available API endpoints for managing Room Types through CRUD operations.

## 1. Get Room Type List

Retrieve room type list.

**Endpoint:** `GET /GetRoomTypesList`

**Query Parameters:**
- `HotelCode`: Hotel code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetRoomTypesList?HotelCode=CKR'
};

axios.request(config)
.then((response) => {
  console.log('Room type list retrieved successfully');
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
      "hotel_code": "CKR",
      "room_type_code": "SIN KING",
      "name": "SIN KING",
      "ota_room_name": "SIN KING",
      "count_of_rooms": 10,
      "default_occupancy": 1,
      "occ_adults": 1,
      "occ_children": 0,
      "occ_infant": 0,
      "id": "",
      "room_type_id": "",
      "room_type_status": "",
      "created_by": "CM12",
      "created_at": "2025-08-13T10:33:58+08:00",
      "updated_by": "CM12",
      "updated_at": "2025-08-13T10:33:58+08:00"
    }
  ]
}
```

#### Response Field Details
**Result**: An array containing room type records returned by the API
  - `id`: Internal ID of the room type record.
  - `hotel_code`: A unique code used to identify the hotel within the system.
  - `room_type_code`: The internal system code representing the specific room type.
  - `name`: The internal display name of the room type.
  - `ota_room_name`: The room type name as shown on OTA (Online Travel Agency) platforms.
  - `count_of_rooms`: Total number of rooms available under this room type.
  - `default_occupancy`: The standard number of guests allowed for the room type.
  - `occ_adults`: Maximum number of adults allowed in the room.
  - `occ_children`: Maximum number of children allowed in the room.
  - `occ_infant`: Maximum number of infants allowed in the room.
  - `room_type_id`: Unique room type ID provided by Channex or channel manager for mapping.
  - `room_type_status`: Status of the room type mapping (M = mapped, N = not mapped).
  - `created_by`: User or system responsible for creating the record.
  - `created_at`: Timestamp when the room type record was created.
  - `updated_by`: User or system who last updated the record.
  - `updated_at`: Timestamp for the latest update of the record.

## 2. Get Room Type By Code

Retrieve one room type by code.

**Endpoint:** `GET /GetRoomType/{hotel_code}/{room_type_code}`

**Parameters:**
- `hotel_code`: Hotel code
- `room_type_code`: Room Type code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetRoomType/CKR/SGL'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Room Type retrieved successfully');
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
    "hotel_code": "CKR",
    "room_type_code": "SGL",
    "name": "Single Room",
    "ota_room_name": "Double Room",
    "count_of_rooms": 10,
    "default_occupancy": 2,
    "occ_adults": 2,
    "occ_children": 0,
    "occ_infant": 0,
    "id": "30",
    "room_type_id": "6cb0a7e0-b97e-4beb-bfaf-3d6fa4119391",
    "room_type_status": "M",
    "created_by": "",
    "created_at": "0001-01-01T00:00:00Z",
    "updated_by": "",
    "updated_at": "0001-01-01T00:00:00Z"
  }
}
```

#### Response Field Details
**Result**: An object containing room type records returned by the API.
  - `id`: Internal record ID of the room type in your system.
  - `hotel_code`: Unique code used to identify the hotel within the system.
  - `room_type_code`: Internal code representing the specific room type.
  - `name`: The internal or system name of the room type.
  - `ota_room_name`: The room type name as displayed on OTA platforms.
  - `count_of_rooms`: Total number of rooms available for this room type.
  - `default_occupancy`: Standard occupancy capacity for the room (total guests).
  - `occ_adults`: Maximum number of adults allowed for this room type.
  - `occ_children`: Maximum number of children allowed for this room type.
  - `occ_infant`: Maximum number of infants allowed for this room type.
  - `room_type_id`: Unique identifier for the room type provided by the channel manager.
  - `room_type_status`: Mapping status of the room type (M = mapped, N = not mapped/new).
  - `created_by`: The user or system who created the record.
  - `created_at`: Timestamp when the record was created.
  - `updated_by`: The user or system who last updated the record.
  - `updated_at`: Timestamp when the record was last updated.

## 3. Get Room Type Combolist

Retrieve room type combolist.

**Endpoint:** `GET /GetRoomTypeComboList`

**Query Parameters:**
- `HotelCode`: Hotel code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetRoomTypeComboList?HotelCode=CKR'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Room Type combolist retrieved successfully');
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
      "name": "Double Room",
      "code": "SGL",
      "room_type_id": "6cb0a7e0-b97e-4beb-bfaf-3d6fa4119391",
      "room_type_code": ""
    }
  ]
}
```

#### Response Field Details
**Rsult**: An object containing rate plan records returned by the API.
  - `name`: The display name of the room type used in the system.
  - `code`: The internal system code assigned to the room type.
  - `room_type_id`: The unique identifier associated with the room type in the system or channel manager.
  - `room_type_code`: An additional room type code used for mapping, categorization, or OTA integration.

## 4. Get Unlisted Room Type Combolist

Retrieve one room type by code.

**Endpoint:** `GET /GetUnlistedRoomTypeList`

**Query Parameters:**
- `HotelCode`: Unique code identifying the hotel.
- `OTARoomID`: Unique code identifying the hotel.

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUnlistedRoomTypeList?HotelCode=CKR&OTARoomID=6cb0a7e0-b97e-4beb-bfaf-3d6fa4119391'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Unlisted room type combolist retrieved successfully');
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
      "hotel_code": "",
      "room_type_code": "",
      "name": "Double Room",
      "ota_room_name": "",
      "count_of_rooms": 10,
      "default_occupancy": 2,
      "occ_adults": 2,
      "occ_children": 0,
      "occ_infant": 0,
      "id": "6cb0a7e0-b97e-4beb-bfaf-3d6fa4119391",
      "room_type_id": "",
      "room_type_status": "",
      "created_by": "",
      "created_at": "0001-01-01T00:00:00Z",
      "updated_by": "",
      "updated_at": "0001-01-01T00:00:00Z"
    }
  ]
}
```

#### Response Field Details
**Result**: An object containing unlisted room type records returned by the API.
  - `id`: Internal system ID referring to this room type record in your database.
  otel_code: Unique identifier for the hotel within the system.
  - `room_type_code`: System code representing the room type.
  - `name`: Internal name of the room type used within the system.
  - `ota_room_name`: Room type name displayed on OTA platforms.
  - `count_of_rooms`: Total number of rooms available under this room type.
  - `default_occupancy`: Standard number of guests allowed for this room type.
  - `occ_adults`: Maximum number of adults allowed.
  - `occ_children`: Maximum number of children allowed.
  - `occ_infant`: Maximum number of infants allowed.
  - `room_type_id`: Unique identifier from the channel manager for mapping (empty = not mapped).
  - `room_type_status`: Status indicating whether the room type is mapped (M) or not mapped (N).
  - `created_by`: The user or system that created this record.
  - `created_at`: Creation timestamp.
  - `updated_by`: The user or system who last updated this record.
  - `updated_at`: Last update timestamp.

## 5. Create Room Type

Create a new room type.

**Endpoint:** `POST /InsertRoomType`

**Request Body:**

```json
{
  "hotel_code": "CKR",
  "room_type_code": "KEFC",
  "name": "Keefe Cochran",
  "count_of_rooms": 12,
  "default_occupancy": 1,
  "occ_adults": 1,
  "occ_children": 0,
  "occ_infant": 0,
  "room_type_id": "",
  "room_type_status": "N",
  "username": "System"
}
```

#### Request Body Field Details
- `hotel_code`: A unique code used to identify the hotel within the system.
- `room_type_code`: A system-generated or assigned code used to uniquely identify the room type.
- `name`: The internal name of the room type as defined in the system.
- `count_of_rooms`: The total number of rooms available under this room type.
- `default_occupancy`: The standard number of guests allowed for this room type.
- `occ_adults`: Maximum number of adults allowed in the room.
- `occ_children`: Maximum number of children allowed in the room.
- `occ_infant`: Maximum number of infants allowed in the room.
- `room_type_id`: The unique identifier for the room type (empty if not yet mapped).
- `rate_plan_status`: Indicates the mapping status of the room type.
    - **"M"** → Mapped (already connected)
    - **"N"** → Not mapped / new property
- `username`: The user or system responsible for creating or modifying the room type.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_code": "CKR",
  "room_type_code": "KEFC",
  "name": "Keefe Cochran",
  "count_of_rooms": 12,
  "default_occupancy": 1,
  "occ_adults": 1,
  "occ_children": 0,
  "occ_infant": 0,
  "room_type_id": "",
  "room_type_status": "N",
  "username": "System"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/InsertRoomType',
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

## 6. Update Room Type

Update a room type.

**Endpoint:** `PUT /UpdateRoomType`

**Request Body:**

```json
{
  "id": "30",
  "hotel_code": "CKR",
  "room_type_code": "KEFC",
  "name": "Keefe Cochran",
  "count_of_rooms": 12,
  "default_occupancy": 1,
  "occ_adults": 1,
  "occ_children": 0,
  "occ_infant": 0,
  "room_type_id": "",
  "room_type_status": "N",
  "username": "System"
}
```

#### Request Body Field Details
- `id`: The internal identifier for this hotel record.
- `rate_plan_code`: A system-generated or assigned code used to uniquely identify the room type.
- `rate_plan_name`: The internal name of the room type as defined in the system.
- `hotel_code`: A unique code used to identify the hotel within the system.
- `username`: The user or system responsible for creating or modifying the room type.
- `inv_code`: The inventory or room code linked to the room type.
- `currency_code`: The currency used for the rate plan’s pricing (ISO 4217 format).
- `rate_plan_status`: Indicates the mapping status of the room type.
    - **"M"** → Mapped (already connected)
    - **"N"** → Not mapped / new property
- `occupancy`: The maximum number of guests allowed for this room type.
- `default_rate`: The base price of the room type when no additional pricing rules apply.

---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "id": "30",
  "hotel_code": "CKR",
  "room_type_code": "KEFC",
  "name": "Keefe Cochran",
  "count_of_rooms": 12,
  "default_occupancy": 1,
  "occ_adults": 1,
  "occ_children": 0,
  "occ_infant": 0,
  "room_type_id": "",
  "room_type_status": "N",
  "username": "System"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/UpdateRoomType',
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

## 7. Delete Room Type

Delete a room type.

**Endpoint:** `DELETE /DeleteRoomType/{hotel_code}/{room_type_code}`

**Parameters:**
- `hotel_code`: Hotel code to delete
- `room_type_code`: Room type code to delete

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/DeleteRoomType/CKR/SGL'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Room Type deleted successfully');
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

## 8. Delete Internal Room Type

Delete the mapping between PMS room type and the corresponding room type in Channex.

**Endpoint:** `DELETE /DeleteRoomTypeInternalOnly/{hotel_code}/{room_type_code}`

**Parameters:**
- `hotel_code`: Hotel code to delete
- `room_type_code`: Room type code to delete

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/DeleteRoomTypeInternalOnly/CKR/SGL'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Room Type deleted successfully');
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