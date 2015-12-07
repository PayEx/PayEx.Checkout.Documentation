# After purchase api calls

## Capture
### Description and purpose
An implementer may call /capture to complete the transaction in the payment system to capture reserved funds from the consumer

### Method, parameters
    POST /api/capture
### Expected responses
 {"Captured"}
### Possible errors
    {"Not found"}
    {"Cancelled"},
    {"Already captured"}


## Cancel

### Description and purpose
An implementer may call /cancel to cancel the transaction and release any reserved funds
This is done with a body like this:

### Method, parameters
   POST /cancel

### Expected responses
   {"OK"}

### Possible errors
    {"Not found"},
    {"Already cancelled"},
    {"Already captured"}


## Address
### Description and purpose
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
