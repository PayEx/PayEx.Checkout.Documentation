#3.1 Getting started
##3.1.1 Adding the script
Start by adding the PayEx Checkout script to your page.

    <script src="https://checkout.okb.no/Content/js/payex-checkout.min.js"></script>

##3.1.2 Initial configuration single orderline

Choose the button of your liking that you want to start the checkout process with, and disable it - the PayEx Checkout javascript will enable it when it is properly loaded.

    <button disabled>Pay</button>

Now you have 2 options; either configure PayEx Checkout with JavaScript or HTML attributes. The choice is up to you and what you feel work best with your solution, however if you have an application that is heavily dependent on JavaScript, we recommend that you use the JavaScript configuration, 
because it gives you more control when and where PayEx Checkout is configured. 

*Please note that mixing both JavaScript and HTML attributes configurations won't work.*

###3.1.2.1 Configuration with JavaScript
To configure PayEx Checkout with JavaScript use the pxc.config function and pass in an object with your API token and amount. Make sure you include this configuration after the PayEx Checkout script you included in the previous step.

    pxc.config({
		orderId: your_orderId,
		description: your_description,
        amount: your_amount,
		token: "your_api_token"
    });

Now add the id to the pxc-button to the button chosen earlier.

    <button id="pxc-button" disabled>Pay</button>

###3.1.2.2 Configuration with html attributes
To configure the application with HTML attributes start by adding

    <button data-pxc data-pxc-orderId="your_orderId" data-pxc-description="your_description" data-pxc-amount="your_amount" data-pxc-token="your_api_token">Pay</button>

You should now be able to make a purchase with PayEx checkout, if you have any questions please don't hesitate to contact us. For further options please continue to the configuration [reference section](../configurationReference).

##3.1.3 Initial configuration several orderlines

Implemented during week 15.

	 
