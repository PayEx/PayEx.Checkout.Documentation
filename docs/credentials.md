#Credentials

##PayEx Admin
To start implementing, there are a few things that must be done to the PayEx Merchant Account that is going to be used with PayEx Checkout.

[The test PayEx Admin](http://test-secure.payex.com/Admin/MerchantDetailsMerchant.aspx)

In _Merchant Profile_: edit the configuration with the following settings:

* **Hash Algorithm** : `Md5`
* **Transaction callback** : `true`
* **Callback method** : `Url`
* **Transaction callback URL/Mail** : `http://callback-hub.test.storefront.no/`

Get the _encryption key_, either by creating a new one, or by obtaining the existing one (not possible in the admin), we need this, and the _Merchant account_(number) later

----

##Payex Checkout Admin
Depending on whether your test shop is using http or https, you use the credentials retrieved from your PayEx contact person to log into the following:

* [HTTP](http://checkout-admin-master.twins.bugano.net/)
* [HTTPS](https://checkout-admin.staging.okb.no/)

This choice determines what "environment" of URLs you must use throughout this tutorial.

After you are logged in, edit the your test shops' settings.

###Shop settings

* **Shop name** : The name that will be displayed on various places for a consumer
* **Shop base url** : The URL of the base of your shop, without any subdirectories. This is used in authentication requests from the front end i.e. https://myshop.com
* **Asynchrounous callback url** (optional) : The url to which PayEx Checkout will POST [Callback notifications](callbacks) to.
* **Country** : Determines what legal rules to apply regarding invoicing.
* **Currency** : The _currency_ of all [payments](payment) for this shop.
* **Culture code** : The display language for the payment window, defined as [Culture Codes](https://msdn.microsoft.com/en-us/library/ee825488(v=cs.20).aspx)
* **PayEx account number** : The _Merchant account_ number (as found in [PayEx Admin](#payex-admin))
* **PayEx account encryption key** : The _encryption key_ (as found in [PayEx Admin](#payex-admin))
* **Autopay max amount** (deprecated) : Pay no attention to this value, it is not in use.

##Authentication Keys

There are 2 authentication keys that are required to put in your application to use PayEx Checkout.
After they are generated, they can not be retrieved, so store them somewhere safe.

* **Frontend-key**: Your publishable key, this key is visible in the source of the shop. If the **Shop base url** is changed, the _frontend-key_ **MUST** be regenerated.

* **Backend-key**: Your secret server to server key. Used for [authenticating your](backend#backend-authentication) back end requests to the [Checkout Api](backend)

