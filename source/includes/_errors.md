# Errors

The Lalamove API uses the following error codes:

| Error Code                     | Message                      | Meaning                                                                                       |
| ------------------------------ | ---------------------------- | --------------------------------------------------------------------------------------------- |
| `400` -- Bad Request           | `ERR_MALFORMED_JSON_BODY`    | Your request is invalid. Make sure the body is a valid JSON string.                           |
| `401` -- Unauthorized          |                              | Your API key is wrong. Make sure to follow [instructions in Authentication](#authentication). |
| `402` -- Payment Required      | `ERR_INSUFFICIENT_CREDIT`    | You have insufficient Credit.                                                                 |
| `403` -- Forbidden             |                              | The Order's or Driver's details requested is not unauthorized.                                |
| `404` -- Not Found             |                              | The specified Order or Driver could not be found.                                             |
| `409` -- Conflict              | `ERR_CANCELLATION_FORBIDDEN` | Cancellation does not meet certain constraints.                                               |
| `409` -- Conflict              | `ERR_INVALID_COUNTRY`        | Incorrect country.                                                                            |
| `409` -- Conflict              | `ERR_INVALID_PARAMS`         | General validation error.                                                                     |
| `409` -- Conflict              | `ERR_REQUIRED_FIELD`         | Missing required fields.                                                                      |
| `429` -- Too Many Requests     |                              | You're sending in too many requests.                                                          |
| `500` -- Internal Server Error |                              | We had a problem with our server. Try again later.                                            |
