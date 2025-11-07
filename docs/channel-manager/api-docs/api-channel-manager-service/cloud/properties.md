---
title: API Properties
description: Complete API reference for managing Properties through CRUD operations
sidebar_position: 3
---

# Properties API Documentation

This page provides an overview of the available API endpoints for managing Properties through CRUD operations.

## 1. Get Property List

Retrieve property list.

**Endpoint:** `GET /GetPropertyList`

**Query Parameters:**
- `IsActive`: Indicates whether the hotel/property is active. This field can be used as a filter when searching for properties.
  - Value: 1 = active, 0 = inactive.

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/GetPropertyList',
  headers:{
    'Authorization': `Basic ${token}`
  }
};

axios.request(config)
.then((response) => {
  console.log('Property list retrieved successfully');
})
.catch((error) => {
  console.log(error);
});
```

## 2. Get Property By Id

Retrieve one property by code.

**Endpoint:** `GET /GetProperty/{id}`

**Parameters:**
- `id`: Hotel/property id

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/GetProperty/1',
    headers:{
    'Authorization': `Basic ${token}`
  }
};

axios.request(config)
.then((response) => {
  console.log('Property retrieved successfully');
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

---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
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
})

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/InsertProperties',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Basic ${token}`
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

## 3. Create Property

Create a property.

**Endpoint:** `POST /InsertProperties`

**Request Body:**

```json
{
  "hotel_id": "MCH003",
  "unit_code": "U01",
  "hotel_code": "MM1064",
  "hotel_name": "Green Valley Hotel",
  "username": "GVHCH003",
  "password": "GreenValley#12",
  "WSDL": "https://cm.cakrasoft.net/cm/api/v1",
  "vendor": "CKHU",
  "type_code": "CM",
  "is_active": 1,
  "interval": 20
}
```

#### Request Body Field Details
- `hotel_id`: Unique identifier for the hotel in the system.
- `unit_code`: Optional code for a specific unit or sub-property. Can be empty if not applicable.
- `hotel_code`: Official hotel code used by the channel manager.
- `hotel_name`: Full name of the hotel or property.
- `username`: Username for authentication with the channel manager service.
- `password`: Password for authentication with the channel manager service.
- `WSDL`: URL endpoint of the channel manager API.
- `vendor`: Vendor code representing the channel manager provider.
- `type_code`: Type of integration..
- `is_active`: Indicates whether the property is active. Can be used as a filter.
  - Value: 1 = active, 0 = inactive.
- `interval`: Sync interval in minutes for data updates between the property and the channel manager (integer).

---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_id": "MCH003",
  "unit_code": "U01",
  "hotel_code": "MM1064",
  "hotel_name": "Green Valley Hotel",
  "username": "GVHCH003",
  "password": "GreenValley#12",
  "WSDL": "https://cm.cakrasoft.net/cm/api/v1",
  "vendor": "CKHU",
  "type_code": "CM",
  "is_active": 1,
  "interval": 20
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/InsertProperties',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Basic ${token}`
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

## 4. Update Property

Update a property.

**Endpoint:** `PUT /UpdateProperties/{id}`

**Parameters:**
- `id`: Hotel/property id

**Request Body:**

```json
{
  "hotel_id": "MCH003",
  "unit_code": "U01",
  "hotel_code": "MM1064",
  "hotel_name": "Green Valley Hotel",
  "username": "GVHCH003",
  "password": "GreenValley#12",
  "WSDL": "https://cm.cakrasoft.net/cm/api/v1",
  "vendor": "CKHU",
  "type_code": "CM",
  "is_active": 1,
  "interval": 20
}
```

#### Request Body Field Details
- `hotel_id`: Unique identifier for the hotel in the system.
- `unit_code`: Optional code for a specific unit or sub-property. Can be empty if not applicable.
- `hotel_code`: Official hotel code used by the channel manager.
- `hotel_name`: Full name of the hotel or property.
- `username`: Username for authentication with the channel manager service.
- `password`: Password for authentication with the channel manager service.
- `WSDL`: URL endpoint of the channel manager API.
- `vendor`: Vendor code representing the channel manager provider.
- `type_code`: Type of integration..
- `is_active`: Indicates whether the property is active. Can be used as a filter.
  - Value: 1 = active, 0 = inactive.
- `interval`: Sync interval in minutes for data updates between the property and the channel manager (integer).

---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_id": "MCH003",
  "unit_code": "U01",
  "hotel_code": "MM1064",
  "hotel_name": "Green Valley Hotel",
  "username": "GVHCH003",
  "password": "GreenValley#12",
  "WSDL": "https://cm.cakrasoft.net/cm/api/v1",
  "vendor": "CKHU",
  "type_code": "CM",
  "is_active": 1,
  "interval": 20
});

let config = {
  method: 'put',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/UpdateProperties/1',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Basic ${token}`
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

## 5. Activate/Deactivate Property API 

Update a property active status in the system.

**Endpoint:** `PUT /UpdateIsActive/{id}`

**Parameters:**
- `id`: Hotel/property id

**Request Body:**

```json
{
  "is_active": 1,
}
```

#### Request Body Field Details
- `is_active`: Indicates whether the property is active. Can be used as a filter.
  - Value: 1 = active, 0 = inactive.

---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "is_active": 1,
});

let config = {
  method: 'put',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/UpdateIsActive/1',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Basic ${token}`
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

## 6. Delete Property

Delete a property.

**Endpoint:** `DELETE /DeleteProperties/{id}`

**Parameters:**
- `id`: Hotel/property id

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/1',
  headers:{
    'Authorization': `Bearer ${token}`
  }
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