## Capture
An implementer may call /capture to complete the transaction in the payment system to capture reserved funds from the consumer

### Method, parameters
    POST /api/capture
### Expected responses
 {"Captured"}
### Possible errors
    {"Not found"}
    {"Cancelled"},
    {"Already captured"}
