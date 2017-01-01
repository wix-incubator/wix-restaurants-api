# Protocol
The Wix Restaurants API is a JSON-RPC variant with a single endpoint:

    https://api.wixrestaurants.com/v1.1

Requests are POSTed as JSON objects:

~~~
{"type":"some_request_type", ...}
~~~
{: .language-json}

Successful responses are returned as JSON objects:

    {"value": ...}

Likewise, error responses: 

    {"error":"some_error_code","errorMessage":"some error message"}

## Example
The following cURL command issues a [get_organization](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/GetOrganizationRequest.java) request to retrieve the test restaurant's info:

    curl -X "POST" -H "Content-Type: application/json" -d '{"type":"get_organization","organizationId":"8830975305376234"}' "https://api.wixrestaurants.com/v1.1"

A successful response returns a [Restaurant](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Restaurant.java) value:

    {"value":{"type":"restaurant","id":"8830975305376234","created":1431011837631,"modified":1459086417084,"title":{"en_US":"The Testaurant"},"description":{"en_US":"Wix Restaurants test restaurant."}, ...}
