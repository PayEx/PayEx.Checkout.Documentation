An implementer may request this resource to obtain the delivery address of the order.
if the initial order is initiated with [requires-physical-address](configurationReference/#requires-physical-address) and is paid with _invoice_, any shipping **MUST** be delivered to this address.

### Properties of an address
 * **uri**
    * the uri to this one resource.
* **city**
    * the city or area where the recipient wants items sendt to.
* **coAddres**




### Resource URI
Resource:  `/payments/{paymentId}/address/`, Where `paymentId` is the token recieved from the paymentsession through checkout.js.
This resource requires authentication, authorizing the owner of the payment. see [Authentication](authentication/#back-end-authentication)

#### Supported HTTP Verbs
Method:    `GET`

##### Example request

    GET scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb/address HTTP/1.1
    Accept: application/json
    Authorization: Token secretencodedtokenthatyoumustneverspillontotheinternet==

##### response:

    HTTP/1.1 200 OK
    Content-Type: application/json
    {
      "uri": "scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb/address",
      "city": "CityTown",
      "coAddress": null,
      "country": "Norway",
      "email": "erik+01@okb.no",
      "fullName": "Place Holder",
      "postalCode": "0001",
      "streetAddress": "The Actual Street 5c"
    }

##### Possible other HTTP status codes
 * `404 Not Found`
 * `401 Unauthorized`
