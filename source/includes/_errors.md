# Errors

The Lalamove API uses the following error codes:

| Error Code                     | Message                       | Meaning                                                                                       |
| ------------------------------ | ----------------------------- | --------------------------------------------------------------------------------------------- |
| `400` -- Bad Request           | `ERR_MALFORMED_JSON_BODY`     | Your request is invalid. Make sure the body is a valid JSON string.                           |
| `401` -- Unauthorized          |                               | Your API key is wrong. Make sure to follow [instructions in Authentication](#authentication). |
| `402` -- Payment Required      | `ERR_INSUFFICIENT_CREDIT`     | You have insufficient Credit.                                                                 |
| `403` -- Forbidden             |                               | The Order's or Driver's details requested is not unauthorized.                                |
| `404` -- Not Found             |                               | The specified Order or Driver could not be found.                                             |
| `409` -- Conflict              | `ERR_CANCELLATION_FORBIDDEN`  | Cancellation does not meet certain constraints.                                               |
| `409` -- Conflict              | `ERR_DELIVERY_MISMATCH`       | Stops and Deliveries mismatch.                                                                |
| `409` -- Conflict              | `ERR_INSUFFICIENT_STOPS`      | Not enough stops (Number of stops should be more than 1).                                     |
| `409` -- Conflict              | `ERR_TOO_MANY_STOPS`          | Reached maximum stops.                                                                        |
| `409` -- Conflict              | `ERR_INVALID_COUNTRY`         | Incorrect country.                                                                            |
| `409` -- Conflict              | `ERR_INVALID_CURRENCY`        | Invalid currency.                                                                             |
| `409` -- Conflict              | `ERR_INVALID_LOCALE`          | Invalid locale.                                                                               |
| `409` -- Conflict              | `ERR_INVALID_PARAMS`          | General validation error.                                                                     |
| `409` -- Conflict              | `ERR_INVALID_PHONE_NUMBER`    | Invalid phone number.                                                                         |
| `409` -- Conflict              | `ERR_INVALID_SCHEDULE_TIME`   | Invalid schedule time.                                                                        |
| `409` -- Conflict              | `ERR_INVALID_SERVICE_TYPE`    | Inputted service type is not yet supported.                                                   |
| `409` -- Conflict              | `ERR_INVALID_SPECIAL_REQUEST` | Inputted special requests are not yet supported.                                              |
| `409` -- Conflict              | `ERR_OUT_OF_SERVICE_AREA`     | Out of service area.                                                                          |
| `409` -- Conflict              | `ERR_PRICE_MISMATCH`          | Inputted price mismatched.                                                                    |
| `409` -- Conflict              | `ERR_REQUIRED_FIELD`          | Missing required fields.                                                                      |
| `409` -- Conflict              | `ERR_REVERSE_GEOCODE_FAILURE` | Fail to reverse from address to location. (**TODO: explain**)                                 |
| `409` -- Conflict              | `ERR_INVALID_PAYMENT_METHOD`  | Invalid payment method.                                                                       |
| `409` -- Conflict              | `ERR_INV ALID_FLEET_PRIORITY` | Invalid fleet priority.                                                                       |
| `429` -- Too Many Requests     |                               | You're sending in too many requests.                                                          |
| `500` -- Internal Server Error |                               | We had a problem with our server. Try again later.                                            |
