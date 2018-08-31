#  Get available shipping methods

Allows third-party systems to get a list of applicable shipping methods based on
the passed send address, recipient address and parcel(s)’ dimensions.

URL: http://api.parcelport.co.nz/api/shippingoptions?client_id=110

*This API can only be called after the API authentication is approved (the correct
auth string has been passed).

## Required Parameters:
* DeliveryAddress_company_name [Optional, recipient's company name]
* DeliveryAddress_contact_name [Require, recipient's contact name]
* DeliveryAddress_phone [Require, recipient's phone]
* DeliveryAddress_building [Optional, recipient's building]
* DeliveryAddress_address_body [Require, recipient's address– street and numbers]
* DeliveryAddress_suburb [Require, recipient's suburb]
* DeliveryAddress_city [Require, recipient's city]
* DeliveryAddress_postcode [Require, recipient's postcode]
* DeliveryAddress_country_code [Require, recipient's country, e.g., "NZ" for NewZealand]
* DeliveryAddress_instruction [Require if "authority_to_leave" is set]
* DeliveryAddress_email [Optional, recipient's email]

* PickupAddress_company_name [Optional, recipient's company name]
* PickupAddress_contact_name [Require, recipient's contact name]
* PickupAddress_phone [Require, recipient's phone]
* PickupAddress_building [Optional, recipient's building]
* PickupAddress_address_body [Require, recipient's address– street and numbers]
* PickupAddress_suburb [Require, recipient's suburb]
* PickupAddress_city [Require, recipient's city]
* PickupAddress_postcode [Require, recipient's postcode]
* PickupAddress_country_code [Require, recipient's country, e.g., "NZ" for NewZealand]
* PickupAddress_instruction [Require if "authority_to_leave" is set]
* PickupAddress_email [Optional, recipient's email]

* parcel [Require, parcel list, JSON encoded string only]
* authority_to_leave [Optional, numeric only, 0 or 1]

*The parcel detail include “volume”, “weight”, “cust_ref” customer reference.
To create a JSON encoded parcel string, the following json string can be taken as a
reference: 
[{"cust_ref":"ref1","volume":0.01,"weight":0.05},{"cust_ref":"ref2","volume"
:0.004,"weight":1}]

Expected responses:
A JSON encoded string contains all the valid shipping methods with shipping method ids.

Supported HTTP methods: POST
{
  "authority_to_leave": 0,
  "carrier_id": null,
  "carrier_method_id": null,
  "carrier_method_code": "parcels",
  "parcels": [
    {
      "length": 1,
      "height": 1,
      "width": 1,
      "volume": 0.001,
      "weight": 1,
      "kind": 0,
      "insurance_required": false,
      "currency": "NZD",
      "content_number": 31,
      "document_flag": 0
    }
  ],
  "DeliveryAddress": {
    "address_body": "17 Witbrock Cresent",
    "address_city": "Christchurch",
    "company_name": "Test",
    "contact_name": "Test Tony",
    "address_country": "NZ",
    "email": "187@parcelport.co.nz",
    "instruction": "TEST",
    "phone": 1234343,
    "address_postcode": 8053,
    "address_number": "17",
    "address_street": "Witbrock Crescent",
    "address_suburb": "Burnside"
  },
  "PickupAddress": {
    "address_body": "512 Queen Street",
    "address_id": 26422,
    "address_city": "Auckland",
    "company_name": "Test",
    "contact_name": "Test Jimmy",
    "address_country": "NZ",
    "email": "187@parcelport.co.nz",
    "instruction": "TEST",
    "phone": 1234343,
    "address_postcode": 1010,
    "address_number": "4512",
    "address_street": "Queen Street",
    "address_suburb": "Auckland"
  },
  "is_saturday": 0,
  "channel": 0
}


***

