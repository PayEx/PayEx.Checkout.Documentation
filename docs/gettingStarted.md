#3.1 Getting started

PayEx Checkout consists of two parts: A frontend and a backend. Both parts need to be implemented. Let's deal with the frontend first.

##3.1 Adding the script
Start by adding the PayEx Checkout script to your page.
```html
<script src="https://checkout.okb.no/Content/js/payex-checkout.min.js"></script>
```

## 3.1 Initial configuration
Choose the button that you want to start the checkout process and add the id `pxc-button`. Then add the disable attribute - the PayEx Checkout JavaScript will enable it when it is properly loaded.
```HTML
<button id="pxc-button" disabled>Pay</button>
```

To configure PayEx Checkout you need to initialize it through the pxc.config function and pass in an configuration object with your API token, amount, order id and order lines.
<br/>Make sure you include this configuration after the PayEx Checkout script you included in the previous step.

```JavaScript
pxc.config({
  amount: your_amount,
	token: "your_api_token"
	orderId: "your_orderId",
	orderLines: [{
		itemPrice: your_item_price,
		description: "your_item_description",
		quantity:  your_item_price
	}]
});
```

Now add the id to the pxc-button to the button chosen earlier.
```HTML
<button id="pxc-button" disabled>Pay</button>
```
