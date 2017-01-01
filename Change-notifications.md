# Change notifications via WebHooks 
The Wix Restaurants platform supports change notifications via a set of WebHooks.

WebHooks endpoints must be valid HTTPS URLs that accept POST requests with `application/json` content-type.

By design, notifications only indicate where the change was. To find out what changed, receivers must make a separate request to the Wix Restaurants API and retrieve the latest relevant data. This avoids many data inconsistency issues that may result from temporary communication errors, and allows request throttling on both ends.

WebHooks must answer with the following within 10 seconds of receiving the notification, or the notification will be retried a few times:

~~~ json
{"value":{}}
~~~

WebHooks are currently in closed beta. For inquiries, email dannyl@wix.com

## Restaurant change notifications
Upon any change in the restaurant's business info or menu, Wix Restaurants will POST the restaurant's ID, e.g.

~~~ json
{"organizationId":"8830975305376234"}
~~~

## Order change notifications
Upon any change in an order's status, Wix Restaurants will POST the order's ID, e.g.

~~~ json
{"orderId":"1234"}
~~~
