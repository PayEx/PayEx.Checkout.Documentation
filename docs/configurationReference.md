# Configuration reference
## Defaults

    {
        buttonSelector: "#pxc-button",
        amount: null,
        token: null,
        requiresDigitalAddress: false,
        requiresPhysicalAddress: false
     }

## API Token (required)
In order to authenticate your solution with PayEx Checkout you will need an API token, this token can be found in the PayEx Checkout admin user interface.

Default property: null <br/>
HTML attribute name: data-pxc-token <br/>
JavaScript property name: token <br/>
JavaScript type: string

## Amount (required)
Amount is the total price of an order (included shipping).

Default property: null <br/>
HTML attribute name: data-pxc-amount <br/>
JavaScript property name: amount <br/>
JavaScript type: string

## Order Id (recommended)
Order Id gives you the option to add a third party reference to PayEx Checkout that will be attached to the transaction.
This will give the opportunity to query PayEx Checkout APIs with your order id to find transactions and other data.

Default property: null <br/>
HTML attribute name: data-pxc-order-id <br/>
JavaScript property name: orderId <br/>
JavaScript type: string

## Requires digital address
If set to true, the users email will be made available through the checkout APIs after the checkout process is completed.

Default property: false <br/>
HTML attribute name: data-pxc-requires-digital-address <br/>
JavaScript property name: requiresDigitalAddress <br/>
JavaScript type: boolean

## Requires physical address
If set to true, PayEx checkout will acquire the user's physical delivery address in the checkout process. After the checkout process if completed the address will be made available through the PayEx checkout APIs.

Default property: false <br/>
HTML attribute name: data-pxc-requires-physical-address <br/>
JavaScript property name: requiresPhysicalAddress <br/>
JavaScript type: boolean

## Button Selector
Changes the selector that PayEx use to find the button that start the checkout process. Please note that the selector provide must be supported by the [Document.querySelector()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector).

Default property: "#pxc-button" <br/>
JavaScript property name: buttonSelector <br/>
JavaScript type: string
