#  Get available shipping methods

Allows third-party systems to get a list of applicable shipping methods based on
the passed sender's address, recipient's address and parcel(s)’ dimensions.

URL: https://api.parcelport.co.nz/api/1.0/shippingoptions?client_id=786

*This API can only be called after the API authentication is approved (the correct
auth string has been passed).

## Required Parameters:
*Parcels*
- **length** - [Require Length of the parcel cm]
- **width** - [Require Width of the parcel cm]
- **height** - [Require Length of the parcel cm]
- **weight** - [Require Weight of the parcel Kg]
- **volume** - [Optional Volume of the parcel]
- **kind** - [Optional default is 0, 1 if using satchel]
- **group_id** - [Optional add the satchel code if using satchel]
- **cust_ref** - [Optional reference of the item]
- **insurance_required** - [Require if International, true / false]
- **insured_value_amount** - [Require if International, insured value]
- **currency** - [Optional, Default NZD, insured value currency]
- **parcel_contents** [Require if International]
  - **description** - [Require if International, description of your products]
  - **quantity** - [Require if International, quantity of your products]
  - **weight** - [Require if International, weight of your products]
  - **value** - [Require if International, value of your products]

*PickupAddress*
- **address_body** [Require, unit number + street number + street name]
- **address_city** [Require, city]
- **address_country** [Require, country code, e.g., "NZ" for NewZealand]
- **address_postcode** [Require, postcode]
- **address_number** [Require, street number]
- **address_street** [Require, street name]
- **address_suburb** [Require, suburb]

*DeliveryAddress*
- **address_body** [Require, unit number + street number + street name]
- **address_city** [Require, city]
- **address_country** [Require, country code, e.g., "NZ" for NewZealand]
- **address_postcode** [Require, postcode]
- **address_number** [Require, street number]
- **address_street** [Require, street name]
- **address_suburb** [Require, suburb]

*Parcelport satchel list*
<table>
  <tr>
    <td>Satchel name</td>
    <td>code</td>
  </tr>
  <tr>
    <td>Satchel 140x230 DLE Letter Size</td>
    <td>dle</td>
  </tr>
  <tr>
    <td>Satchel 150x210 Small A5 Size</td>
    <td>a5</td>
  </tr>
  <tr>
    <td>Satchel Small A5 Bubble</td>
    <td>a5b</td>
  </tr>
  <tr>
    <td>Satchel 210x297 A4 Size</td>
    <td>a4</td>
  </tr>
  <tr>
    <td>Satchel A4 Bubble</td>
    <td>a4b</td>
  </tr>
  <tr>
    <td>Satchel 280x350 Medium Size</td>
    <td>med</td>
  </tr>
  <tr>
    <td>Satchel Medium Bubble</td>
    <td>medb</td>
  </tr>
  <tr>
    <td>Satchel 297x420 Large A3 Size</td>
    <td>a3</td>
  </tr>
  <tr>
    <td>Satchel 450x450 Extra Large A2 Size</td>
    <td>xl</td>
  </tr>
</table>

## Example
Request
POST https://api.parcelport.co.nz/api/1.0/shippingoptions?client_id=110

**Headers**
Content-Type: application/json;

**Authorization**
Bearer:bSEX9PltRH8uoHLmFdnt115OqEPPQTrrHpht6Bwq0yos9EW7o6vcBtrV23AF2TcuA8FJTabH_t9x2hDo_tP840QIXfUmg0AGmRBfRHfeTeCjBGrK4ezMuLQ0jsyoDAb3cxUhkMniuJHYfSWhKlvyuQZPDqAffr4ggCY9qiojTgRm1s-EubJZK941SrtXBmTQKnkAWcru5MmXQvm0ziNAfZ_JhCKGoNHhpmnJVfQvGYMQNjMRknoE6GZl63GFZZ9tjMz2ICBPqEJsX67fWOoB2adbr58hA72omCMgLaX-1-DhYjlEnb_qhGljklPL3Qo6ohgykA

**Body**
``` json
{
  "parcels": [
    {
      "length": 1,
      "height": 1,
      "width": 1,
      "weight": 1,
    }
  ],
  "DeliveryAddress": {
    "address_body": "17 Witbrock Crescent",
    "address_city": "Christchurch",
    "address_country": "NZ",
    "address_postcode": 8053,
    "address_number": "17",
    "address_street": "Witbrock Crescent",
    "address_suburb": "Burnside"
  },
  "PickupAddress": {
    "address_body": "12 Pitt Street",
    "address_city": "Auckland",
    "address_country": "NZ",
    "address_postcode": 1010,
    "address_number": "12",
    "address_street": "Pitt Street",
    "address_suburb": "Auckland Central"
  },
}
```
**Responses**
A JSON encoded string contains all the valid shipping methods with shipping method ids.
The quoteRequestID need to be added in the request when you create a consignment, and it will be expired.

``` json
{
    "errorMessage": null,
    "quoteRequestID": "9552255a-05b7-4c7e-81ea-4eff2f0caae1",
    "expiryDate": "2019-02-15T14:46:31.6321973+13:00",
    "errors": {},
    "quotes": [
        {
            "quoteType": {
                "code": "D",
                "description": "Direct - Non Stop"
            },
            "quoteDetails": [
                {
                    "type": {
                        "code": "None",
                        "kind": "0",
                        "description": "None",
                        "sequence": null
                    },
                    "quote": {
                        "carrier_id": "ph",
                        "carrier_method_code": "TD",
                        "carrier_method_id": "phtd",
                        "carrier_method_name": "Own Packaging InterIsland 2 Days",
                        "carrier_method_notesHtml": "<ul>\r\n<li>Two-day delivery between Islands</li>\r\n<li>Delivery Standard -&nbsp;Economy 2 day option between islands</li>\r\n<li>FREE Insurance covers up to $2000</li>\r\n</ul>",
                        "carrier_method_desc": "Two Day Inter Island",
                        "carrier_name": "Post Haste",
                        "is_signature": null,
                        "min_delivery_target": null,
                        "max_delivery_target": null,
                        "price_satchel": 0,
                        "packageDetails": {
                            "kind": null,
                            "price_net": 5.67,
                            "price_rural": 0,
                            "price_sat": 0,
                            "price_sig": 0,
                            "addOnPrice_Sig": 0,
                            "addOns": [
                                {
                                    "type": 0,
                                    "code": "phtd",
                                    "name": "Own Packaging InterIsland 2 Days",
                                    "description": "<ul>\r\n<li>Two-day delivery between Islands</li>\r\n<li>Delivery Standard -&nbsp;Economy 2 day option between islands</li>\r\n<li>FREE Insurance covers up to $2000</li>\r\n</ul>",
                                    "price": 5.67,
                                    "gstPrice": 0.85
                                },
                                {
                                    "type": 5,
                                    "code": "phfaf",
                                    "name": "Fuel Adjustment Factor",
                                    "description": "<p>The Fuel Adjustment Factor (FAF) is a charge to Domestic and International Courier Services to off-set the current fuel volatility.&nbsp;</p>",
                                    "price": 0,
                                    "gstPrice": 0
                                },
                                {
                                    "type": 5,
                                    "code": "phruc",
                                    "name": "Road User Charge RUC",
                                    "description": "<p>Governmet Road User Charge</p>\r\n<p>Since 2007 the government have implemented increases in road user charges every year except 2011.<br /><br /> On the 18th December 2012 the Transport Minister, Gerry Brownlee, announced that road user charges will be increased on the 1st July each year until 2016 to contribute to the cost of the Roads of National Significance programme. There are seven roads of national significance some of which have not started yet so it is reasonable to assume that the government may continue to fund these projects via road user increases past July 2016. <br /><br />This surcharge will be operating separately from our existing fuel surcharge and be applied to the base price independently.</p>",
                                    "price": 0.25,
                                    "gstPrice": 0.04
                                }
                            ],
                            "total_price": 5.92,
                            "total_tax": 0.89,
                            "price": 5.67
                        },
                        "items": [
                            {
                                "pc": 1,
                                "volume": 0,
                                "weight": 1,
                                "kind": null,
                                "group_id": null,
                                "cust_ref": null,
                                "pack_name": null
                            }
                        ],
                        "insurance": 2000,
                        "tracking_included": "1",
                        "signature_included": "1",
                        "interchangeBrachCode": null,
                        "interchangeType": 0,
                        "interchangeAddress": null
                    }
                }
            ]
        },
    ]
}
```

***

