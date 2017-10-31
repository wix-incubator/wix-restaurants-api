# Analytics
With the Wix Restaurants Analytics API you can query for stats about your online ordering activities.

## Restaurant Orders Stats
Querying for online ordering stats of a specific restaturant can be done using the following endpoint:

~~~
GET https://analytics.wixrestaurants.com/v1/restaurants/{restaurant_id}/orders/stats
~~~

with the following required query parameters:

|name     |type  |allowed values                              |
|---------|------|--------------------------------------------|
|metric   |String|price                                       |
|group_by |String|day, week, month, year, lifetime, hourOfWeek|
|time_zone|String|a valid timezone id                         |
|since    |Long  |any timestamp                               |
|until    |Long  |any timestamp                               |

and the following optional query parameters:

|name     |type  |description                                                                        |
|---------|------|-----------------------------------------------------------------------------------|
|sources  |String|an optional comma separated filter of relevant sources (who made the order)        |
|platforms|String|an optional comma separated filter of relevant platforms (where the order was made)|
|statuses |String|an optional comma separated filter of relevant order statuses                      |

Successful responses for non lifetime groups are returned as a JSON object representing an array of aggregated groups 
including the group id and the count and total of order prices for that group:

~~~ json
{"stats": [{"id": "someGroupId", "count": someCount, "total": someTotal}]}
~~~

The group id is derived according to the group_by query parameter as described in the following table:

|group_by                        |group id                                                         |
|--------------------------------|-----------------------------------------------------------------|
|day, week, month, year, lifetime|start time in yyyy-MM-dd format                                  |
|hourOfWeek                      |an index between 0 and 167 representing the relevant hour of week|


Successful responses for lifetime groups are returned as a JSON object representing an array of a single aggregated group 
including the count and total of order prices for that group:

~~~ json
{"stats": [{"count": someCount, "total": someTotal}]}
~~~

Unsuccessful responses are returned as a JSON object describing the relevant problem details according to RFC 7807.

## Chain Orders Stats
Querying for online ordering stats of a specific chain can be done using the following endpoint:

~~~
GET https://analytics.wixrestaurants.com/v1/chains/{chain_id}/orders/stats
~~~

with the same query parametres as in [Restaurant Orders Stats](Analytics#restaurant-orders-stats) above.

Successful and unsuccessful responses are also the same.

## Permissions
All of the endpoints must receieve a valid [access token](Authorization) with manager permissions for chain/restaurant.
The access token must be provided inside an 'Authorization' header according to the Bearer standard (see RFC 6750).

A valid Authorization header value example: ``` Bearer <access token with manager permissions for restaurant/chain> ```

## Example
The following cURL command:

~~~ bash
curl -X "GET" -H "Authorization: Bearer someAccessToken" "https://analytics.wixrestaurants.com/v1/restaurants/someRestaurantId/orders/stats?metric=price&group_by=day&time_zone=Asia%2FJerusalem&since=1485043200000&until=1485129600000l&statuses=accepted,new"
~~~

issues a request to retrieve the count of orders with ```accepted``` or ```new``` status that were made between 22/01/2017 (including) and 23/01/2017 (excluding) from  a restaurant with id ```someRestaurantId``` and the total sum of their prices grouped by day.
