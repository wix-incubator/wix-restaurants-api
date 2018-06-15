# Protocol
The Wix Restaurants API is a RESTful service with this base URL:

    https://api.wixrestaurants.com/v2

Requests and responses use JSON.

On error, the service returns an appropriate HTTP status code (4xx / 5xx) and error information in the body as in [RFC 7807](https://tools.ietf.org/html/rfc7807).

~~~ json
{"type":"https://www.wixrestaurants.com/errors/some_error", "detail":"some error detail"}
~~~

## Example
The following cURL command retrieves the test restaurant's info:

~~~ bash
curl "https://api.wixrestaurants.com/v2/organizations/8830975305376234"
~~~

A successful response returns a [Restaurant](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Restaurant.java) value:

~~~ json
{"type":"restaurant","id":"8830975305376234","created":1431011837631,"modified":1459086417084,"title":{"en_US":"The Testaurant"},"description":{"en_US":"Wix Restaurants test restaurant."}
~~~
