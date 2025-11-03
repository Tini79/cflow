---
title: API Properties
description: Complete API reference for managing Properties through CRUD operations
sidebar_position: 3
---

# Properties API Documentation

This page provides an overview of the available API endpoints for managing Properties through CRUD operations.

## 1. Get Property List

Retrieve property list.

**Endpoint:** `GET /GetPropertiesList/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetPropertiesList/Drune'
};

axios.request(config)
.then((response) => {
  console.log('Property list retrieved successfully');
})
.catch((error) => {
  console.log(error);
});
```

## 2. Get Property By Code

Retrieve one property by code.

**Endpoint:** `GET /GetPropertyByCode/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetPropertyByCode/Drune'
};

axios.request(config)
.then((response) => {
  console.log('Property list retrieved successfully');
})
.catch((error) => {
  console.log(error);
});
```

### 3. Create Property

Create a new property.

**Endpoint:** `POST /InsertProperties`

**Request Body:**

```json
{
  "hotel_id": "MRTNSH001",
  "unit_code": "UT010",
  "hotel_code": "MRTN2001",
  "hotel_name": "Martinez Hotel & Suites",
  "username": "MRTNSH_api",
  "password": "Mrtz#2024!",
  "WSDL": "https://cm.cakrasoft.net/cm/api/v2",
  "vendor": "CKHU",
  "type_code": "CM",
  "is_active": 1,
  "interval": 15
}
```

#### Request Body Field Details
- `hotel_id`: Unique identifier for the hotel within the system.
- `unit_code`: Code representing the specific unit, building, or property subdivision (if applicable).
- `hotel_code`: The official code assigned to the hotel, typically used for internal mapping or external integrations.
- `hotel_name`: The full name of the hotel as registered in the system.
- `username`: Username used for API authentication when connecting to the hotel’s Channel Manager.
- `password`: Password associated with the API authentication credentials.
- `WSDL`: Endpoint URL or WSDL address used to establish the integration connection with the Channel Manager.
- `vendor`: Code representing the Channel Manager vendor or provider being used.
- `type_code`: Indicates the type of connection or integration (e.g., "CM" for Channel Manager).
- `is_active`: Flag indicating whether the API connectivity for this property is active (1) or inactive (0).
- `interval`: Time interval (in minutes) used for synchronization, polling, or scheduled API checks.

