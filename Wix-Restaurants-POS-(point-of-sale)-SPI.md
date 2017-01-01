# Wix Restaurants POS SPI
The Wix Restaurants POS SPI defines a standard way for point of sale systems to receive incoming orders from Wix in real-time. This is the best method to [integrate your point of sale with Wix Restaurants](Integrating-POS-(point-of-sale)-systems-to-Wix-Restaurants).

This SPI is currently available for select partners, email dannyl@wix.com for details.

## Protocol
Wix Restaurants pushes incoming orders in real-time via a simple WebHook.

WebHook endpoints must be valid HTTPS URLs that accept POST requests with `application/json` content-type.

When a new order is submitted, Wix Restaurants will POST the full order information, e.g.

    {"menu":{...}, "order":{...}}

where ```menu``` is a [Menu object](Data-structures#menu), and ```order``` is an [Order object](Data-structures#order).

Upon successfully receiving the order, the WebHook must answer with the following within 10 seconds of receiving the notification, or the order will be rejected and the customer will be shown an error message:

    {"value":{"orderId":"XXX"}}

where ```XXX``` is the point of sale's internal order identifier.

## Errors
If the WebHook cannot receive the order for any reason, it should answer with the following:

    {"error":{"code":"XXX", "description":"YYY"}}

where ```XXX``` is one of the error codes below, and ```YYY``` is a human-readable error message.

| Error Code                | Error                                   |
| ------------------------- | --------------------------------------- |
| ```endpoint_down```       | The point-of-sale is down               |
| ```invalid_item_mapping```| The order refers to an unknown item     |
| ```cc_rejected```         | A card payment was rejected (see below) |
| ```pos_error```           | Internal error                          |

## Card payments
If the point of sale is PCI-DSS level 1 complaint, merchants may prefer to have card payments processed by the POS instead of by an external payment gateway.

In this case, Wix Restaurants will also post full card information, e.g.-

    {"menu":{...}, "order":{...}, "cards":{"card_token_1":{...}, "card_token_2":{...}, ...}

where ```cards``` maps card tokens to full card information.
