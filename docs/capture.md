An implementer may call /capture to complete the transaction in the payment system to capture reserved funds from the consumer

### Method, parameters
Method:    `POST`

Endpoint:  `/api/capture`

Headers:

    Content-Type: application/json
    Authorization: Token M2EwNWFkZjgtNGFhMy00ZGYyLWIzOWMtYmVkNmY2YTc1YTdkOjQ0Mzg5MgdlLTQ1NDktNGMxOC05Mjk5LTkyZjMxY2VhYTllNw==

Body:

    {"paymentToken":"bbe947b5-0150-465a-a153-ec5bf99f888d","totalAmount":199}
The `paymentToken` is the token your purchase-endpoint is receiving from checkout.js

### Expected responses
Status code:

    200

Body:

    {"reference":"8135598"}
The reference is the ID of the transaction that can be used inside Payex Admin to do more actions on the order.

### Possible errors
`404 Not Found` :
 * When the order is not found in the system

`409 Conflict` :
* When the amount on the initial order is not identical to the amount sent in the capture request

`403 Bad Request`
* When the capture request is malformed
* When the order attempted captured is not in a captureable state.
 * Already captured
 * Already cancelled
 * Not completed
