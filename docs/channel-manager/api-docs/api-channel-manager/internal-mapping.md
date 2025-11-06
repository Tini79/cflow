---
title: API Internal Mapping
description: Complete API reference for managing Internal Mapping through CRUD operations
sidebar_position: 13
---

# Internal Mapping API Endpoints

This page provides an overview of the available API endpoints for managing Internal Mapping through CRUD operations. It also specifies that all data handled in these endpoints originates from the PMS (Property Management System), ensuring synchronization between the PMS and the internal system.

## 1. Get Internal Mapping List

Retrieve internal mapping list.

**Endpoint:** `GET /GetInternalMappingList/{hotel_code}`

**Parameters:**

- `hotel_code`: Hotel code

**Example Request:**

```javascript
const axios = require("axios");

let config = {
  method: "get",
  maxBodyLength: Infinity,
  url: "https://cm.cakrasoft.net/cm/api/v2/GetInternalMappingList/CKR",
};

axios
  .request(config)
  .then((response) => {
    console.log("User list retrieved successfully");
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
      "hotel_code": "HTL9001",
      "cm_rate_plan_code": "RBFLEX01",
      "cm_rate_plan_name": "Room + Breakfast Flexible",
      "cm_room_type_code": "DLXKING",
      "cm_room_type_name": "Deluxe King Room",
      "id": 145,
      "id_internal_rate_plan": 201,
      "internal_rate_plan_code": "INT-RBFLEX01",
      "internal_rate_plan_name": "INTERNAL ROOM + BREAKFAST FLEX",
      "internal_room_type_code": "INT-DLX-K",
      "internal_room_type_name": "INTERNAL DELUXE KING",
      "is_static": 1,
      "created_at": "2025-06-15T10:22:10Z",
      "created_by": "AdminUser",
      "mapping_code": "RBFLEX01:INT-RBFLEX01",
      "updated_at": "2025-07-01T14:55:32Z",
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
- `cm_rate_plan_code`: The rate plan code from the Channel Manager.
- `cm_rate_plan_name`: The rate plan name from the Channel Manager.
- `cm_room_type_code`: The room type code from the Channel Manager.
- `cm_room_type_name`: The room type name from the Channel Manager.
- `id`: The unique ID of this mapping record.
- `id_internal_rate_plan`: The internal system ID of the rate plan.
- `internal_rate_plan_code`: The internal rate plan code.
- `internal_rate_plan_name`: The internal rate plan name.
- `internal_room_type_code`: The internal room type code.
- `internal_room_type_name`: The internal room type name.
- `is_static`: Indicates whether the mapping is static (0 = dynamic, 1 = static).
- `mapping_code`: The combined mapping code (Channel Manager code : Internal code).
- `created_at`: The timestamp indicating when the record was created.
- `created_by`: The user or system responsible for creating the record.
- `updated_at`: The timestamp indicating the latest update to the record.
- `updated_by`: The user who performed the most recent update.
- `pagination`: Pagination metadata for the specific result item (total, limit, page).

## 2. Get Internal Mapping By Code

Retrieve one internal mapping by code.

**Endpoint:** `GET /GetInternalMapping/{id}`

**Parameters:**

- `id`: Internal mapping id

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetInternalMapping/1'
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
    "hotel_code": "HTL2025",
    "cm_rate_plan_code": "RBLSUP01",
    "cm_rate_plan_name": "Room + Breakfast Super Saver",
    "cm_room_type_code": "SUPKING",
    "cm_room_type_name": "Super King Room",
    "id": 230,
    "id_internal_rate_plan": 502,
    "internal_rate_plan_code": "INT-RBLSUP01",
    "internal_rate_plan_name": "INTERNAL ROOM + BREAKFAST SUPER SAVER",
    "internal_room_type_code": "INT-SUP-K",
    "internal_room_type_name": "INTERNAL SUPER KING",
    "is_static": 1,
    "mapping_code": "RBLSUP01:INT-RBLSUP01",
    "created_at": "2025-06-20T09:15:42Z",
    "created_by": "AdminUser",
    "updated_at": "2025-07-02T11:23:10Z",
    "updated_by": "System"
  }
}
```

#### Response Field Details

**Result**: An object containing user record returned by the API.

- `hotel_code`: The unique code identifying the hotel.
- `cm_rate_plan_code`: The rate plan code from the Channel Manager.
- `cm_rate_plan_name`: The rate plan name from the Channel Manager.
- `cm_room_type_code`: The room type code from the Channel Manager.
- `cm_room_type_name`: The room type name from the Channel Manager.
- `id`: The unique ID of this mapping record.
- `id_internal_rate_plan`: The internal system ID of the mapped rate plan.
- `internal_rate_plan_code`: The internal rate plan code used by the PMS/system.
- `internal_rate_plan_name`: The internal rate plan name used by the PMS/system.
- `internal_room_type_code`: The internal room type code used by the PMS/system.
- `internal_room_type_name`: The internal room type name used by the PMS/system.
- `is_static`: Indicates whether the mapping is static (0 = dynamic, 1 = static).
- `mapping_code`: The combined mapping code (CM rate plan code : Internal rate plan code).
- `created_at`: The timestamp when this mapping record was created.
- `created_by`: The user or system that created this mapping record.
- `updated_at`: The timestamp when this mapping record was last updated.
- `updated_by`: The user or system that last updated this mapping record.

## 3. Create Internal Mapping API

Create a new internal mapping in the system.

**Endpoint:** `POST /InsertInternalMapping/{hotel_code}`

**Parameters:**

- `hotel_code`: Hotel code

**Request Body:**

```json
{
  "hotel_code": "HTL001",
  "internal_rate_plan_code": "INT-RBFAST01",
  "internal_rate_plan_name": "INTERNAL ROOM + FAST BREAKFAST",
  "cm_rate_plan_code": "RBFAST01",
  "cm_rate_plan_name": "Room + Fast Breakfast",
  "mapping_code": "RBFAST01:INT-RBFAST01"
}
```

#### Request Body Field Details

- `hotel_code`: The unique code identifying the hotel.
- `internal_rate_plan_code`: The internal rate plan code used by the PMS or internal system.
- `internal_rate_plan_name`: The internal rate plan name used by the PMS or internal system.
- `cm_rate_plan_code`: The rate plan code from the Channel Manager.
- `cm_rate_plan_name`: The rate plan name from the Channel Manager.
- `mapping_code`: The combined mapping reference (CM rate plan code : Internal rate plan code).

---

**Example Request:**

```javascript
const axios = require("axios");

let data = JSON.stringify({
  hotel_code: "HTL001",
  internal_rate_plan_code: "INT-RBFAST01",
  internal_rate_plan_name: "INTERNAL ROOM + FAST BREAKFAST",
  cm_rate_plan_code: "RBFAST01",
  cm_rate_plan_name: "Room + Fast Breakfast",
  mapping_code: "RBFAST01:INT-RBFAST01",
});

let config = {
  method: "post",
  maxBodyLength: Infinity,
  url: "https://cm.cakrasoft.net/cm/api/v2/InsertInternalMapping/CKR",
  headers: {
    "Content-Type": "application/json",
    token:
      "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0",
  },
  data: data,
};

axios
  .request(config)
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

## 4. Update Internal Mapping API

Update a internal mapping in the system.

**Endpoint:** `PUT /UpdateInternalMapping/{id}`

**Parameters:**

- `id`: Internal mapping id

**Request Body:**

```json
{
  "hotel_code": "HTL909",
  "internal_room_type_code": "INT-DLX-K",
  "internal_room_type_name": "INTERNAL DELUXE KING",
  "internal_rate_plan_code": "INT-RBSTD01",
  "internal_rate_plan_name": "INTERNAL ROOM + BREAKFAST STANDARD",
  "cm_room_type_code": "DLXKING",
  "cm_room_type_name": "Deluxe King Room",
  "cm_rate_plan_code": "RBSTD01",
  "cm_rate_plan_name": "Room + Breakfast Standard",
  "is_static": 0
}
```

#### Request Body Field Details

- `hotel_code`: The unique code identifying the hotel.
- `internal_room_type_code`: The internal room type code used by the PMS/internal system.
- `internal_room_type_name`: The internal room type name used by the PMS/internal system.
- `internal_rate_plan_code`: The internal rate plan code used by the PMS/internal system.
- `internal_rate_plan_name`: The internal rate plan name used by the PMS/internal system.
- `cm_room_type_code`: The room type code received from the Channel Manager.
- `cm_room_type_name`: The room type name received from the Channel Manager.
- `cm_rate_plan_code`: The rate plan code received from the Channel Manager.
- `cm_rate_plan_name`: The rate plan name received from the Channel Manager.
- `is_static`: Indicates whether the mapping is static (0 = dynamic, 1 = static).

---

**Example Request:**

```javascript
const axios = require("axios");

let data = JSON.stringify({
  hotel_code: "HTL909",
  internal_room_type_code: "INT-DLX-K",
  internal_room_type_name: "INTERNAL DELUXE KING",
  internal_rate_plan_code: "INT-RBSTD01",
  internal_rate_plan_name: "INTERNAL ROOM + BREAKFAST STANDARD",
  cm_room_type_code: "DLXKING",
  cm_room_type_name: "Deluxe King Room",
  cm_rate_plan_code: "RBSTD01",
  cm_rate_plan_name: "Room + Breakfast Standard",
  is_static: 0,
});

let config = {
  method: "put",
  maxBodyLength: Infinity,
  url: "https://cm.cakrasoft.net/cm/api/v2/UpdateInternalMapping/8",
  headers: {
    "Content-Type": "application/json",
    token:
      "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0",
  },
  data: data,
};

axios
  .request(config)
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

## 5. Reset Internal Mapping API

Reset a internal mapping in the system.

**Endpoint:** `PUT /ResetMapping/{id}`

**Parameters:**
- `id`: Internal mapping id

**Request Body:**

```json
{
  "internal_room_type_code": "INT-DLX-K",
  "internal_room_type_name": "INTERNAL DELUXE KING",
  "internal_rate_plan_code": "INT-RBSTD01",
  "internal_rate_plan_name": "INTERNAL ROOM + BREAKFAST STANDARD"
}
```

#### Request Body Field Details

- `internal_room_type_code`: The internal room type code used by the PMS/internal system.
- `internal_room_type_name`: The internal room type name used by the PMS/internal system.
- `internal_rate_plan_code`: The internal rate plan code used by the PMS/internal system.
- `internal_rate_plan_name`: The internal rate plan name used by the PMS/internal system.

---

**Example Request:**

```javascript
const axios = require("axios");

let data = JSON.stringify({
  internal_room_type_code: "INT-DLX-K",
  internal_room_type_name: "INTERNAL DELUXE KING",
  internal_rate_plan_code: "INT-RBSTD01",
  internal_rate_plan_name: "INTERNAL ROOM + BREAKFAST STANDARD",
});

let config = {
  method: "put",
  maxBodyLength: Infinity,
  url: "https://cm.cakrasoft.net/cm/api/v2/ResetMapping/8",
  headers: {
    "Content-Type": "application/json",
    token:
      "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0",
  },
  data: data,
};

axios
  .request(config)
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

## 6. Delete Internal Mapping

Delete a internal mapping.

**Endpoint:** `DELETE /DeleteInternalRatePlan/{id}`

**Parameters:**

- `id`: Internal mapping id to delete

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
