#4.1 The payment resource.
An implementer may request this resource to obtain the root resource describing a payment.
All other resources related to the payment are found on the resource itself or linked to from this resource.

The uri of this resource is the base uri to request all other resources related to the payment.

##4.1.1 Properties of payment
 * **uri**
    * the uri to this resource.
 * **cancelled**
    * see [cancel transaction](../transaction/#cancel)
    * `decimal`
    * the amount that has been cancelled on the payment.
    * This amount is released from `reserved`    
 * **captured**
    * see [capture transaction](../transaction/#capture)
    * `decimal`
    * the amount that have been captured.
    * also describes the maximum amount that can be credited.
 * **credited**
    * see [credit transaction](../transaction/#credit)
    * `decimal`
    * the amount that has been credited.
 * **originalAmount**
    * see [authorize transaction](../transaction/#authorize)    
    * `decimal`
    * the amount initially authorized on the payment.
 * **currency**
    * see [transaction currency](../transaction/#currency)    
    * `NOK` or `SEK`
    * the currency of all `transactions` and amounts related to this `payment`
 * **transactions**
    * ordered list of all [transactions](../transaction) executed on the payment.
 * **address**
    * link this payments' [address ](../address) resource.
    * if the initial order is initiated with [requires-physical-address](../configurationReference/#requires-physical-address) and is paid with invoice, any shipping MUST be delivered to this address.



##4.1.2 Resource URI
Resource:  `/payments/{paymentId}`, Where `paymentId` is the token recieved from the paymentsession through checkout.js
This resource requires authentication, authorizing the owner of the payment. see [Authentication](../authentication/#back-end-authentication)

##4.1.2.1 Supported HTTP Verbs
Method:    `GET`


##4.1.2.1.1 Example request

    GET scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb HTTP/1.1
    Accept: application/json
    Authorization: Token secretencodedtokenthatyoumustneverspillontotheinternet==

##4.1.2.1.2 response:

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
      "uri": "scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb",
      "cancelled": 0,
      "captured": 199,
      "credited": 0,
      "currency": "NOK",
      "originalAmount": 199,
      "reserved": 0,
      "transactions": [
      {
        "uri": "scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb/transactions/9450400",
        "currency": "NOK",
        "amount": 199,
        "type": "Authorize"
      },
      {
        "uri": "scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb/transactions/9450402",
        "currency": "NOK",
        "amount": 199,
        "type": "Capture"
      }
      ],
      "address": {
      "uri": "scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb/address"
      }
    }

##4.1.2.1.3 Possible other HTTP status codes
 * `404 Not Found`
 * `401 Unauthorized`
