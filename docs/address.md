#4.2 Address

An implementer may request this resource to obtain the delivery address of the order.
if the initial order is initiated with [requires-physical-address](../configurationReference/#requires-physical-address) and is paid with _invoice_, any shipping **MUST** be delivered to this address.

##4.2.1 Properties of an address
 * **uri**
    * the uri to this resource.
* **city**
    * the city or area where the recipient wants items sendt to.
* **coAddres**




##4.2.2 Resource URI
Resource:  `/payments/{paymentId}/address/`, Where `paymentId` is the token recieved from the paymentsession through checkout.js.
This resource requires authentication, authorizing the owner of the payment. see [Authentication](../authentication/#back-end-authentication)

##4.2.2.1 Supported HTTP Verbs
Method:    `GET`

##4.2.2.1.1 Example request

    GET scheme://domain.tld/api/payments/94ac4cde-5cb1-4609-938d-8c510bcef1bb/address HTTP/1.1
    Accept: application/json
    Authorization: Token secretencodedtokenthatyoumustneverspillontotheinternet==

##4.2.2.1.2 response:

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

##4.2.2.1.3 Possible other HTTP status codes
 * `404 Not Found`
 * `401 Unauthorized`
