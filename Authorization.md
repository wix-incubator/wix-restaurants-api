# Authorization

## *** Deprecated API - Will be removed by August 1st 2022 ***

Our general philosophy is that any information that could be obtained through anonymous web-scraping or UI automation should not require authentication. This includes all API requests that retrieve public data (business info, menus) or submit orders.

Authentication is required for API requests that modify public data (change the business phone number, add a menu item, accept an order), or access non-public information (the list of open orders, payment gateway credentials). These requests have a mandatory ```accessToken``` field that's used to verify the user's permissions - the rest of this article deals with this.

## Retrieving access tokens
Access tokens are generated by the Wix Restaurants Authentication service, a RESTful service with this base URL:

~~~
https://auth.wixrestaurants.com/v2
~~~

Requests and responses use JSON.

On error, the service returns an appropriate HTTP status code (4xx / 5xx) and error information in the body as in [RFC 7807](https://tools.ietf.org/html/rfc7807).

~~~ json
{"type":"https://www.wixrestaurants.com/errors/some_error", "detail":"some error detail"}
~~~

While the service supports various modes of authentication, the recommended flow is to exchange a Wix [App Instance](https://dev.wix.com/docs/infrastructure/app-instance/) with an access token, and use the access token for all subsequent API requests.

## Retrieving a Wix App Instance
To retrieve a Wix app instance,

1. Access your site's Dashboard (see instructions [here](https://support.wix.com/en/article/accessing-your-dashboard-1928525)).
2. Open the browser's development console.
3. You should see a line that says `[Restaurants] init app with instance XXX`.
4. Note the `XXX` - this is your Wix App Instance.

## Example
The following cURL command generates an access token from a Wix App Instance (```XXX``` in the example):

~~~ bash
curl -X "POST" -H "Content-Type: application/json" -d '{"instance":"XXX"}' "https://auth.wixrestaurants.com/v2/com.wix/access_token"
~~~

A successful response returns a [LoginResponse](https://github.com/wix/wix-restaurants-authentication/blob/master/wix-restaurants-authentication-api/src/main/java/com/wix/restaurants/authentication/model/LoginResponse.java) value:

~~~ json
{"user":{"ns":"com.wix", "id":"some wix user id"},"accessToken":"AAA"}
~~~

```AAA``` can then be used to make privileged API calls on behalf of the user.
