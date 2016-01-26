An implementer may request a new capture-transaction. This captures any authorized funds from the transaction.

### Method, parameters
Method:    `POST`

Resource:  `api/orders/{orderid}/transactions/`

Headers:

    Content-Type: application/json
    Authorization: Token M2EwNWFkZjgtNGFhMy00ZGYyLWIzOWMtYmVkNmY2YTc1YTdkOjQ0Mzg5MgdlLTQ1NDktNGMxOC05Mjk5LTkyZjMxY2VhYTllNw==

Body:

    {
      "transaction-type" : "Capture"
      "transaction-amount" {amount}
    }

Where `orderid` is the token your purchase-endpoint is receiving from checkout.js

Where `amount` is the amount to capture. Must not exceed remaining authorized amount.

### Expected responses
Status code: `201`

Body:

    {"reference":"8135598"}
The reference is the ID of the transaction that can be used inside Payex Admin to do more actions on the order.

### Possible errors
`404 Not Found` :
 * When the order is not found in the system

`400 Bad Request`
 * When the request is malformed
 * When the transaction-amount exceeds remaining authorized amount
 * when the order is not completed
