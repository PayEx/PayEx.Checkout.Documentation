An implementer may call /cancel to cancel the transaction and release any reserved funds

### Method, parameters
Method:    `POST`

Endpoint:  `/api/cancel`

Headers:

    Content-Type: application/json
    Authorization: Token M2EwNWFkZjgtNGFhMy00ZGYyLWIzOWMtYmVkNmY2YTc1YTdkOjQ0Mzg5MgdlLTQ1NDktNGMxOC05Mjk5LTkyZjMxY2VhYTllNw==

Body:

    {"PaymentToken":"bbe947b5-0150-465a-a153-ec5bf99f888d"}

The PaymentToken here is the token your purchase-endpoint is receiving from checkout.js

### Expected responses

Status code:

    200

### Possible errors
`404 Not Found` :
 * When the order is not found in the system

`410 Gone` :
* When the order is already captured
* When the order is already cancelled

`403 Bad Request`
* When the cancel request is malformed
* When the order attempted cancelled is not in a cancellable state.
