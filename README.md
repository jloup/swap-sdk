# Swap Widget

Demo: [https://swap.savitar.io/widget](https://swap.savitar.io/widget)

For direct API connection, please see [https://doc.savitar.io/api/](https://doc.savitar.io/api/)

## Index

1. **[Install](#install)**

    * [NPM](#npm)

2. **[Quick Start](#quick-start)**

    * [Initialize the client](#initialize-the-client)
    * [Modal mode](#mode-modal)
    * [Embed mode](#mode-embed)

3. **[Configurations](#configurations)**
    
    * [For wallets](#for-wallets)
    * [IOV](#iov)

4. **[Advanced](#advanced)**
    * [Callbacks](#callbacks)

5. **[About](#about)**

## Install
### NPM

`npm install --save https://github.com/savitar-exchange/swap-sdk.git` 

or 

`yarn add https://github.com/savitar-exchange/swap-sdk.git`

## Quick Start

### Initialize the client

```js
var Swap = require('swap-sdk');
// OR
import * as Swap from 'swap-sdk';

new Swap.Widget({
    type: 'modal'
}).init()
```

### Mode `modal`
This mode loads an overlay on the click of a button or a link with id `buttonId`.

```js
new Swap.Widget({
    type: 'modal',
    buttonId: 'swap-button',
})
.init()
```


### Mode `embed`
This mode loads the widget in the DOM node of your choice parametrized with `embedContainerId`

```js
new Swap.Widget({
    type: 'embed',
    embedContainerId: 'swap-widget',
})
.init()
```

## Configurations

List of parameters of Swap.Widget config:

```js
new Swap.Widget({
    type: 'embed',
    embedContainerId: 'swap-widget',
    config: {
      // input parameters here
    }
})
.init()
```

### For wallets

- `email` (optional): User email - `string`
- `email_editable` (optional): Allow user to change predefined email - `bool`
- `currency` (optional): Currency of the order  - `string`
- `order_type` (optional): `buy` | `sell` - `string`
- `amount` (optional): Amount of the order  - `float`
- `amount_currency` (optional): Currency of the order  - `string`
- `amount_editable` (optional): Allow user to modify amount - `bool`
- `delivery_address` (optional): Address to send ordered coins - `string`

### IOV

#### Buy a domain

- `payment_type`: `iov`,
- `email` (optional): User email - `string`
- `email_editable` (optional): Allow user to change predefined email - `bool`
- `delivery_address` (optional): Owner of the domain - `string`

#### Buy IOVs

- `currency`: `IOV`  - `string`
- `order_type`: `buy` - `string`
- `email` (optional): User email - `string`
- `email_editable` (optional): Allow user to change predefined email - `bool`
- `amount` (optional): Amount of the order  - `float`
- `amount_currency` (optional): `IOV` or `EUR`  - `string`
- `amount_editable` (optional): Allow user to modify amount - `bool`
- `delivery_address` (optional): Address to send ordered coins - `string`

## Buttons

Pay button with simple configuration

####  Attributes
- `svt-email`: User email - `string`
- `svt-email-editable`: Allow user to change predefined email - `bool`
- `svt-amount`: Amount to order - `float`
- `svt-amount-editable`: Allow user to modify amount - `bool`
- `svt-currency`: Select a currency - `string`
- `svt-order-type`: `buy` or `sell` - `bool`
- `svt-delivery-address`: Address to send ordered coins - `string`
- `svt-payment-type`: Payment type of widget (`merchant` / `exchange` / `iov` / `sell` ) - `string`

##### Example 

###### JS
```javascript
const widget = new Swap.Widget({
    payButtons: true,
    payButtonsStyle: true
})

widget.init()
```
###### HTML
```html
<button type='svt-btn' svt-amount='50' svt-currency='usdt' svt-email='user@email.com' svt-order-type='buy'>Pay now !</button>
<button type='svt-btn' svt-amount='150' svt-currency='btc' svt-delivery-address='367pVvSShqKzBZBA4eqHLwHB41g9NAphTd' />
<button type='svt-btn' svt-amount='50' svt-currency='btc' svt-delivery-address='367pVvSShqKzBZBA4eqHLwHB41g9NAphTd' />
<button type='svt-btn' svt-currency='xtz' />
<button type='svt-btn' svt-payment-type='iov' svt-email='user@email.com' svt-email-editable='true' >Buy Starname<button/>
<button type='svt-btn' svt-email='user@email.com' svt-email-editable='true' svt-currency='iov' svt-amount='100'/>
```


##### Options
- `type`: `modal` or `embed` - `string` 
- `payButtons`: `true` or `false` - Enable click events on swap buttons - `bool`
- `payButtonsStyle`:  `true` or `false` - Enable auto styling of buttons - `bool`
- `embedContainerId`: `swap-embed` - Embed container id - `string`
- `iframeContainerClass`: `swap-widget-container` - iFrame container class - `string`
- `buttonId`: `swap-init` - Modal button id - `string`
- `config`: Widget configuration - `object`

##### Example
```javascript
const opts = {
        type: 'modal',
        buttonId: 'swap-init',
        config: {
            email: 'user@test.com',
            email_editable: true,
            currency: 'btc',
            amount: 200,
            amount_editable: false,
            delivery_address: '1F1tAaz5x1HUXrCNLbtMDqcw6o5GNn4xqX'
        }
}
```

## Advanced

### Callbacks
```javascript

    widget
    .on('ready', () => {
      // widget has loaded
    })
    .on('close', () => {
      // user has closed widget
    })
    .on('success', () => {
      // user has successfully paid
    })
    .on('failure', () => {
      // payment failure
    })
```

## About

Website: [https://swap.savitar.io](https://swap.savitar.io)
