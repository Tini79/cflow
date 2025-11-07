---
title: API Reservation
description: Complete API reference for managing Reservation
sidebar_position: 5
---

# Reservations API Documentation

This page provides an overview of the available API endpoints for managing Reservations through CRUD operations.

## 1. Receive Booking Webhook

This API is designed to receive booking data from the Channel Manager and then forward that information to the PMS (Property Management System). It acts as a communication bridge between the Channel Manager and the PMS, ensuring that every new reservation, modification, or cancellation made on online travel platforms is delivered accurately and in real-time to the PMS.

**Endpoint:** `POST /ReceiveBookingWebhook/{hotel_code}`

**Parameters:**
- `hotel_code`: Hotel code

#### Request Body Field Details
**data**: Array of booking records returned by the API. Each element contains the Attributes of a single booking.
  - `attributes`: Contains all detailed information about a booking.
    - `id`: Unique internal identifier for the booking record.
    - `meta`: Metadata associated with the booking.
      - `ruid`: Unique record identifier.
      - `booking_com_room_index`: A numeric index used to identify the corresponding room mapping specifically for Booking.com
    - `status`: Current status of the booking.
      - **new**: New booking
      - **modified**: Modified booking
      - **cancelled**: Cancelled booking
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
      - `phone`: Phone number.
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
---

**Example Request:**

```javascript
const axios = require('axios');

let data = JSON.stringify({
  "data": [
    {
      "attributes": {
        "id": "aa9a98e3-08b5-42d1-b219-b2de00f1bb3f",
        "meta": {
          "ruid": "UmFuZG9tSVYkc2RlIyh9YRLi6s6kj24wzLnoUJlJBRUYO80+OfrdWjs8ir+EjfU1gnesPbeO9/++nL6rTFmbMxWA66XHHq+g7cAH/3/5aLA="
        },
        "status": "modified",
        "services": [],
        "currency": "USD",
        "amount": "369.12",
        "agent": null,
        "inserted_at": "2025-10-30T02:46:34.538859",
        "ota_name": "BookingCom",
        "channel_id": "3810c750-3b55-4514-b162-c7934f041f6f",
        "property_code": "Drune",
        "unique_id": "BDC-6700672290",
        "system_id": "bef3ae78",
        "booking_id": "eebd0c4b-0bdb-4b19-90fb-2f1e31fc45b0",
        "arrival_date": "2025-10-30",
        "arrival_hour": null,
        "customer": {
          "meta": { "is_genius": false },
          "name": "Bambang",
          "zip": "80581",
          "address": "Jl. Tamblingan Sanur",
          "country": "ID",
          "city": "Denpasar",
          "language": null,
          "company": null,
          "mail": "bsuher.347203@guest.booking.com",
          "phone": "+62 819 9999 99999",
          "surname": "Suherma"
        },
        "departure_date": "2025-10-31",
        "deposits": [],
        "guarantee": {
          "card_number": "411111******1111",
          "card_type": "VI",
          "cardholder_name": "Bambang Suherma",
          "cvv": "***",
          "expiration_date": "12/2025",
          "is_virtual": false,
          "token": null
        },
        "notes": "\nMeal Plan: Breakfast costs US$14 per person per night.\nDinner costs US$35 per person per night.\nPayment Collect: hotel collect\nOTA Commission: 0.00",
        "payment_collect": "property",
        "payment_type": "credit_card",
        "rooms": [
          {
            "internal_room_id": 68,
            "booking_status": "Modify",
            "booking_id": "eebd0c4b-0bdb-4b19-90fb-2f1e31fc45b0",
            "meta": {
              "days_breakdown": [
                {
                  "amount": "54.00",
                  "date": "2025-10-30",
                  "promotion": null,
                  "rate_code": 37364467,
                  "rate_plan": "b3cd6118-1614-488c-824f-998a02039304"
                }
              ],
              "cancel_penalties": [
                {
                  "amount": "61.56",
                  "currency": "USD",
                  "from": "2025-10-30T02:31:11"
                }
              ],
              "additional_details": [],
              "booking_com_room_index": 437,
              "meal_plan": "Breakfast costs US$14 per person per night.\nDinner costs US$35 per person per night.",
              "policies": "Children and Extra Bed Policy: Children are not allowed. You haven't added any cots. You haven't added any extra beds. The maximum number of guests is 2.  Deposit Policy: The guest will be charged a prepayment of the total price of the reservation at any time.  Cancellation Policy: The guest will be charged the total price of the reservation if they cancel at any time.",
              "promotion": [],
              "room_remarks": [],
              "smoking_preferences": "",
              "rate_plan_code": 37364467
            },
            "taxes": [
              {
                "is_inclusive": false,
                "name": "Cleaning fee",
                "nights": 1,
                "persons": 1,
                "price_mode": "Per booking",
                "price_per_unit": "123.00",
                "total_price": "123.00",
                "type": "Service Charge"
              },
              {
                "is_inclusive": false,
                "name": "VAT (14%)",
                "nights": 1,
                "persons": 1,
                "price_mode": "Per booking",
                "price_per_unit": "7.56",
                "total_price": "7.56",
                "type": "Value Added Tax (VAT)"
              }
            ],
            "services": [],
            "amount": "184.56",
            "days": { "2025-10-30": "54.00" },
            "booking_room_id": "91564388-492e-4ab9-91ec-ea671b642fd3",
            "rate_plan_code": "2DRM",
            "room_type_code": "STR",
            "guests": [{ "name": "Bambang", "surname": "Suherma" }],
            "occupancy": {
              "children": 0,
              "adults": 1,
              "infants": 0,
              "ages": []
            },
            "ota_commission": "0.00",
            "checkin_date": "2025-10-30",
            "checkout_date": "2025-10-31",
            "is_cancelled": false
          },
          {
            "internal_room_id": 69,
            "booking_status": "Modify",
            "booking_id": "eebd0c4b-0bdb-4b19-90fb-2f1e31fc45b0",
            "meta": {
              "days_breakdown": [
                {
                  "amount": "54.00",
                  "date": "2025-10-30",
                  "promotion": null,
                  "rate_code": 37364467,
                  "rate_plan": "4ec3b7c2-29df-44d0-966b-bff6593e99c3"
                }
              ],
              "cancel_penalties": [
                {
                  "amount": "61.56",
                  "currency": "USD",
                  "from": "2025-10-30T02:31:11"
                }
              ],
              "additional_details": [],
              "booking_com_room_index": 436,
              "meal_plan": "Breakfast costs US$14 per person per night.\nDinner costs US$35 per person per night.",
              "policies": "Children and Extra Bed Policy: Children are not allowed. You haven't added any cots. You haven't added any extra beds. The maximum number of guests is 2.  Deposit Policy: The guest will be charged a prepayment of the total price of the reservation at any time.  Cancellation Policy: The guest will be charged the total price of the reservation if they cancel at any time.",
              "promotion": [],
              "room_remarks": [],
              "smoking_preferences": "",
              "rate_plan_code": 37364467
            },
            "taxes": [
              {
                "is_inclusive": false,
                "name": "Cleaning fee",
                "nights": 1,
                "persons": 1,
                "price_mode": "Per booking",
                "price_per_unit": "123.00",
                "total_price": "123.00",
                "type": "Service Charge"
              },
              {
                "is_inclusive": false,
                "name": "VAT (14%)",
                "nights": 1,
                "persons": 1,
                "price_mode": "Per booking",
                "price_per_unit": "7.56",
                "total_price": "7.56",
                "type": "Value Added Tax (VAT)"
              }
            ],
            "services": [],
            "amount": "184.56",
            "days": { "2025-10-30": "54.00" },
            "booking_room_id": "0f512c61-43f5-4409-a5c5-ed3a0c6b3064",
            "rate_plan_code": "",
            "room_type_code": "",
            "guests": [{ "name": "Bambang", "surname": "Suherma" }],
            "occupancy": {
              "children": 0,
              "adults": 1,
              "infants": 0,
              "ages": []
            },
            "ota_commission": "0.00",
            "checkin_date": "2025-10-30",
            "checkout_date": "2025-10-31",
            "is_cancelled": false
          },
          {
            "internal_room_id": 70,
            "booking_status": "Cancelled",
            "booking_id": "91564388-492e-4ab9-91ec-ea671b642fd3",
            "meta": {
              "days_breakdown": null,
              "cancel_penalties": null,
              "additional_details": null,
              "booking_com_room_index": 0,
              "meal_plan": "",
              "policies": "",
              "promotion": null,
              "room_remarks": null,
              "smoking_preferences": "",
              "rate_plan_code": null
            },
            "taxes": null,
            "services": null,
            "amount": "",
            "days": null,
            "booking_room_id": "",
            "rate_plan_code": "",
            "room_type_code": "",
            "guests": null,
            "occupancy": {
              "children": 0,
              "adults": 0,
              "infants": 0,
              "ages": null
            },
            "ota_commission": "",
            "checkin_date": "",
            "checkout_date": "",
            "is_cancelled": false
          }
        ],
        "secondary_ota": null,
        "occupancy": { "children": 0, "adults": 2, "infants": 0, "ages": [] },
        "acknowledge_status": "pending",
        "ota_commission": "0.00",
        "ota_reservation_code": "6700672290",
        "comments": "",
        "special_requests": "",
        "raw_message": ""
      }
    }
  ]
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://cakrasoft.net/api/v1/cm_service/ReceiveBookingWebhook/CKR',
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