# Getting started
## 1. Adding the script
Start by adding the PayEx Checkout script to your page.
```JavaScript
<script src="checkout.okb.no/content/js/payex-checkout.min.js"></script>
```

## 2. Initial configuration
Choose the button you want to start checkout process and disable it, the PayEx checkout will enable it when it is properly loaded.
```HTML
<button disabled>Pay</button>
```
Now you have 2 options; either configure PayEx Checkout with JavaScript or HTML attributes. The choice is up to and what you feel work best with your solution, but if you have an application that is heavily dependent on JavaScript, we recommend you use the JavaScript configuration, because it gives you more control when and where PayEx Checkout is configured. Please note that mixing both JavaScript and HTML attributes configurations wont work.

### Configuration with JavaScript
To configure PayEx Checkout with JavaScript use the pxc.config function and pass in an object with your API token and amount. Make sure you include this configuration after the PayEx Checkout script you included in the previous step.
```JavaScript
pxc.config({
    amount: your_amount,
    token: "your_api_token"
});
```
Now added the id pxc-button to the button chose earlier.
```HTML
<button id="pxc-button" disabled>Pay</button>
```
### Configuration with html attributes
To configure the application with HTML attributes start by adding
```HTML
<button data-pxc data-pxc-amount="your_amount" data-pxc-token="your_api_token">Pay</button>
```
You should now be able to make a purchase with PayEx checkout, if you have any question please don't hesitate to contact us on drift@okb.no. For further options please continue to the configuration reference section below.
