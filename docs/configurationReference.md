#Configuration reference
##Defaults
```JSON
{
  buttonSelector: "#pxc-button",
  orderId: null,
  amount: null,
  key: null,
  requiresDigitalAddress: false,
  requiresPhysicalAddress: false,
  orderLines: []
}
```

##Amount (required)
Amount is the total price of an order (included shipping).

Default property: `null` <br/>
JavaScript property name: `amount` <br/>
JavaScript type: `number`

##Frontend key (required)
In order to authenticate your solution with PayEx Checkout you will need a frontend key, this key can be found in the [PayEx Checkout admin](credentials#authentication-keys) user interface.

Default property: `null` <br/>
JavaScript property name: `key` <br/>
JavaScript type: `string`

##Order Id (required)
Order Id gives you the option to add a third party reference to PayEx Checkout that will be attached to the transaction and will be presented as order id on the invoice if end user chooses to pay with invoice.
This will give the opportunity to query PayEx Checkout APIs with your order id to find transactions and other data.

Default property: `null` <br/>
JavaScript property name: `orderId` <br/>
JavaScript type: `string`

##Order lines (required)
Providing order lines will improve the presentations of the invoice.

###Order lines - Item price (required)
Sets item price for the order line.

JavaScript property name: `itemPrice` <br/>
JavaScript type: `number`

###Order lines - Description (required)
Sets description for the order line.

JavaScript property name: `description` <br/>
JavaScript type: `string`

###Order lines - Quantity (required)
Sets quantity for the order line.

JavaScript property name: `quantity` <br/>
JavaScript type: `number`

###Order lines - Vat rate
Sets vat rate for the order line.

Default property: 25 <br/>
JavaScript property name: `vatRate` <br/>
JavaScript type: `number`

###Example

```JavaScript
{
  ...
  orderLines: [
      {
          itemPrice: 499,
          description: "Super Fit Treningsbukse",
          quantity: 2
      },
      {
          itemPrice: 999,
          description: "Ultra Jumper Treningsjakke",
          vatRate: 8,
          quantity: 1
      }
  ]
}
```

##Requires digital address
If set to true, the users email will be made available through the [backend APIs](address) after the checkout process is completed.

Default property: `false` <br/>
JavaScript property name: `requiresDigitalAddress` <br/>
JavaScript type: `boolean`

##Requires physical address
If set to true, PayEx Checkout will acquire the user's physical delivery address in the checkout process. After the checkout process if completed the address will be made available through the [backend APIs.](address)

Default property: `false` <br/>
JavaScript property name: `requiresPhysicalAddress` <br/>
JavaScript type: `boolean`

##Button Selector
Changes the selector that PayEx use to find the button that start the checkout process. Please note that the selector provide must be supported by the [Document.querySelector()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector).

Default property: `"#pxc-button"` <br/>
JavaScript property name: `buttonSelector` <br/>
JavaScript type: `string`
