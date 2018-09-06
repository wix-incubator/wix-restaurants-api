# Search
With the Wix Restaurants Search API you can query for restaurants that are located nearby or delivering to a given location.

## Restaurants Delivering
Querying for restaurants that are delivering to a given location can be done using the following endpoint:

~~~
GET https://search.wixrestaurants.com/v1/restaurants/delivering
~~~

with the following query parameters:

|name       |type  |required|value                             |
|-----------|------|--------|----------------------------------|
|`lat`      |Double|yes     |a valid latitiude                 |                                                                 |
|`lng`      |Double|yes     |a valid longitude                 |

Successful responses are returned as a JSON object representing an array of restaurant ids:

~~~ json
{"restaurantIds": ["someRestaurantId", "anotherRestaurantId"]}
~~~

Unsuccessful responses are returned as a JSON object describing the relevant problem details according to RFC 7807.

## Chain Branches Delivering
Querying for chain branches that are delivering to a given location can be done using the following endpoint:

~~~
GET https://search.wixrestaurants.com/v1/chains/{chain_id}/branches/delivering
~~~

with the same query parametres as in [Restaurants Delivering](Search#restaurants-delivering) above.

Successful and unsuccessful responses are also the same.

## Restaurants Near
Querying for restaurants that are located within a given radius from a given location can be done using the following endpoint:

~~~
GET https://search.wixrestaurants.com/v1/restaurants/near
~~~

with the following query parameters:

|name       |type  |required|value                             |
|-----------|------|--------|----------------------------------|
|`lat`      |Double|yes     |a valid latitiude                 |                                                                 |
|`lng`      |Double|yes     |a valid longitude                 |
|`radius`   |Double|yes     |a radius in meters                |

Successful responses are returned as a JSON object representing an array of restaurant ids:

~~~ json
{"restaurantIds": ["someRestaurantId", "anotherRestaurantId"]}
~~~

Unsuccessful responses are returned as a JSON object describing the relevant problem details according to RFC 7807.

## Chain Branches Near
Querying for chain branches that are located within a given radius from a given location can be done using the following endpoint:

~~~
GET https://search.wixrestaurants.com/v1/chains/{chain_id}/branches/near
~~~

with the same query parametres as in [Restaurants Near](Search#restaurants-near) above.

Successful and unsuccessful responses are also the same.

## Permissions
Anyone can use the search API. No special permissions are required.

## Examples
The following cURL command:

~~~ bash
curl -X "GET" "https://search.wixrestaurants.com/v1/restaurants/delivering?lat=40.748817&lng=-73.985428"
~~~

issues a request to retrieve all restaurants that are delivering to the empire state building.

The following cURL command:

~~~ bash
curl -X "GET" "https://search.wixrestaurants.com/v1/restaurants/near?lat=40.748817&lng=-73.985428&radius=1609.34"
~~~

issues a request to retrieve all restaurants that are located within 1609.34m (one mile) from the empire state building.
