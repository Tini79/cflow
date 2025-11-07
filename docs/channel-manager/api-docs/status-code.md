---
sidebar_position: 5
---

# API Response Status Codes

All API responses from the Cakrahub Booking Engine follow a standard structure:

## Default Response Structure

```json
{
	"StatusCode": 0,
	"Message": "Success",
	"Result": { /* response data or null */ }
}
```

- **StatusCode**: Indicates the status of the API call. `0` means success; other values indicate errors.
- **Message**: Human-readable message describing the result of the API call. Could be used as Toast Message.
- **Result**: Contains the main result. This is an object with the response data, or `null` if there is no result.

---

## Status Code Reference

| Code | Name                                 | Description                                      |
|------|--------------------------------------|--------------------------------------------------|
| 0    | Successfully                         | Request was successful                           |
| 1    | NotAuthorized                        | Not authorized / invalid or missing token         |
| 2    | InvalidDataFormat                    | Data format is invalid                            |
| 3    | ErrorCreateToken                     | Error occurred while creating token               |
| 4    | DataNotFound                         | Requested data not found                          |
| 5    | InvalidDataValue                     | Data value is invalid                             |
| 6    | DatabaseValueChanged                 | Database value has changed                        |
| 7    | DatabaseError                        | Database error                                    |
| 8    | EmptyRequireField                    | Required field is empty                           |
| 9    | PaymentDateCannotLowerThanIssuedDate | Payment date cannot be earlier than issued date   |
| 10   | SuccessfullyWithStatus               | Request was successful, with additional status    |
| 11   | DuplicateEntry                       | Duplicate entry detected                          |
| 12   | SubscriptionExpired                  | Subscription has expired                          |
| 13   | Unregistered                         | Not registered                                   |
| 500  | InternalServerError                  | Internal server error                             |
| 999  | OtherResult                          | Other/unknown result                              |

---

Use these codes to interpret the result of any API call. For error handling, check the `StatusCode` and `Message` fields in the response.

## Error Handling

When an error occurs, the API will return an appropriate HTTP status code along with an error message in the response body.