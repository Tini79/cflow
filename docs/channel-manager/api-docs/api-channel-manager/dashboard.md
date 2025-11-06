---
title: API Booking Dashboard
description: Complete API reference for Booking Dashboard
sidebar_position: 9
---

# Booking Dashboard API Endpoints

This API provides a summary and calculation of booking data.

## 1. Get Booking Count

Retrieve booking count.

**Endpoint:** `GET /GetBookingCount/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetBookingCount/Drune'
};

axios.request(config)
.then((response) => {
  console.log('Booking count retrieved successfully');
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
    "daily_count": [
      {
        "count": 0,
        "date": "1"
      },
      {
        "count": 0,
        "date": "2"
      },
      {
        "count": 0,
        "date": "3"
      },
      {
        "count": 0,
        "date": "4"
      },
      {
        "count": 0,
        "date": "5"
      },
      {
        "count": 0,
        "date": "6"
      },
      {
        "count": 0,
        "date": "7"
      },
      {
        "count": 0,
        "date": "8"
      },
      {
        "count": 0,
        "date": "9"
      },
      {
        "count": 0,
        "date": "10"
      },
      {
        "count": 0,
        "date": "11"
      },
      {
        "count": 0,
        "date": "12"
      },
      {
        "count": 0,
        "date": "13"
      },
      {
        "count": 0,
        "date": "14"
      },
      {
        "count": 0,
        "date": "15"
      },
      {
        "count": 0,
        "date": "16"
      },
      {
        "count": 0,
        "date": "17"
      },
      {
        "count": 0,
        "date": "18"
      },
      {
        "count": 0,
        "date": "19"
      },
      {
        "count": 0,
        "date": "20"
      },
      {
        "count": 0,
        "date": "21"
      },
      {
        "count": 0,
        "date": "22"
      },
      {
        "count": 0,
        "date": "23"
      },
      {
        "count": 0,
        "date": "24"
      },
      {
        "count": 0,
        "date": "25"
      },
      {
        "count": 0,
        "date": "26"
      },
      {
        "count": 0,
        "date": "27"
      },
      {
        "count": 0,
        "date": "28"
      },
      {
        "count": 0,
        "date": "29"
      },
      {
        "count": 0,
        "date": "30"
      }
    ],
    "current_date": null,
    "monthly": null,
    "annually": [
      {
        "count": 23,
        "status": "S"
      },
      {
        "count": 3,
        "status": "P"
      }
    ],
    "daily_booking_by_ota": null,
    "monthly_booking_by_ota": [
      {
        "ota_code": "OBE ",
        "total_count": 1,
        "monthly_counts": {
          "10": 1
        }
      },
      {
        "ota_code": "BDC",
        "total_count": 26,
        "monthly_counts": {
          "4": 7,
          "5": 17,
          "7": 1,
          "10": 1
        }
      }
    ],
    "annually_booking_by_ota": [
      {
        "count": 1,
        "ota_code": "OBE ",
        "year": 2024
      },
      {
        "count": 27,
        "ota_code": "BDC",
        "year": 2025
      }
    ]
  }
}
```

#### Response Field Details
**Result**: An array containing booking count returned by the API.
  - `current_date`: Current date of the report.
  - `daily_count`: Array of daily booking counts for the current month.
    - `count`: Number of bookings for that day.
    - `date`: Day of the month (1–30 or 31).
  - `monthly`: Monthly aggregate data.
    - `count`: Number of bookings.
    - `status`: Status of bookings.
      - **S** = Success
      - **U** = Unmapping
      - **P** = Process
      - **F** = Failed
  - `annually`: Array of aggregated booking counts for the year by status.
    - `count`: Number of bookings.
    - `status`: Status of bookings.
  - `daily_booking_by_ota`: Optional array of daily booking counts broken down by OTA.
    - `count`: Number of bookings.
    - `ota_code`: OTA identifier.
    - `day`: Day of the bookings.
  - `monthly_booking_by_ota`: Array of monthly booking counts per OTA.
    - `ota_code`: OTA identifier (e.g., "BDC", "OBE").
    - `total_count`: Total bookings for the OTA in the current period.
    - `monthly_counts`: Object mapping month numbers to booking counts (e.g., "4": 7 means 7 bookings in April).
  - `annually_booking_by_ota`: Annual bookings broken down per OTA.
    - `count`: Number of bookings.
    - `ota_code`: OTA identifier.
    - `year`: Year of the bookings.
    
## 2. Get Inventory Count

Retrieve inventory count.

**Endpoint:** `GET /GetInvCount/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetInvCount/Drune'
};

axios.request(config)
.then((response) => {
  console.log('Inventory count retrieved successfully');
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
    "data": {
      "4a90fd9a-6690-4570-9866-306b97387409": {
        "2025-11-06": 10,
        "2025-11-07": 6,
        "2025-11-08": 5,
        "2025-11-09": 16,
        "2025-11-10": 16,
        "2025-11-11": 16,
        "2025-11-12": 17,
        "2025-11-13": 17,
        "2025-11-14": 15,
        "2025-11-15": 14,
        "2025-11-16": 17,
        "2025-11-17": 17,
        "2025-11-18": 17,
        "2025-11-19": 17,
        "2025-11-20": 16,
        "2025-11-21": 15,
        "2025-11-22": 14,
        "2025-11-23": 17,
        "2025-11-24": 17,
        "2025-11-25": 17,
        "2025-11-26": 17,
        "2025-11-27": 17,
        "2025-11-28": 14,
        "2025-11-29": 14,
        "2025-11-30": 17,
        "2025-12-01": 17,
        "2025-12-02": 17,
        "2025-12-03": 17,
        "2025-12-04": 17,
        "2025-12-05": 17,
        "2025-12-06": 17,
        "2025-12-07": 17,
        "2025-12-08": 17,
        "2025-12-09": 17,
        "2025-12-10": 17,
        "2025-12-11": 17,
        "2025-12-12": 17,
        "2025-12-13": 17,
        "2025-12-14": 17,
        "2025-12-15": 17,
        "2025-12-16": 17,
        "2025-12-17": 17,
        "2025-12-18": 17,
        "2025-12-19": 17,
        "2025-12-20": 17,
        "2025-12-21": 17,
        "2025-12-22": 17,
        "2025-12-23": 17,
        "2025-12-24": 17,
        "2025-12-25": 17,
        "2025-12-26": 17,
        "2025-12-27": 17,
        "2025-12-28": 17,
        "2025-12-29": 17,
        "2025-12-30": 17,
        "2025-12-31": 17
      },
    }
  }
}
```

#### Response Field Details
**Result**: An object containing inventory count returned by the API.
  - `data`: Holds the room-type availability information.
    - `4a90fd9a-6690-4570-9866-306b97387409`: Room-type ID obtained from Channex.
      - Each property inside this object represents a date, and its value indicates the number of available rooms for that specific date.

## 3. Get Revenue Count

Retrieve revenue count.

**Endpoint:** `GET /GetRevenueCount/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetRevenueCount/Drune'
};

axios.request(config)
.then((response) => {
  console.log('Revenue count retrieved successfully');
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
    "daily_revenue": [
      {
        "amount": 10306788,
        "date": "1"
      },
      {
        "amount": 15061962.5,
        "date": "2"
      },
      {
        "amount": 13880779.5,
        "date": "3"
      },
      {
        "amount": 18209132.6,
        "date": "4"
      },
      {
        "amount": 8721734.5,
        "date": "5"
      },
      {
        "amount": 10506816,
        "date": "6"
      },
      {
        "amount": 0,
        "date": "7"
      },
      {
        "amount": 0,
        "date": "8"
      },
      {
        "amount": 0,
        "date": "9"
      },
      {
        "amount": 0,
        "date": "10"
      },
      {
        "amount": 0,
        "date": "11"
      },
      {
        "amount": 0,
        "date": "12"
      },
      {
        "amount": 0,
        "date": "13"
      },
      {
        "amount": 0,
        "date": "14"
      },
      {
        "amount": 0,
        "date": "15"
      },
      {
        "amount": 0,
        "date": "16"
      },
      {
        "amount": 0,
        "date": "17"
      },
      {
        "amount": 0,
        "date": "18"
      },
      {
        "amount": 0,
        "date": "19"
      },
      {
        "amount": 0,
        "date": "20"
      },
      {
        "amount": 0,
        "date": "21"
      },
      {
        "amount": 0,
        "date": "22"
      },
      {
        "amount": 0,
        "date": "23"
      },
      {
        "amount": 0,
        "date": "24"
      },
      {
        "amount": 0,
        "date": "25"
      },
      {
        "amount": 0,
        "date": "26"
      },
      {
        "amount": 0,
        "date": "27"
      },
      {
        "amount": 0,
        "date": "28"
      },
      {
        "amount": 0,
        "date": "29"
      },
      {
        "amount": 0,
        "date": "30"
      }
    ],
    "current_revenue": 10506816,
    "monthly_revenue": 76687213.1,
    "annually_revenue": 1288813210.020001
  }
}
```

#### Response Field Details
**Result**: An object containing revenue count returned by the API.
  - `daily_revenue`: An array listing revenue per day. Each item includes:
    - `date`: The day of the month.
    - `amount`: Total revenue generated on that day.
  - `current_revenue`: Total revenue for the most recent day.
  - `monthly_revenue`: Total accumulated revenue for the current month.
  - `annually_revenue`: Total accumulated revenue for the current year.