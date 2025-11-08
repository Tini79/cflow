---
title: ARI API
description: Complete API reference for managing room rate and room availability on Channel Manager
sidebar_position: 7
---

## 1. Update Rate Plan

To update the pricing, details, or conditions of an existing rate plan for a hotel or property.

**Endpoint:** `PUT /UpdateARIRatePlan`

**Request Body:**

```json
{
  "hotel_code": "HTL-1001",
  "hotel_name": "Grand Aurora Hotel",
  "details": [
    {
      "start_date": "2023-11-10T00:00:00Z",
      "end_date": "2023-11-16T00:00:00Z",
      "rate_plan_code": "RPSTD01",
      "rate_plan_name": "Standard Rate Plan",
      "room_type_code": "SGL",
      "currency_code": "USD",
      "rate_details": [
        {
          "amount_after_tax": 312
        }
      ]
    }
  ]
}
```

#### Request Body Field Details
- `hotel_code`: A unique code identifying the hotel in the system.
- `hotel_name`: The official name of the hotel.
- `details`: Array of rate plan details for specific date ranges and room types.
  - `start_date`: Start date of the rate plan validity.
  - `end_date`: End date of the rate plan validity.
  - `rate_plan_code`: Unique code representing the rate plan.
  - `rate_plan_name`: Name of the rate plan.
  - `room_type_code`: Code representing the room type this rate applies to.
  - `currency_code`: Currency in which the rate is expressed.
  - `rate_details`: Array containing rate values for the specified room and rate plan.
    - `amount_after_tax`: Final price per room including all taxes for the given rate plan.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_code": "HTL-1001",
  "hotel_name": "Grand Aurora Hotel",
  "details": [
    {
      "start_date": "2023-11-10T00:00:00Z",
      "end_date": "2023-11-16T00:00:00Z",
      "rate_plan_code": "RPSTD01",
      "rate_plan_name": "Standard Rate Plan",
      "room_type_code": "SGL",
      "currency_code": "USD",
      "rate_details": [
        {
          "amount_after_tax": 312
        }
      ]
    }
  ]
});

let config = {
  method: 'put',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/UpdateARIRatePlan',
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

## 2. Update Room Availability

To update the availability of rooms in a hotel or property for specific dates.

**Endpoint:** `PUT /UpdateARIAvailability`

**Request Body:**

```json
{
  "hotel_code": "HTL-1001",
  "details": [
    {
      "start_date_str": "2025-02-13",
      "end_date_str": "2025-02-13",
      "room_type_code": "PRS",
      "availability": 4,
      "booking_limit": 9
    }
  ]
}
```

#### Request Body Field Details
- `hotel_code`: A unique code identifying the hotel in the system.
- `details`:
Array of room availability records for specific dates and room types.
  - `start_date_str`: Start date of the availability period (format: YYYY-MM-DD).
  - `end_date_str`: End date of the availability period (format: YYYY-MM-DD).
  - `room_type_code`: Code representing the room type.
  - `availability`: Number of rooms available for booking for the given date range and room type.
  - `booking_limit`: Maximum number of rooms that can be booked per reservation for this room type.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_code": "HTL-1001",
  "details": [
    {
      "start_date_str": "2025-02-13",
      "end_date_str": "2025-02-13",
      "room_type_code": "PRS",
      "availability": 4,
      "booking_limit": 9
    }
  ]
});

let config = {
  method: 'put',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/UpdateARIAvailability',
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