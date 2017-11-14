# Rendering

The Wix Restaurants Rendering API renders domain objects to HTML.

> ⚠ This API is currently in alpha, and may change without notice.

## Orders
To render orders, use the following [JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC) endpoint:

~~~
POST https://renderer.wixrestaurants.com/render
~~~

Use the `application/json` content-type, and the following body:

~~~ json
{"jsonrpc": "2.0", "method": "renderNewOrder", "params": {...}, "id": 1}
~~~

where `params` is an object with the following fields:

|name         |type       |required|value                                                                                    |
|-------------|-----------|--------|-----------------------------------------------------------------------------------------|
|`locale`     |String     |yes     |The rendered locale, e.g. `en_US`                                                        |
|`style`      |String     |yes     |`email`, `fax`, `receipt`, `sms`, `embedded`, `voice`                                    |
|`distributor`|[Distributor](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Distributor.java)|yes     |The restaurant's distributor. |
|`restaurant` |[Restaurant](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Restaurant.java)|yes     |The order's restaurant. |
|`menu`       |[Menu](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Menu.java)|yes     |The restaurant's menu. |
|`order`      |[Order](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Order.java)|yes     |The order to render. |
|`viewMode`   |String     |yes      |`restaurant`, `customer`                                                                |
|`cardStyle`  |String     |yes      |`minimal`                                                                               |
|`unbranded`  |Boolean    |yes      |false                                                                                   |
|`unbranded`  |Boolean    |yes      |false                                                                                   |
