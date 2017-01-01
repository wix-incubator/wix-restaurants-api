# Main data structures

## Restaurant
A [Restaurant](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Restaurant.java) object holds the information associated with a single venue (a single physical location):

* ID
* Title
* Address
* Opening times
* Delivery areas
* ... and more

See: [Finding your restaurant's id](Finding-your-restaurant's-id)

## Menu
A [Menu](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Menu.java) object holds the complete menu information for a Restaurant.

Menu information is hierarchical:

* The complete menu information is a list of menus, e.g. "Lunch Menu", "Dinner Menu", "Wines Menu"
* A menu consists of a list of menu sections, e.g. "Starters", "Mains", "Drinks"
* A menu section holds a list of items, e.g. "Hamburger", "Cheeseburger"
* An item may have a a list of variations, e.g. "Size", "Cooking level"
* A variation is a list of choices, e.g. "Small", "Medium", "Large"
* Choices are just items, so they can have variations of their own.

From a technical perspective, this whole thing is compacted to two fields in the Menu object:

1. ```items```: a list of [Item](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Item.java) objects.
2. ```sections```: a list of [MenuSection](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/MenuSection.java) objects. Top-level menu sections refer to menus, with their "children" field as the list of menu-sections.

Example: [printing a menu](https://github.com/wix/wix-restaurants-java-sdk/blob/master/wix-restaurants-java-examples/src/main/java/com/wix/restaurants/examples/MenuExample.java)

## Order
An [Order](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/Order.java) object holds the information associated with a pickup or delivery:

* ID
* restaurant ID
* customer contact information: name, phone, email
* dispatch information: pickup or delivery (address), guaranteed times
* ordered items
* status: new, accepted, canceled

Ordered items are represented as a list of [OrderItem](https://github.com/wix/openrest4j/blob/master/openrest4j-api/src/main/java/com/openrest/v1_1/OrderItem.java) objects, where each member refers to some menu item, and holds a (hierarchical) list of corresponding variation choices.

Example: [submitting a new order](https://github.com/wix/wix-restaurants-java-sdk/blob/master/wix-restaurants-java-examples/src/main/java/com/wix/restaurants/examples/SubmitOrderExample.java)

# Additional data structures

## LocalizedString
The Wix Restaurants API is localized by design, and any user-generated string can vary between locales: from the restaurant's title to item descriptions.

A localized string is simply a map from locales to values. For example, a restaurant's title may be represented as:

    {"en_US":"The Testaurant","fr_FR":"Le Testaurant","he_IL":"המבדקה"}

API users should display the value associated with their locale of choice, falling back to the value associated with the restaurant's default locale (as specified by `Restaurant.locale`) which is guaranteed to always exist.