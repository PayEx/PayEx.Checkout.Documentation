#Go live procedure

## Production-account

In order to enable PayEx Checkout in production you need

  * A PayEx Merchant [Production-account](https://secure.payex.com/admin) with access to PayEx Checkout
  * Access to Checkout Admin in `production` environment.

__If you do not meet some or any of there requirements, please contact <sales@payex.com>__

##Checklist

![Screenshot](img/sequence_diagram.png)

Before you go live you need to install a SSL certificate on your site and;

1. Init order via Checkout with form action url
2. Save `payment-id` to your backend (appended to form on return from an authorized order from checkout)
3. Verify that you have implemented order amount check functionality via `payment-id` on the payment resource to ensure that the payment form has not been tampered with
4. Verify that you have implemented capture, credit and cancel-transaction functionality to ensure economic settlement on the ordered amount and a sound value chain


Change your URLs and credentials to production values

* Frontend JS: <https://checkout.okb.no/Content/js/payex-checkout.min.js>
* Backend API: <https://checkout-api.okb.no/>
* Admin URL:   <https://checkout-admin.okb.no/>

Login to Checkout Admin and generate your production API keys.
Update your configuration and verify that a live transaction has been completed and verified by PayEx backoffice personell before you GO LIVE.