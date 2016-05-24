# Getting started

##For the test environment:

### PayEx Admin
To start implementing, there are a few things that must be done to the PayEx Merchant Account that is going to be used with PayEx Checkout.


[The test PayEx Admin](http://test-secure.payex.com/Admin/MerchantDetailsMerchant.aspx)

In _Merchant Profile_: edit the configuration with the following settings:

* **Hash Algorithm** : `Md5`
* **Transaction callback** : `true`
* **Callback method** : `Url`
* **Transaction callback URL/Mail** : `http://callback-hub.test.storefront.no/`

PLACEHOLDER PICTURE

Get the _encryption key_, either by creating a new one, or by obtaining the existing one (not possible in the admin), we need this, and the _Merchant account_(number) later

----

### Payex Checkout Admin
Depending on whether your test shop is using http or https, you use the credentials retrieved from your PayEx contact person to log into the following:

* [HTTP](http://checkout-admin-master.twins.bugano.net/)
* [HTTPS](https://checkout-admin.staging.okb.no/)

This choice determines what "environment" of URLs you must use throughout this tutorial.

After you are logged in, edit the your test shops' settings.

#### Shop settings

* **Shop name** : The name that will be displayed on various places for a consumer
* **Shop base url** : The URL of the base of your shop, without any subdirectories. This is used in authentication requests from the front end i.e. https://myshop.com
* **Asynchrounous callback url** (optional) : The url to which PayEx Checkout will POST [Callback notifications](callbacks) to.
* **Country** : Determines what legal rules to apply regarding invoicing.
* **Currency** : The _currency_ of all [payments](payment) for this shop.
* **Culture code** : The display language for the payment window, defined as [Culture Codes](https://msdn.microsoft.com/en-us/library/ee825488(v=cs.20).aspx)
* **PayEx account number** : The _Merchant account_ number (as found in [PayEx Admin](#payex-admin))
* **PayEx account encryption key** : The _encryption key_ (as found in [PayEx Admin](#payex-admin))
* **Autopay max amount** (deprecated) : Pay no attention to this value, it is not in use.

#### Authentication Keys

There are 2 authentication keys that are required to put in your application to use PayEx Checkout.
After they are generated, they can not be retrieved, so store them somewhere safe.

* **frontend-key** : Your publishable key, this key is visible in the source of the shop. If the **Shop base url** is changed, the _frontend-key_ **MUST** be regenerated.

* **backend-key** : Your secret server to server key. Used for [authenticating your](api#backend-authentication) back end requests to the [Checkout Api](api)


------

#Implementation
There are two areas that your shop must have integration to PayEx Checkout

## Frontend

PayEx Checkout frontend is a script that bootstraps the payment process when a special button is clicked.

### Adding the script
Start by adding the PayEx Checkout script to your page.

**If HTTPS**
```html
<script src="https://checkout.staging.okb.no/Content/js/payex-checkout.min.js"></script>
```
**If HTTP**
```html
<script src="https://checkout-master.twins.bugano.net/Content/js/payex-checkout.min.js"></script>
```

### Initial configuration
Choose the button that you want to start the checkout process and add the id `pxc-button`. Then add the disable attribute - the PayEx Checkout JavaScript will enable it when it is properly loaded.
The button **MUST** be contained within a html `<form>` that POSTs to your server.

```HTML
<button id="pxc-button" disabled>Pay</button>
```

To configure PayEx Checkout you need to initialize it through the pxc.config function and pass in an configuration object with your frontend key, amount, order id and order lines.
<br/>Make sure you include this configuration after the PayEx Checkout script you included in the previous step.

```JavaScript
pxc.config({
  amount: your_amount,
	key: "your_frontend-key",
	orderId: "your_orderId",
	orderLines: [{
		itemPrice: your_item_price,
		description: "your_item_description",
		quantity:  your_item_price
	}]
});
```


When the payment process completes successfully, a hidden input element with a `payment-id` will be injected to the form and sent alongside any other input elements as normal to the defined form-action.
A successful request requires that the _Referer_ Header matches the one entered in the [shop settings](#shop-settings). This headers' inclusion is taken care of by the checkout-script.


## Backend
After a successful payment, the shops web server receives the `payment-id` from the form-post. This ID is the key to actually capturing the now authorized payment.
To do this you have to implement a server side http request.
All requests to the [API](api) uses authentication.
using cURL or other http libraries, construct and send a [Capture](transaction#capture) request to the url:

* HTTPS : <https://checkout-api.staging.okb.no/payments/YOUR PAYMENT-ID/transactions>
* HTTP  : <http://checkout-api-master.twins.bugano.net/payments/YOUR PAYMENT-ID/transactions>

### Example

```csharp
string payment_id = HttpContext.Current.Request.Form["payment-id"];
string backend_key = "mysupersecretbackendkey";
decimal order_total_price = 100M;

HttpClient httpClient = new HttpClient();
httpClient.DefaultRequestHeaders.Add("Authorization", "Token " + backend_key);

string json = Newtonsoft.Json.JsonConvert.SerializeObject(
    new
    {
        type = "Capture",
        amount = order_total_price
    });
StringContent content = new StringContent(json, Encoding.UTF8, "application/json");

var result = httpClient.PostAsync($"https://checkout-api.staging.okb.no/{payment_id}/transactions/", content).Result;

if (result.StatusCode == HttpStatusCode.OK)
    //the payment is captured.
```
You may now test.



#Before you go live

##Checklist

1. SSL installed on your site
1. Init order via Checkout with form action url
1. Save `payment-id` to your backend (appended to form on return from an authorized order from checkout)
1. Verify that you have implemented order amount check functionality via `payment-id` on the payment resource to ensure that the payment form has not been tampered with
1. Verify that you have implemented capture-transaction functionality to ensure economic settlement on the ordered amount
1. Verify that you have implemented credit and cancel-transaction functionality to ensure that the value chain is ok

Change your URLs and credentials to production values

* Frontend JS: <https://checkout.okb.no/Content/js/payex-checkout.min.js>
* Backend API: <https://checkout-api.okb.no/>
* Admin URL:   <https://checkout-admin.okb.no/>

Login to Checkout Admin and generate your production API keys.
Update your configuration and verify that a live transaction has been completed and verified by PayEx backoffice personell before you GO LIVE.
