# Make consignment / Get consignment tracking number

Allows third-party systems to make consignments and get consignment tracking
numbers based on the passed shipping method id, send address, recipient address
and parcel(s)’ dimensions. 

URL: https://api.parcelport.co.nz/api/1.0/consignment?client_id=110

*This API can only be called after the API authentication is approved (the correct
auth string has been passed). 

## Required Parameters:
* carrier_method_id [Require, e.g. "phms"]
* carrier_method_code [Require, e.g. "MS"]

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

* carrier_id [Optional]
* carrier_method_id [Require, e.g., "CPOLP" For Courier post]
* carrier_method_code [Require, e.g., "CPOLP" For Courier post]
* consignment_name [Require, DateTime + clientID, e.g., "20180830154322-187"]
* pickup_option [Require, numeric only, 0 or 1]
* is_saturday [Require, numeric only, 0 or 1]
* email_to_recipient [Require, numeric only, 0 or 1]
* is_signature [Require, numeric only, 0 or 1]
* QuoteRequestID [Require, For Get quotes response]
* authority_to_leave [Optional, numeric only, 0 or 1]

* parcel [Require, parcel list, JSON encoded string only]

Expected responses:
A JSON encoded string contains the tracking number of the consignment and
tracking Link

Supported HTTP methods: POST

{
  "authority_to_leave": 0,
  "carrier_id": "NCP",
  "carrier_method_id": "CPOLP",
  "carrier_method_code": "CPOLP",
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
  "channel": 0,
  "document_flag": 0,
  "consignment_name": "20180830154322-187",
  "pickup_option": 1,
  "allow_return": 0,
  "email_to_recipient": 1,
  "is_signature": 1,
  "undeliverable_instructions": 1,
  "QuoteRequestID": "09aa49c3-2fbc-45f7-808a-3e77f0e790eb"
}