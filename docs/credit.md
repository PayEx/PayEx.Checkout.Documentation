An implementer may request a new credit-transaction. This can credit any captured funds from the order.

### Method, parameters
Method:    `POST`

Resource:  `api/orders/{orderid}/transactions/`

Headers:

    Content-Type: application/json
    Authorization: Token M2EwNWFkZjgtNGFhMy00ZGYyLWIzOWMtYmVkNmY2YTc1YTdkOjQ0Mzg5MgdlLTQ1NDktNGMxOC05Mjk5LTkyZjMxY2VhYTllNw==

Body:

    {
      "transaction-type" : "Credit"
      "transaction-amount" {amount}
    }

Where `orderid` is the token your purchase-endpoint is receiving from checkout.js

Where `amount` is the amount to be credited. Must not exceed the total of all captures on the order.

### Expected responses
Status code: `201`

### Possible errors
`404 Not Found` :
 * When the order is not found in the system

`403 Bad Request`
 * When the request is malformed
 * When the transaction-amount exceeds the captured amount
