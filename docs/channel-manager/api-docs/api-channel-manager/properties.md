---
title: API Properties
description: Complete API reference for managing Properties through CRUD operations
sidebar_position: 4
---

# Properties API Endpoints

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

**Example Response:**

```json
{
  "StatusCode": 0,
  "Message": "Success",
  "Result": [
    {
      "state": "",
      "address": "Omnis et ut laborios",
      "country_code": "AU",
      "hotel_name": "Maite Mann",
      "hotel_code": "Illum voluptatem do",
      "ota_hotel_name": "Maite Mann",
      "currency_code": "GTQ",
      "email": "",
      "city": "",
      "phone_number": "+1 (379) 834-3328",
      "min_stay_type": "through",
      "zip_code": "28281",
      "group_name": "User Group",
      "user_api_key": "",
      "is_cc": "0",
      "is_bcc": "0",
      "is_directly": "1",
      "id": "",
      "emails": null,
      "created_at": "2025-11-04T10:18:47+08:00",
      "created_by": "System",
      "updated_at": "2025-11-04T10:18:47+08:00",
      "updated_by": ""
    }
  ]
}
```

#### Response Field Details
**Result**: An array containing hotel/property records returned by the API.
  - `id`: The internal identifier for this hotel record.
  - `state`: The state or province where the hotel is located.
  - `address`: The full street address of the hotel.
  - `country_code`: The country of the hotel using the ISO 3166-1 alpha-2 code (e.g., AU, US, ID).
  - `hotel_name`: The registered name of the hotel within the system.
  - `hotel_code`: A unique identifier or code for the hotel property.
  - `ota_hotel_name`: The hotel name as displayed on OTA platforms (e.g., Booking.com, Agoda).
  - `currency_code`: The currency used by the hotel for transactions or reservations (ISO 4217 format).
  - `email`: The primary email address of the hotel (if provided).
  - `city`: The city where the hotel is located.
  - `phone_number`: The official phone number of the hotel.
  - `min_stay_type`: Defines how the minimum stay rules apply.
    - **"arrival"** → Minimum stay applies based on arrival date.
    - **"through"** → Minimum stay applies across the entire stay period.
  - `zip_code`: Postal or ZIP code of the hotel's location.
  - `group_name`: Name of the user group associated with the hotel or integration context.
  - `user_api_key`: API key associated with the hotel, provided by the channel manager (e.g., Channex) for authentication and integration.
  - `is_cc`: Indicates if CC email notifications are enabled.
    - **"1"** → enabled
    - **"0"** → disabled
  - `is_bcc`: Indicates if BCC email notifications are enabled.
    - **"1"** → enabled
    - **"0"** → disabled
  - `is_directly`: Indicates whether the configuration is set directly (no intermediary).
    - **"1"** → direct integration
    - **"0"** → through another system
  - `emails`: A list of additional email addresses associated with the hotel.
  - `created_at`: Timestamp indicating when the hotel record was created (ISO 8601 format).
  - `created_by`: The user or system that created the record (e.g., "System").
  - `updated_at`: Timestamp indicating when the hotel record was last updated.
  - `updated_by`: The user who last updated the record (empty if no update user is tracked).

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
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Property retrieved successfully');
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
    "state": "Riau",
    "address": "Komplek Ruko Nagoya Hill Blok I No. 10-16, Jl. Teuku Umar No.10, Kota, Kec. Lubuk Baja, Kota Batam, Kepulauan Riau 29444",
    "country_code": "ID",
    "property_name": "Alltrue Lite Batam",
    "name": "Alltrue Lite Batam",
    "property_type": "hotel",
    "currency_code": "IDR",
    "emails": null,
    "city": "Batam",
    "phone_number": "(0778) 7430488",
    "website": "https://alltruelitebatam.chsres.com",
    "zip_code": "29444",
    "user_api_key": "AjX+ttCJ6052EobW6e+aA11r/+gAWCXhaIH/YsXTOv/5BcV2BQoYrf7RbSoXOhlhhSja3Lz60lOUWrWwq2XJASYGUv4lhKKfTQgBMR7NfME=",
    "property_status": "M",
    "is_cc": "0",
    "is_bcc": "0",
    "is_directly": "0",
    "property_id": "1d9a27a8-3ea0-4e33-b5c5-d77b0c41b3dc",
    "id": "28"
  }
}
```

#### Response Field Details
**Result**: An object containing hotel/property record returned by the API.
  - `id`: Internal identifier for this property record in your system.
  - `property_id`: Unique property ID assigned by Channex.
  - `state`: The state or province where the property is located.
  - `address`: The full street address of the property.
  - `country_code`: Country code using ISO 3166-1 alpha-2 format (ID for Indonesia).
  - `property_name`: The official property name as registered in the system.
  - `name`: Display name of the property (usually same as property_name).
  - `property_type`: Type of property (e.g., hotel, apartment, villa).
  - `currency_code`: Currency used for transactions (ISO 4217, e.g., IDR).
  - `emails`: Additional property email list (null if not provided).
  - `city`: City where the property is located.
  - `phone_number`: Property contact number.
  - `website`: Official website URL of the property.
  - `zip_code`: Postal/ZIP code of the property location.
  - `user_api_key`: API key provided by Channex for integration and authentication.
  - `property_status`: Mapping status of the property:
    - **"M"** → Mapped (already connected)
    - **"N"** → Not mapped / new property
  - `is_cc`: Indicates if CC email notifications are enabled.
    - **"1"** → enabled
    - **"0"** → disabled
  - `is_bcc`: Indicates if BCC email notifications are enabled.
    - **"1"** → enabled
    - **"0"** → disabled
  - `is_directly`: Indicates whether the configuration is set directly (no intermediary).
    - **"1"** → direct integration
    - **"0"** → through another system

## 3. Get Property Combolist

Retrieve property combolist.

**Endpoint:** `GET /GetPropertyComboList/{user_group_code}`

**Parameters:**
- `user_group_code`: Indicates the group or role of the currently logged-in user

**Query Parameters:**
- `Username`: The name or identifier of the user currently logged into the system. It represents the account performing the action.
- `IsGeneral`: Indicates whether the user is considered a general-level user with broader access to data.
- `IsEdit`: A boolean flag that indicates whether the user has editing privileges.

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetPropertyComboList/S?Username=System&IsGeneral=true&IsEdit=false'
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
{
  "StatusCode": 0,
  "Message": "Success",
  "Result": [
    {
      "name": "Maite Mann",
      "code": "Illum voluptatem do",
      "currency_code": "GTQ"
    },
    {
      "name": "All Properties",
      "code": "All",
      "currency_code": "GTQ"
    }
  ]
}
```

#### Response Field Details
**Result**: An object containing hotel/property records returned by the API.
  - `name`: The display name of the property or group of properties.
  - `code`: The unique code representing the property.
  - `currency_code`: The currency code associated with the property (ISO 4217 format).

## 4. Get Unlisted Property Combolist

Retrieve unlisted property combolist.

**Endpoint:** `GET /GetUnlistedPropertyList`

**Query Parameters:**
- `OTAPropertyID`: A unique property identifier provided by Channex. This ID represents the hotel within the Channex channel manager system and is used for mapping, syncing availability, rates, and inventory.

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetUnlistedPropertyList?OTAPropertyID=c4e540c0-40d8-44ff-9842-e87e08440973'
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NjIyNDE1NDQsInVzZXIiOiJDTSBURUFNIn0.W-JJ1uXJ9hvNyZVYZVoRLmuZoJ_zS4YEtx-VZwJEtm0'
};

axios.request(config)
.then((response) => {
  console.log('Unlisted property combolist retrieved successfully');
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
      "state": "California",
      "address": "742 Evergreen Terrace, Springfield",
      "country_code": "US",
      "hotel_name": "Fuguy",
      "hotel_code": "FUG-0001",
      "ota_hotel_name": "Fuguy Hotel",
      "currency_code": "USD",
      "email": "info@fuguyhotel.com",
      "city": "Springfield",
      "phone_number": "+1-310-555-0147",
      "min_stay_type": "arrival",
      "zip_code": "90210",
      "group_name": "Operations",
      "user_api_key": "api_AjXttCJ6052EobW6e_aA11r_examplekey",
      "is_cc": "0",
      "is_bcc": "0",
      "is_directly": "1",
      "id": "b6561a4d-3b72-45b4-9cd5-5e52ded052f5",
      "emails": [
        "info@fuguyhotel.com",
        "reservations@fuguyhotel.com"
      ],
      "created_at": "2025-11-04T10:18:47+08:00",
      "created_by": "admin_user",
      "updated_at": "2025-11-04T10:18:47+08:00",
      "updated_by": "admin_user"
    }
  ]
}
```

#### Response Field Details
**Result**: An object containing unlisted hotel records returned by the API.
  - `state`: The state or province where the hotel is located.
  - `address`: The full street address of the hotel.
  - `country_code`: The country of the hotel using the ISO 3166-1 alpha-2 code (e.g., AU, US, ID).
  - `hotel_name`: The registered name of the hotel within the system.
  - `hotel_code`: A unique identifier or code for the hotel property.
  - `ota_hotel_name`: The hotel name as displayed on OTA platforms (e.g., Booking.com, Agoda).
  - `currency_code`: The currency used by the hotel for transactions or reservations (ISO 4217 format).
  - `email`: The primary email address of the hotel (if provided).
  - `city`: The city where the hotel is located.
  - `phone_number`: The official phone number of the hotel.
  - `min_stay_type`: Defines how the minimum stay rules apply.
    - **"arrival"** → Minimum stay applies based on arrival date.
    - **"through"** → Minimum stay applies across the entire stay period.
  - `zip_code`: Postal or ZIP code of the hotel's location.
  - `group_name`: Name of the user group associated with the hotel or integration context.
  - `user_api_key`: API key associated with the hotel, provided by the channel manager (e.g., Channex) for authentication and integration.
  - `is_cc`: Indicates if CC email notifications are enabled.
    - **"1"** → enabled
    - **"0"** → disabled
  - `is_bcc`: Indicates if BCC email notifications are enabled.
    - **"1"** → enabled
    - **"0"** → disabled
  - `is_directly`: Indicates whether the configuration is set directly (no intermediary).
    - **"1"** → direct integration
    - **"0"** → through another system
  - `emails`: A list of additional email addresses associated with the hotel.
  - `created_at`: Timestamp indicating when the hotel record was created (ISO 8601 format).
  - `created_by`: The user or system that created the record (e.g., "System").
  - `updated_at`: Timestamp indicating when the hotel record was last updated.
  - `updated_by`: The user who last updated the record (empty if no update user is tracked).

## 5. Create Property

Create a new property.

**Endpoint:** `POST /InsertProperties`

**Request Body:**

```json
{
  "hotel_code": "HTL-98234",
  "hotel_name": "Grand Aurora Hotel",
  "ota_hotel_name": "Grand Aurora Downtown",
  "currency_code": "USD",
  "username": "aurora_admin",
  "phone_number": "+1-202-555-0198",
  "zip_code": "90210",
  "country_code": "US",
  "state": "California",
  "city": "Los Angeles",
  "address": "1234 Sunset Boulevard",
  "property_id": "your_property_id",
  "property_status": "N",
  "min_stay_type": "arrival",
  "user_api_key": "your_property_api_key",
  "is_cc": "true",
  "is_bcc": "false",
  "is_directly": "true",
  "emails": [
    "contacthotel@mail.com",
    "reservationshotel@mail.com"
  ]
}
```

#### Request Body Field Details
- `hotel_code`: A unique code used to identify the hotel within the system.
- `hotel_name`: The official name of the hotel as registered in the internal system.
- `ota_hotel_name`: The name of the hotel as it appears on the OTA (Online Travel Agency) platform, such as Booking.com or Agoda.
- `currency_code`: The currency used by the hotel for transactions (ISO 4217 format, e.g., USD, IDR).
- `username`: The username taken from the currently logged-in user in your system. It identifies which user performed or initiated the integration or configuration action.
- `phone_number`: The hotel’s official contact phone number.
- `zip_code`: The postal code of the hotel’s location.
- `country_code`: The country code following ISO 3166-1 alpha-2 format (e.g., US, ID, MY).
- `state`: The state or province where the hotel is located.
- `city`: The city where the hotel is located.
- `address`: The full physical address of the hotel.
- `property_id`: A unique property identifier provided by Channex. This ID represents the hotel within the Channex channel manager system and is used for mapping, syncing availability, rates, and inventory.
- `property_status`: Indicates the mapping status of the property in the system.
  - **Mapped ("M")** → The property is already connected or synchronized.
  - **Not Mapped / New Property ("N")** → The property is not yet connected and still needs configuration.
- `min_stay_type`: Defines how the minimum stay restriction is applied.
  - **"arrival"** → Minimum stay applies based on the arrival date of the guest.
  - **"through"** → Minimum stay applies across the entire stay period.
- `user_api_key`: The API key generated by Channex, required for authenticating requests and enabling the hotel's integration with the Channex platform.
- `is_cc`: Indicates if CC email notifications are enabled.
  - **"1"** → enabled
  - **"0"** → disabled
- `is_bcc`: Indicates if BCC email notifications are enabled.
  - **"1"** → enabled
  - **"0"** → disabled
- `is_directly`: Indicates whether the configuration is set directly (no intermediary).
  - **"1"** → direct integration
  - **"0"** → through another system
- `emails`: A list of email addresses used by the hotel to receive notifications.

---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_code": "HTL-98234",
  "hotel_name": "Grand Aurora Hotel",
  "ota_hotel_name": "Grand Aurora Downtown",
  "currency_code": "USD",
  "username": "aurora_admin",
  "phone_number": "+1-202-555-0198",
  "zip_code": "90210",
  "country_code": "US",
  "state": "California",
  "city": "Los Angeles",
  "address": "1234 Sunset Boulevard",
  "property_id": "your_property_id",
  "property_status": "N",
  "min_stay_type": "arrival",
  "user_api_key": "your_property_api_key",
  "is_cc": "true",
  "is_bcc": "false",
  "is_directly": "true",
  "emails": [
    "contacthotel@mail.com",
    "reservationshotel@mail.com"
  ]
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/InsertProperties',
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

## 6. Update Property

Update a property.

**Endpoint:** `PUT /UpdateProperties`

**Request Body:**

```json
{
  "id": 1,
  "hotel_code": "HTL-98234",
  "hotel_name": "Grand Aurora Hotel",
  "name": "Grand Aurora Downtown",
  "currency_code": "USD",
  "username": "aurora_admin",
  "phone_number": "+1-202-555-0198",
  "zip_code": "90210",
  "country_code": "US",
  "state": "California",
  "city": "Los Angeles",
  "address": "1234 Sunset Boulevard",
  "property_id": "your_property_id",
  "min_stay_type": "arrival",
  "user_api_key": "your_property_api_key",
  "is_cc": "true",
  "is_bcc": "false",
  "is_directly": "true",
  "emails": [
    "contacthotel@mail.com",
    "reservationshotel@mail.com"
  ]
}
```

#### Request Body Field Details
- `id`: The internal identifier for this hotel record.
- `hotel_code`: A unique code used to identify the hotel within the system.
- `hotel_name`: The official name of the hotel as registered in the internal system.
- `ota_hotel_name`: The name of the hotel as it appears on the OTA (Online Travel Agency) platform, such as Booking.com or Agoda.
- `currency_code`: The currency used by the hotel for transactions (ISO 4217 format, e.g., USD, IDR).
- `username`: The username taken from the currently logged-in user in your system. It identifies which user performed or initiated the integration or configuration action.
- `phone_number`: The hotel’s official contact phone number.
- `zip_code`: The postal code of the hotel’s location.
- `country_code`: The country code following ISO 3166-1 alpha-2 format (e.g., US, ID, MY).
- `state`: The state or province where the hotel is located.
- `city`: The city where the hotel is located.
- `address`: The full physical address of the hotel.
- `property_id`: A unique property identifier provided by Channex. This ID represents the hotel within the Channex channel manager system and is used for mapping, syncing availability, rates, and inventory.
- `property_status`: Indicates the mapping status of the property in the system.
  - **Mapped ("M")** → The property is already connected or synchronized.
  - **Not Mapped / New Property ("N")** → The property is not yet connected and still needs configuration.
- `min_stay_type`: Defines how the minimum stay restriction is applied.
  - **"arrival"** → Minimum stay applies based on the arrival date of the guest.
  - **"through"** → Minimum stay applies across the entire stay period.
- `user_api_key`: The API key generated by Channex, required for authenticating requests and enabling the hotel's integration with the Channex platform.
- `is_cc`: Indicates if CC email notifications are enabled.
  - **"1"** → enabled
  - **"0"** → disabled
- `is_bcc`: Indicates if BCC email notifications are enabled.
  - **"1"** → enabled
  - **"0"** → disabled
- `is_directly`: Indicates whether the configuration is set directly (no intermediary).
  - **"1"** → direct integration
  - **"0"** → through another system
- `emails`: A list of email addresses used by the hotel to receive notifications.


---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "id": 1,
  "hotel_code": "HTL-98234",
  "hotel_name": "Grand Aurora Hotel",
  "ota_hotel_name": "Grand Aurora Downtown",
  "currency_code": "USD",
  "username": "aurora_admin",
  "phone_number": "+1-202-555-0198",
  "zip_code": "90210",
  "country_code": "US",
  "state": "California",
  "city": "Los Angeles",
  "address": "1234 Sunset Boulevard",
  "property_id": "your_property_id",
  "min_stay_type": "arrival",
  "user_api_key": "your_property_api_key",
  "is_cc": "true",
  "is_bcc": "false",
  "is_directly": "true",
  "emails": [
    "contacthotel@mail.com",
    "reservationshotel@mail.com"
  ]
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/UpdateProperties',
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

## 7. Delete Property

Delete a property.

**Endpoint:** `DELETE /DeleteProperties/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code to delete

---

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'delete',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/DeleteProperties/CKR'
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