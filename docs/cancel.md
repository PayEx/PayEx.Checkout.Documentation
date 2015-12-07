## Cancel
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
