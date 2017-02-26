# Wix Restaurants POS SPI
The Wix Restaurants POS SPI defines a standard way for point of sale systems to receive incoming orders from Wix in real-time. This is the best method to [integrate your point of sale with Wix Restaurants](Integrating-POS-(point-of-sale)-systems-to-Wix-Restaurants).

This SPI is currently available for select partners, email dannyl@wix.com for details.

## Protocol
Wix Restaurants pushes incoming orders in real-time via a simple WebHook.

WebHook endpoints must be valid HTTPS URLs that accept POST requests with `application/json` content-type.

When a new order is submitted, Wix Restaurants will POST the full order information, e.g.

~~~ json
{
  "menu": {
    "modified": 1478093212332,
    "items": [
      {
        "id": "7285589409963911",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Carpaccio"
        },
        "description": {
          "en_US": "Thinly sliced beef with extra virgin olive oil, lemon, arugola, and shaved parmigiano reggiano."
        },
        "price": 1000
      },
      {
        "id": "580639693308748",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Calamari Fritti"
        },
        "description": {
          "en_US": "Squid, lightly dusted in flour, deep fried, and served with fresh herbs, fried lemon, zucchini, and a spicy cucumber r?moulade."
        },
        "price": 1000,
        "picture": "https://lh3.googleusercontent.com/RIMA3qJ43WTOMGr7kD1SCeXaamPyLUyPHLu0id3E_DQo-3lQkE89dZlm7qu6QzkaGjSfzwrhcmvK97ozsUgjyw",
        "blobs": {
          "logo": {
            "id": "1696531050",
            "url": "https://lh3.googleusercontent.com/RIMA3qJ43WTOMGr7kD1SCeXaamPyLUyPHLu0id3E_DQo-3lQkE89dZlm7qu6QzkaGjSfzwrhcmvK97ozsUgjyw"
          }
        }
      },
      {
        "id": "1364562365249646",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Bresaola Rughetta e Parmigiano"
        },
        "description": {
          "en_US": "Thinly sliced air dried aged beef prepared carpaccio style with\nextra virgin olive oil, lemon, arugola, and shavings of parmigiano reggiano."
        },
        "price": 1000
      },
      {
        "id": "8254231576335078",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Insalata Tricolore"
        },
        "description": {
          "en_US": "Radicchio, belgian endive, and arugola with a balsamic vinaigrette."
        },
        "price": 800,
        "picture": "https://lh3.googleusercontent.com/UTHe6DdXaQ0o26d7oleO9YWhCmSNl15_LunPX6H6PqsO__NriWvWAm6Auo8ugEPTEpM-WHKWQHCJ0aC0qUxQtg",
        "blobs": {
          "logo": {
            "id": "2501963d-5ac3-4490-8677-b67b1d5fb0f4",
            "url": "https://lh3.googleusercontent.com/UTHe6DdXaQ0o26d7oleO9YWhCmSNl15_LunPX6H6PqsO__NriWvWAm6Auo8ugEPTEpM-WHKWQHCJ0aC0qUxQtg"
          }
        }
      },
      {
        "id": "4538038090707527",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Caprese"
        },
        "description": {
          "en_US": "Salad of fresh tomatoes and housemade fresh mozzarella dressed with extra virgin olive oil and fresh basil."
        },
        "price": 900,
        "picture": "https://lh3.googleusercontent.com/R4gbpwYBdIhANu3aPjzQdLx--kfffsfpUC8in1Z3w1ZP46x4y56AFJM_ffM4eMP4WMLQYGH6rIZ80mkioeNq2g",
        "blobs": {
          "logo": {
            "id": "1708571042",
            "url": "https://lh3.googleusercontent.com/R4gbpwYBdIhANu3aPjzQdLx--kfffsfpUC8in1Z3w1ZP46x4y56AFJM_ffM4eMP4WMLQYGH6rIZ80mkioeNq2g"
          }
        }
      },
      {
        "id": "4135591530877631",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Chopped Salad"
        },
        "description": {
          "en_US": "Our version with romaine, tomato, carrots, cucumber, radicchio, corn, cheddar cheese, palm hearts, and pancetta tossed in a three peppercorn parmigiano vinaigrette."
        },
        "price": 900,
        "picture": "https://lh3.googleusercontent.com/lpAmMt8CnGUzVqWMkBrmLUEqLrv4VaqzoGMoqvUd1XBIPVlcMr-N2fwwudvnMIHUmuNGIUcW5fMOBOvIFTkd",
        "blobs": {
          "logo": {
            "id": "1701251044",
            "url": "https://lh3.googleusercontent.com/lpAmMt8CnGUzVqWMkBrmLUEqLrv4VaqzoGMoqvUd1XBIPVlcMr-N2fwwudvnMIHUmuNGIUcW5fMOBOvIFTkd"
          }
        }
      },
      {
        "id": "3840387583130477",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Salmone"
        },
        "description": {
          "en_US": "Salmon."
        },
        "price": 2600,
        "picture": "https://lh3.googleusercontent.com/ppmCo58QaThDKFLPTzd2-CUTwpK10QtLq0M4FDvElYmvgr8tTcaWReCGGKiklnOuyQVi_zIcqGjR_t_Ri6upyQ",
        "blobs": {
          "logo": {
            "id": "1708401044",
            "url": "https://lh3.googleusercontent.com/ppmCo58QaThDKFLPTzd2-CUTwpK10QtLq0M4FDvElYmvgr8tTcaWReCGGKiklnOuyQVi_zIcqGjR_t_Ri6upyQ"
          }
        }
      },
      {
        "id": "2459507507152902",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Costata di Manzo"
        },
        "description": {
          "en_US": "Ribeye."
        },
        "price": 3100,
        "picture": "https://lh3.googleusercontent.com/7E7X8g2GR6Hja-hgn1VwVgCM2beBlld6uw2ofsInN_YoxigPedie-yhnjyMZPy5s6dNTxW3W8ibOd6-Q5xTWhw",
        "blobs": {
          "logo": {
            "id": "1697341043",
            "url": "https://lh3.googleusercontent.com/7E7X8g2GR6Hja-hgn1VwVgCM2beBlld6uw2ofsInN_YoxigPedie-yhnjyMZPy5s6dNTxW3W8ibOd6-Q5xTWhw"
          }
        }
      },
      {
        "id": "1712127355705869",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Coke"
        },
        "variations": [
          {
            "title": {
              "en_US": "We offer the following sizes:"
            },
            "itemIds": [
              "6011645467251806",
              "8131262756128535"
            ],
            "minNumAllowed": 1,
            "maxNumAllowed": 1,
            "prices": {
              "6011645467251806": 199,
              "8131262756128535": 299
            }
          }
        ]
      },
      {
        "id": "6011645467251806",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Small (12 fl oz)"
        },
        "price": 199
      },
      {
        "id": "8131262756128535",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Large (20 fl oz)"
        },
        "price": 299
      },
      {
        "id": "6654098186120851",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Name Your Third Dish e.g., Hamburger"
        },
        "description": {
          "en_US": "Sometimes the same dish comes in different sizes."
        },
        "variations": [
          {
            "title": {
              "en_US": "Select Size"
            },
            "itemIds": [
              "8384777276263641",
              "4020579968451736",
              "6709541687878791"
            ],
            "minNumAllowed": 1,
            "maxNumAllowed": 1,
            "prices": {
              "8384777276263641": 299,
              "4020579968451736": 499,
              "6709541687878791": 999
            }
          }
        ]
      },
      {
        "id": "8384777276263641",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Small"
        }
      },
      {
        "id": "4020579968451736",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Medium"
        }
      },
      {
        "id": "6709541687878791",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Large"
        }
      },
      {
        "id": "3313929511162872",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Name Your First Dish e.g., French Onion Soup"
        },
        "description": {
          "en_US": "This is a dish on your menu. Briefly describe it, e.g., Classic homemade soup, served with fresh baguette."
        },
        "price": 900
      },
      {
        "id": "7298776909705189",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Name Your Second Dish e.g., Nachos"
        },
        "description": {
          "en_US": "This is a dish on your menu. Briefly describe it, e.g., Nachos, cheese, olives, jalapeno pepper, served with sour cream."
        },
        "price": 1150
      },
      {
        "id": "29258699-de0c-43a4-8c4c-1fdc53bdff02",
        "restaurantId": "8830975305376234",
        "title": {
          "en_US": "Orange juice"
        },
        "price": 190,
        "picture": "https://media.wixapps.net/ggl-106739423631341017825/images/12364ef1372943fa8b543c06e001bde6~mv2/",
        "blobs": {
          "logo": {
            "id": "fc9d9bbc-eee5-476a-8896-b1dc978e96e4",
            "url": "https://media.wixapps.net/ggl-106739423631341017825/images/12364ef1372943fa8b543c06e001bde6~mv2/"
          }
        }
      }
    ],
    "sections": [
      {
        "id": "1",
        "title": {
          "en_US": "Lunch menu"
        },
        "description": {
          "en_US": "Available daily, 12pm-3pm"
        },
        "children": [
          {
            "id": "8",
            "title": {
              "en_US": "Appetizers"
            },
            "description": {
              "en_US": "Get busy with these dishes."
            },
            "itemIds": [
              "7285589409963911",
              "580639693308748",
              "1364562365249646"
            ]
          },
          {
            "id": "16.1432199531864",
            "title": {
              "en_US": "Insalate"
            },
            "itemIds": [
              "8254231576335078",
              "4538038090707527",
              "4135591530877631"
            ]
          },
          {
            "id": "35.1432199717577",
            "title": {
              "en_US": "Simply Grilled"
            },
            "description": {
              "en_US": "(served with fresh vegetables and starch)"
            },
            "itemIds": [
              "3840387583130477",
              "2459507507152902"
            ]
          },
          {
            "id": "48.1432199818848",
            "title": {
              "en_US": "Beverages"
            },
            "itemIds": [
              "1712127355705869",
              "29258699-de0c-43a4-8c4c-1fdc53bdff02"
            ]
          }
        ],
        "properties": {
          "com.wix.restaurants": "{\"systems\":[\"OLO\"]}"
        }
      }
    ],
    "chargesV2": [
      {
        "type": "tax",
        "id": "7e051b7f-4d6a-41f4-aa97-4706fd30dce6",
        "organizationId": "8830975305376234",
        "title": {
          "en_US": "% tax"
        },
        "displayCondition": {
          "type": "true"
        },
        "condition": {
          "type": "and",
          "conditions": [
            {
              "type": "true"
            },
            {
              "type": "or",
              "conditions": [
                {
                  "type": "order_delivery_type",
                  "deliveryType": "delivery"
                },
                {
                  "type": "order_delivery_type",
                  "deliveryType": "takeout"
                }
              ]
            }
          ]
        },
        "operator": {
          "type": "multiply",
          "numerators": [
            {
              "type": "sum_prices",
              "items": {
                "ids": [
                  "2459507507152902",
                  "4538038090707527",
                  "6654098186120851",
                  "3840387583130477",
                  "4020579968451736",
                  "6011645467251806",
                  "7298776909705189",
                  "1712127355705869",
                  "6709541687878791",
                  "8131262756128535",
                  "4135591530877631",
                  "8384777276263641",
                  "3313929511162872",
                  "7285589409963911",
                  "29258699-de0c-43a4-8c4c-1fdc53bdff02",
                  "1364562365249646",
                  "580639693308748",
                  "8254231576335078"
                ]
              }
            },
            {
              "type": "value",
              "value": 0
            }
          ],
          "denominators": [
            {
              "type": "value",
              "value": 100000
            }
          ]
        },
        "mandatory": true,
        "properties": {
          "com.openrest": "{\"menuFilter\":{\"type\":\"dishes\",\"ids\":[\"2459507507152902\",\"4538038090707527\",\"6654098186120851\",\"3840387583130477\",\"4020579968451736\",\"6011645467251806\",\"7298776909705189\",\"1712127355705869\",\"6709541687878791\",\"8131262756128535\",\"4135591530877631\",\"8384777276263641\",\"3313929511162872\",\"7285589409963911\",\"29258699-de0c-43a4-8c4c-1fdc53bdff02\",\"1364562365249646\",\"580639693308748\",\"8254231576335078\"]}}"
        }
      }
    ]
  },
  "order": {
    "id": "50243837983",
    "restaurantId": "8830975305376234",
    "locale": "en_US",
    "orderItems": [
      {
        "itemId": "1712127355705869",
        "variations": [
          {
            "title": {
              "en_US": "We offer the following sizes:"
            },
            "itemIds": [
              "6011645467251806",
              "8131262756128535"
            ],
            "minNumAllowed": 1,
            "maxNumAllowed": 1,
            "prices": {
              "6011645467251806": 199,
              "8131262756128535": 299
            }
          }
        ],
        "variationsChoices": [
          [
            {
              "itemId": "6011645467251806",
              "price": 199
            }
          ]
        ]
      }
    ],
    "price": 199,
    "currency": "USD",
    "delivery": {
      "type": "takeout",
      "time": 1477490401287
    },
    "contact": {
      "firstName": "Test",
      "lastName": "Test",
      "email": "customer@example.org",
      "phone": "+14156399034"
    },
    "payments": [
      {
        "type": "cash",
        "amount": 199
      }
    ],
    "orderCharges": [
      {
        "chargeId": "7e051b7f-4d6a-41f4-aa97-4706fd30dce6"
      }
    ],
    "created": 1477489501088,
    "modified": 1477490280330,
    "status": "new",
    "source": "",
    "platform": "web"
  }
}
~~~

where ```menu``` is a [Menu object](Data-structures#menu), and ```order``` is an [Order object](Data-structures#order).

Upon successfully receiving the order, the WebHook must answer with the following within 10 seconds of receiving the notification, or the order will be rejected and the customer will be shown an error message:

~~~ json
{"value":{"orderId":"XXX"}}
~~~

where ```XXX``` is the point of sale's internal order identifier.

## Errors
If the WebHook cannot receive the order for any reason, it should answer with the following:

~~~ json
{"error":{"code":"XXX", "description":"YYY"}}
~~~

where ```XXX``` is one of the error codes below, and ```YYY``` is a human-readable error message.

| Error Code                | Error                                   |
| ------------------------- | --------------------------------------- |
| ```endpoint_down```       | The point-of-sale is down               |
| ```invalid_item_mapping```| The order refers to an unknown item     |
| ```cc_rejected```         | A card payment was rejected (see below) |
| ```pos_error```           | Internal error                          |

## Card payments
If the point of sale is PCI-DSS level 1 complaint, merchants may prefer to have card payments processed by the POS instead of by an external payment gateway.

In this case, Wix Restaurants will also post full card information, e.g.-

~~~ json
{"menu":{}, "order":{}, "cards":{"card_token_1":{}, "card_token_2":{}}}
~~~

where ```cards``` maps card tokens to full card information.
