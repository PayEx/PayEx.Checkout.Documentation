An implementer may request this resource to obtain the delivery address of the order.
It is expected that the item(s) purchased is being sent to this address, if the implementer have initiated the transaction with the property `requiresDigitalAddress` or `requiresPhysicalAddress` set to true.

### Method, parameters
Method:    `GET`

Resource:  `api/orders/{orderid}/address`

Headers:

    Authorization: Token M2EwNWFkZjgtNGFhMy00ZGYyLWIzOWMtYmVkNmY2YTc1YTdkOjQ0Mzg5MgdlLTQ1NDktNGMxOC05Mjk5LTkyZjMxY2VhYTllNw    
    Accept: application/json

Where `orderid` is the token your purchase-endpoint is receiving from checkout.js

### Example response
    {
     "city": "Oslo",
     "coAddress": "C/O Ares coAddress",
     "country": "Norge",
     "email": "test@example.com",
     "firstName": "Are",
     "fullName": "Are Eriksen",
     "lastName": "Eriksen",
     "mobilePhoneNumber": "01010101010",
     "postalCode": "3179",
     "streetAddress": "Strandsveien 560"
    }
