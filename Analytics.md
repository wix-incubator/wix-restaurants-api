# Analytics
With the Wix Restaurants Analytics API you can query for stats about your online ordering activities.

## Restaurant Orders Stats
Querying for online ordering stats of a specific restaturant can be done using the following endpoint:

~~~
GET https://analytics.wixrestaurants.com/v1/restaurants/{restaurant_id}/orders/stats
~~~

with the follwoing required query parameters:
~~~
* metric (String): "price"
* period (String): "day"/"week"/"month"/"year"/"lifetime"
* time_zone (String): a valid timezone id
* since (Long): timestamp 
* until (Long): timestamp
~~~

and the following optional query parameters:
~~~
* sources (String): an optional comma separated filter of relevant sources (who made the order)
* platforms (String): an optional comma separated filter of relevant platforms (where the order was made)
* statuses (String): an optional comma separated filter of relevant order statuses
~~~

Successful responses for non lifetime periods are returned as a JSON object representing an array of aggregated periods 
including the start time of the period and the count and total of order prices for that period:

~~~ json
{"stats": [{"startTime": "yyyy-MM-dd", "count": "someCount", "total": "someTotal"}]}
~~~

Successful responses for lifetime periods are returned as a JSON object representing an array of a single aggregated period 
including the count and total of order prices for that period:

~~~ json
{"stats": [{"count": "someCount", "total": "someTotal"}]}
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
