---
title: API Room Rate
description: Complete API reference for managing Room Rate
sidebar_position: 4
---

# Room Rate API Documentation

This page provides an overview of the available API endpoints for managing Room Rate.

## 1. Send Room Rate to Cakrahub Channel Manager

This API sends updated room rates from the PMS to the CakraHub Channel Manager, ensuring that pricing changes are synchronized and distributed to connected OTAs.

**Endpoint:** `POST /SendRoomRate`

**Request Body:**

```json
{
  "cm_vendor": "CKHU",
  "hotel_code": "MM1064",
  "unit_code": "U01",
  "hotel_name": "Green Valley Hotel",
  "requestor_id": "",
  "user": "GVHCH003",
  "password": "GreenValley#12",
  "WSDL": "https://cm.cakrasoft.net/cm/api/v1",
  "type_code": "CM",
  "details": [
    {
      "id": 1,
      "start_date_str": "2025-03-01",
      "end_date_str": "2025-03-07",
      "start_date": "2025-03-01",
      "end_date": "2025-03-07",
      "rate_plan_code": "RP001",
      "cm_rate_plan_code": "CMRP001",
      "rate_plan_name": "Standard Flexible Rate",
      "room_type_code": "DLX",
      "currency_code": "IDR",
      "closed_to_arrival": 0,
      "closed_to_departure": 1,
      "day1": 750000,
      "day2": 750000,
      "day3": 760000,
      "day4": 760000,
      "day5": 780000,
      "day6": 800000,
      "day7": 820000,
      "hotel_code": "MM1062",
      "inv_code": "INV-DLX",
      "cm_inv_code": "CMINV-DLX",
      "rate": "750000",
      "stop_sell": 0
    }
  ]
});
```

#### Request Body Field Details
- `cm_vendor`: Code identifying the Channel Manager vendor (e.g., CKHU).
- `hotel_code`: A unique code used to identify the hotel within the system.
- `unit_code`: Code representing a specific unit or sub-property. Can be empty if not applicable.
- `hotel_name`: The full name of the hotel or property.
- `requestor_id`: Optional ID of the requesting system or user. Can be empty if not used.
- `user`: Username used for authentication with the Channel Manager.
- `password`: Password used for authentication with the Channel Manager.
- `WSDL`: The base API endpoint or WSDL URL of the CakraHub Channel Manager.
- `type_code`: Integration type. "CM" indicates Channel Manager.
- `details`: A list of room rate details to be sent to the Channel Manager.
  - `id`: Internal ID used to identify the rate detail entry.
  - `start_date_str`: Start date of the rate period in string format (YYYY-MM-DD).
  - `end_date_str`: End date of the rate period in string format (YYYY-MM-DD).
  - `start_date`: Start date value to be sent to the Channel Manager.
  - `end_date`: End date value to be sent to the Channel Manager.
  - `rate_plan_code`: PMS rate plan code associated with the rate update.
  - `cm_rate_plan_code`: Channel Manager rate plan code mapped to the PMS rate plan.
  - `rate_plan_name`: Name of the rate plan for reference.
  - `room_type_code`: PMS room type code associated with the rate.
  - `currency_code`: Currency code used for the rate value (e.g., IDR).
  - `closed_to_arrival`: Indicates if the date is closed to arrival. 0 = open, 1 = closed.
  - `closed_to_departure`: Indicates if the date is closed to departure. 0 = open, 1 = closed.
  - `day1`: Rate value for Monday.
  - `day2`: Rate value for Tuesday.
  - `day3`: Rate value for Wednesday.
  - `day4`: Rate value for Thursday.
  - `day5`: Rate value for Friday.
  - `day6`: Rate value for Saturday.
  - `day7`: Rate value for Sunday.
  - `hotel_code`: Hotel code linked to the rate detail (may differ if mapped differently).
  - `inv_code`: PMS inventory/room type code.
  - `cm_inv_code`: Channel Manager inventory code mapped from the PMS room type.
  - `rate`: Base rate value as string (typically used as the default rate for the period).
  - `stop_sell`: Indicates stop-sell status. 0 = open for sale, 1 = stop sell.
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "cm_vendor": "CKHU",
  "hotel_code": "MM1064",
  "unit_code": "U01",
  "hotel_name": "Green Valley Hotel",
  "requestor_id": "",
  "user": "GVHCH003",
  "password": "GreenValley#12",
  "WSDL": "https://cm.cakrasoft.net/cm/api/v1",
  "type_code": "CM",
  "details": [
    {
      "id": 1,
      "start_date_str": "2025-03-01",
      "end_date_str": "2025-03-07",
      "start_date": "2025-03-01",
      "end_date": "2025-03-07",
      "rate_plan_code": "RP001",
      "cm_rate_plan_code": "CMRP001",
      "rate_plan_name": "Standard Flexible Rate",
      "room_type_code": "DLX",
      "currency_code": "IDR",
      "closed_to_arrival": 0,
      "closed_to_departure": 1,
      "day1": 750000,
      "day2": 750000,
      "day3": 760000,
      "day4": 760000,
      "day5": 780000,
      "day6": 800000,
      "day7": 820000,
      "hotel_code": "MM1062",
      "inv_code": "INV-DLX",
      "cm_inv_code": "CMINV-DLX",
      "rate": "750000",
      "stop_sell": 0
    }
  ]
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/SendRoomRate',
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