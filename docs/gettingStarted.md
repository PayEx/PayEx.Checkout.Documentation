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

Get the _encryption key_, either by creating a new one, or by obtaining the existing one (not possible in the admin), we need this, and the _Merchant account_(number) later

### Payex Checout Admin
Depending on whether your test shop is using http or https, you use the credentials retrieved from your PayEx contact person to log into the following:

* [HTTP](http://checkout-admin-master.twins.bugano.net/)
* [HTTPS](https://checkout-admin.staging.okb.no/)

This choice determines what "environment" of URLs you must use throughout this tutorial.

After you are logged in, edit the your test shops' settings.

* **Shop name** : The name that will be displayed on various places for a consumer
* **Shop base url** : The URL of the base of your shop, without any subdirectories. This is used in authentication requests from the front end i.e. https://myshop.com
* **Asynchrounous callback url** (optional) : The url to which PayEx Checkout will POST [Callback notifications](callbacks) to.
* **Country** : Determines what legal rules to apply regarding invoicing.
* **Currency** : The _currency_ of all [payments](payment) for this shop.
* **Culture code** : The display language for the payment window, defined as [Culture Codes](https://msdn.microsoft.com/en-us/library/ee825488(v=cs.20).aspx)
* **PayEx account number** : The _Merchant account_ number (as found in [PayEx Admin](#payex-admin))
* **PayEx account encryption key** : The _encryption key_ (as found in [PayEx Admin](#payex-admin))
* **Autopay max amount** (deprecated) : _Pay no attention to this value, it is not in use._  



## Frontend

### Adding the script
Start by adding the PayEx Checkout script to your page.
```html
<script src="https://checkout.okb.no/Content/js/payex-checkout.min.js"></script>
```

### Initial configuration
Choose the button that you want to start the checkout process and add the id `pxc-button`. Then add the disable attribute - the PayEx Checkout JavaScript will enable it when it is properly loaded.
```HTML
<button id="pxc-button" disabled>Pay</button>
```

To configure PayEx Checkout you need to initialize it through the pxc.config function and pass in an configuration object with your API token, amount, order id and order lines.
<br/>Make sure you include this configuration after the PayEx Checkout script you included in the previous step.

```JavaScript
pxc.config({
  amount: your_amount,
	token: "your_api_token",
	orderId: "your_orderId",
	orderLines: [{
		itemPrice: your_item_price,
		description: "your_item_description",
		quantity:  your_item_price
	}]
});
```
