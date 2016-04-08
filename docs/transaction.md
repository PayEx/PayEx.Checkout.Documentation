An implementer may request this resource to obtain the spesifics of a single transaction in a [payments](payment)' transaction chain

### Properties of a transaction
 * **uri**
    * the uri to this one resource.
 * **type**
       * the [transaction type](#transaction-types).

 * **amount**
    * `decimal`
    * the amount in this `transaction`
 * **currency**
    * see [transaction currency](#currency)    
    * `NOK` or `SEK`
    * the currency of this `transaction`

## Transaction-types
#### Cancel
A cancel transaction, this releases all available [reseved](#authorize) funds.

#### Capture
A capture transaction, it captures funds from [reseved](#authorize).

#### Credit
A credit transaction, it credits previously  [captured](#capture), paying them back to the consumer.

#### Authorize
An authorize transaction, all transactions available in the api for a api-consumer have this transaction. It is not possible to repeat this transaction.
This transaction reserves funds, making them available for [capture](#capture) or [cancel](#cancel)

### Resource URI
Resource:  `/payments/{paymentId}/transactions/{transactionId}`, Where `paymentId` is the token recieved from the paymentsession through checkout.js and the `transactionId` is the unique ID for this transaction
This resource requires authentication, authorizing the owner of the payment. see [Authentication](authentication/#back-end-authentication)


#### Supported HTTP Verbs
Method:    `GET`


##### Example request
```HTTP
GET scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb/transactions/9450400 HTTP/1.1
Accept: application/json
Authorization: Token secretencodedtokenthatyoumustneverspillontotheinternet==
```
##### response:
```HTTP
HTTP/1.1 200 OK
Content-Type: application/json

{    
  "uri": "scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb/transactions/9450400",
  "currency": "NOK",
  "amount": 199,
  "type": "Authorize"  
}
```
##### Possible other HTTP status codes
 * `404 Not Found`
 * `401 Unauthorized`
