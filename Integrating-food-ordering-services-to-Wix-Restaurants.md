Integrating 3rd-party food ordering services to Wix Restaurants requires dealing with three issues:

* Menu management and synchronization
* Order submission and status monitoring
* Payment processing

### Menu management and synchronization
Wix Restaurants products are self-managed by the restaurant staff, and so act as the "single source of truth" for the restaurant's business info and menu data.

3rd-party services are encouraged to pull this information, in real-time or periodically, and import it into their systems so it can be displayed to their customers.

Example: [printing a menu](https://github.com/wix/wix-restaurants-java-sdk/blob/master/wix-restaurants-java-examples/src/main/java/com/wix/restaurants/examples/MenuExample.java)

### Order submission and status monitoring
3rd-party services can submit new orders to any restaurant. Once received, 3rd-party orders go through the exact same flow as orders that originated from the restaurant's own systems: they are delivered to the restaurant via the restaurant's channel of choice, and trigger the restaurant's predefined "delayed order" notifications (if needed).

Example: [submitting a new order](https://github.com/wix/wix-restaurants-java-sdk/blob/master/wix-restaurants-java-examples/src/main/java/com/wix/restaurants/examples/SubmitOrderExample.java)

3rd-parties can register a webhook that gets called on any change in the order's status. If an order is not handled after a while, 3rd-parties can trigger their own "delayed order" notifications.

### Payment processing
The Wix Restaurants API supports the common use-case where customers pay the 3rd-party service for the order, as opposed to paying the restaurant directly. The 3rd-party service can later settle the bill with the restaurant offline, minus the service fees.

In this case, orders submitted to the restaurant should simply specify the payment method as "3rd-party credit".

Example: [submitting an order paid with 3rd-party credit](https://github.com/wix/wix-restaurants-java-sdk/blob/master/wix-restaurants-java-examples/src/main/java/com/wix/restaurants/examples/DeliveryclubPaymentExample.java)
