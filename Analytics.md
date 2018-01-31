# Analytics
With the Wix Restaurants Analytics API you can query for stats about your online ordering activities.

## Restaurant Orders Stats
Querying for online ordering stats of a specific restaturant can be done using the following endpoint:

~~~
GET https://analytics.wixrestaurants.com/v1/restaurants/{restaurant_id}/orders/stats
~~~

with the following query parameters:

|name       |type  |required|value                                                                                    |
|-----------|------|--------|-----------------------------------------------------------------------------------------|
|`metric`   |String|yes     |`price`                                                                                  |
|`group_by` |String|yes     |`day`, `week`, `month`, `year`, `lifetime`, `hourOfWeek`, `monthOfYear`                  |
|`time_zone`|String|yes     |a valid [timezone id](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones), e.g. `America/New_York`                                                                                                    |
|`since`    |Long  |yes     |timestamp, inclusive (number of milliseconds since January 1, 1970, 00:00:00 UTC)        |
|`until`    |Long  |yes     |timestamp, exclusive (see `since`)                                                       |
|`sources`  |String|no      |comma separated list of order sources                                                    |
|`platforms`|String|no      |comma separated list of order [platforms](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/wix/restaurants/Platforms.java)       |
|`statuses` |String|no      |comma separated list of order [statuses](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/wix/restaurants/orders/Statuses.java) |

Successful responses are returned as a JSON object representing an array of aggregated groups 
including the group id and the count and total of order prices for that group:

~~~ json
{"stats": [{"id": "someGroupId", "count": someCount, "total": someTotal}]}
~~~

The group id is derived according to the group_by query parameter as described in the following table:

|group_by              |group id                                                         |
|----------------------|-----------------------------------------------------------------|
|day, week, month, year|start time in yyyy-MM-dd format                                  |
|hourOfWeek            |an index between 0 and 167 representing the relevant hour of week|
|monthOfYear           |an index between 1 and 12 representing the relevant month of year|
|lifetime              |N/A                                                              |

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
curl -X "GET" -H "Authorization: Bearer someAccessToken" "https://analytics.wixrestaurants.com/v1/restaurants/someRestaurantId/orders/stats?metric=price&group_by=day&time_zone=Asia%2FJerusalem&since=1485043200000&until=1485129600000&statuses=accepted,new"
~~~

issues a request to retrieve the count of orders with ```accepted``` or ```new``` status that were made between 22/01/2017 (including) and 23/01/2017 (excluding) from  a restaurant with id ```someRestaurantId``` and the total sum of their prices grouped by day.
