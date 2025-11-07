---
title: API Reservation
description: Complete API reference for handling reservation on Channel Manager
sidebar_position: 8
---

## 1. Read Booking for Cakra PMS API

Read bookings from OTA and send them to Cakra PMS.

**Endpoint:** `GET /ReadBooking`

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/ReadBooking',
  headers: {
    'Authorization': `Basic ${token}`
  }
};

axios.request(config)
.then((response) => {
  console.log('Booking list retrieved successfully');
})
.catch((error) => {
  console.log(error);
});
```

#### Response Field Details
**data**: Array of booking records returned by the API. Each element contains the Attributes of a single booking.
  - `attributes`: Contains all detailed information about a booking.
    - `id`: Unique internal identifier for the booking record.
    - `meta`: Metadata associated with the booking.
        - `ruid`: Unique record identifier.
    - `status`: Current status of the booking.
      - **new**: New booking
      - **modified**: Modified booking
      - **cancelled**: Cancelled booking
    - `services`: Array of additional services associated with the booking.
    - `currency`: Currency code for amounts.
    - `amount`: Total amount of the booking in the specified currency.
    - `agent`: Information about the booking agent, if applicable. Could be null or structured object.
    - `inserted_at`: Timestamp when the booking was created/inserted in the system.
    - `ota_name`: Name of the OTA (Online Travel Agency) through which the booking was made.
    - `channel_id`: Identifier for the channel if applicable.
    - `property_code`: Code representing the hotel or property for the booking.
    - `unique_id`: Unique identifier for the booking used across systems.
    - `system_id`: Internal system ID linking the booking to a specific PMS or platform.
    - `booking_id`: Booking reference number.
    - `arrival_date`: Check-in date for the booking.
    - `arrival_hour`: Optional expected check-in time.
    - `customer`: Object containing customer information.
      - `meta`: Metadata for the customer record.
      - `name`: Customer’s first name.
      - `surname`: Customer’s last name.
      - `zip`: Postal code.
      - `address`: Customer address.
      - `country`: ISO country code for the customer.
      - `city`: City of the customer.
      - `language`: Preferred language.
      - `company`: Customer’s company or organization.
      - `mail`: Email address.
    - `departure_date`: Check-out date for the booking.
    - `deposits`: Information on any deposits paid or required.
    - `guarantee`: Details about any guarantee.
    - `notes`: Internal notes associated with the booking.
    - `payment_collect`: Specifies who collects the payment.
    - `payment_type`: Type of payment.
    - `rooms`: Array of room details associated with this booking.
      - `internal_room_id`: Internal system ID for the room.
      - `booking_status`: Status of the room booking.
        - **New**: New booking
        - **Modify**: Modified booking
        - **Cancelled**: Cancelled booking
      - `booking_id`: ID of the booking this room belongs to.
      - `meta` RoomMeta: Metadata about the room record .
      - `taxes`: Array of taxes applied to this room.
      - `services`: Extra services associated with the room.
      - `amount`: Total amount charged for this room.
      - `days`: Rates per day; keys are date strings, values are amounts.
      - `booking_room_id`: Unique ID for this room in the booking.
      - `booking_com_room_index`: Optional index for OTA or external system reference.
      - `rate_plan_code`: Rate plan code applied to this room.
      - `room_type_code`: Code of the room type.
      - `guests`: Array of guest details for this room.
      - `occupancy` Occupancy: Number of adults, children, and infants in the room.
      - `ota_commission`: Commission applied by the OTA, if any.
      - `checkin_date`: Room check-in date.
      - `checkout_date`: Room check-out date.
      - `is_cancelled`: Boolean indicating whether this room booking is canceled.
    - `secondary_ota`: Optional secondary OTA reference, if any.
    - `occupancy`: Object specifying the number of adults, children, and infants in the booking.
      - `children`: Number of children in the room.
      - `adults`: Number of adults in the room.
      - `infants`: Number of infants in the room.
      - `ages`: Array of ages for all occupants.
    - `acknowledge_status`: Status of booking acknowledgment.
    - `ota_commission`: Commission information for the OTA.
    - `ota_reservation_code`: Reservation code assigned by the OTA.
    - `comments`: Guest comments.
    - `special_requests`: Any special requests made by the guest.
    - `raw_message`: Raw message or data payload received from the OTA or channel system, useful for debugging or auditing.

## 2. Send Booking to Other PMS API

Read bookings from OTA and send them to other PMS.
The API response contains two types of booking data:
  1. **Cancelled Bookings** – Bookings that have been canceled in the OTA.
  2. **New or Modified Bookings** – Newly created or updated bookings that need to be pushed to the PMS.

**Endpoint:** `GET /GetReservation/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code

**Example Request:**

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/GetReservation/CKR',
  'Authorization': `Bearer ${token}`
};

axios.request(config)
.then((response) => {
  console.log('Booking list retrieved successfully');
})
.catch((error) => {
  console.log(error);
});
```

#### Response Field for New/Modified Details
- `booking_id`: Unique internal identifier for the booking.
- `booking_code`: Booking reference code provided by the OTA.
- `otaid`: Identifier of the OTA from which the booking originated.
- `arrival_time_str`: Expected check-in time in string format.
- `arrival_date`: Check-in date.
- `departure_date`: Check-out date.
- `adult`: Number of adult guests.
- `child`: Number of child guests.
- `room_type_code`: Code of the room type reserved.
- `bed_type_code`: Code for the bed type.
- `full_name`: Full name of the guest.
- `street`: Street address of the guest.
- `city`: Guest’s city.
- `postal_code`: Guest’s postal code.
- `phone1`: Primary contact number of the guest.
- `email`: Email address of the guest.
- `room_rate_amount_str`: Rate amount per room.
- `room_rate_code`: Code representing the rate plan applied.
- `company_code`: Guest’s company code, if applicable.
- `country_code`: ISO country code of the guest.
- `comment`: Any comments added by the guest or OTA.
- `special_request`: Special requests made by the guest.
- `currency_code`: Currency of the booking amount.
- `res_status`: Reservation status.

#### Response Field for Canceled Details
- `booking_id`: Unique internal identifier for the booking.
- `booking_code`: Booking reference code provided by the OTA.
- `otaid`: Identifier of the OTA from which the booking originated.

## 3. Save and Acknoledge Booking API

Saving the booking to the Channel Manager (CM) and PMS, including acknowledgment for bookings successfully received by the PMS.

**Endpoint:** `POST /ReservationNotif`

**Request Body:**

```json
{
  "ota_id": "2c4cecd0-f459-4aed-81ae-d23b57934ce0",
  "revision_id": "4890517111"
}
```

#### Request Body Field Details
- `ota_id`: Unique identifier for the Online Travel Agency (OTA) or channel in the system.
- `revision_id`: Identifier for a specific revision/version of data sent or received from the OTA.

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "ota_id": "2c4cecd0-f459-4aed-81ae-d23b57934ce0",
  "revision_id": "4890517111"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/ReservationNotif',
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

**Example Response:**

```json
{
  "StatusCode": 0,
  "Message": "Success",
  "Result": null
}
```

## 4. Resend Booking API

Resending the booking to the PMS if it failed or has not yet been delivered.

**Endpoint:** `POST /ResendBooking`

**Request Body:**

```json
{
  "hotel_code": "CKR",
  "booking_id": "3626a0a9-6e11-443b-aa32-152d7fdd2853",
  "revision_id": "ef0fc39b-90ee-4306-be7d-99e0f939c38a"
}
```

#### Request Body Field Details
- `hotel_code`: The unique identifier of the hotel where the booking belongs.
- `booking_id`: The booking reference number received from the Channel Manager or OTA.
- `revision_id`: The revision number of the booking, used to track updates or modifications to the reservation.

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "hotel_code": "CKR",
  "booking_id": "3626a0a9-6e11-443b-aa32-152d7fdd2853",
  "revision_id": "ef0fc39b-90ee-4306-be7d-99e0f939c38a"
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/ResendBooking',
  headers: {
    'Content-Type': 'application/json',
    headers:{
      'Authorization': `Bearer ${token}`
    }
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

**Example Response:**

```json
{
  "StatusCode": 0,
  "Message": "Success",
  "Result": null
}
```

## 5. Read Booking Webhook API

This API serves as the booking webhook endpoint used by Channex to send reservation data to the Cakrahub Channel Manager. Whenever a new booking or booking update occurs, Channex pushes the booking payload to this endpoint so Cakrahub can process, store, and synchronize the reservation with the PMS.

**Endpoint:** `POST /ReadBookingWebhook`

**Query Parameters:**
- `HotelCode`: Hotel code

**Request Body:**

```json
{
  "event": "booking",
  "payload": {
    "booking_id": "fbb30008-8050-41a2-afbb-7ba3acc2acc8",
    "property_id": "7c9fd297-9e1c-422f-857b-93495ff25425",
    "revision_id": "ebc775e7-b140-473a-8380-dbe41b8f3c95"
  },
  "property_id": "7c9fd297-9e1c-422f-857b-93495ff25425",
  "user_id": 1024,
  "timestamp": "2025-02-14T10:22:45Z"
}
```

#### Request Body Field Details
- `event`: The type of webhook event sent by Channex.
- `payload`: The booking data included in the webhook, containing booking and revision identifiers.
  - `booking_id`: The unique booking identifier assigned by Channex.
  - `property_id`: The property ID associated with the booking, matching the property in Channex.
  - `revision_id`: The revision number for the booking, representing changes or updates made to the reservation.
- `property_id`: The unique property ID in Channex associated with the booking.
- `user_id`: The ID of the user or integration sender triggering the webhook. May be null or various types depending on Channex’s structure.
- `timestamp`: The ISO 8601 timestamp indicating when the webhook event was generated.

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "event": "booking",
  "payload": {
    "booking_id": "fbb30008-8050-41a2-afbb-7ba3acc2acc8",
    "property_id": "7c9fd297-9e1c-422f-857b-93495ff25425",
    "revision_id": "ebc775e7-b140-473a-8380-dbe41b8f3c95"
  },
  "property_id": "7c9fd297-9e1c-422f-857b-93495ff25425",
  "user_id": 1024,
  "timestamp": "2025-02-14T10:22:45Z"
}
);

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cm.cakrasoft.net/cm/api/v2/ReadBookingWebhook',
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

**Example Response:**

```json
{
  "StatusCode": 0,
  "Message": "Success",
  "Result": null
}
```