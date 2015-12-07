An implementer may use this endpoint to obtain the delivery address of the order.
It is expected that the item is being sent to this address, if the implementer have initiated the transaction with the property `requiresDigitalAddress` or `requiresPhysicalAddress` set to true.

### Method, parameters

    GET /address?orderid=your-order-token
    Authorization: Token your-token    
    Accept: application/json

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
