#  Get available shipping methods

Allows third-party systems to get a list of applicable shipping methods based on
the passed send address, recipient address and parcel(s)’ dimensions.
URL: http://freightdemo.payport.co.nz/customerapi/shipping?customer_id=xxxxx&request_id=xxxxxx&auth_string=xxxxxxx

*This API can only be called after the API authentication is approved (the correct
auth string has been passed).

## Required Parameters:
* recipient_company_name [Optional, recipient's company name]
* recipient_contact_name [Require, recipient's contact name]
* recipient_phone [Require, recipient's phone]
* recipient_building [Require, recipient's building]
* recipient_address_body [Require, recipient's address– street and numbers]
* recipient_suburb [Require, recipient's suburb]
* recipient_city [CompRequireulsory, recipient's city]
* recipient_postcode [Optional, recipient's postcode]
* recipient_country_code [Require, recipient's country, e.g., "NZ" for NewZealand]
* recipient_instruction [Require if "authority_to_leave" is set]
* recipient_email [Require, recipient's email]
* authority_to_leave [Optional, numeric only, 0 or 1]
* sender_address_body [Require, senders's address, e.g., "12 pitt st"]
* sender_city [Require, sender's city]
* sender_country_code [Require, sender's country]
* sender_address_id[Optional, sender's address id, numeric only]
* parcel [Require, parcel list, JSON encoded string only]

*The parcel detail include “volume”, “weight”, “cust_ref” customer reference.
To create a JSON encoded parcel string, the following json string can be taken as a
reference: 
[{"cust_ref":"ref1","volume":0.01,"weight":0.05},{"cust_ref":"ref2","volume"
:0.004,"weight":1}]

Expected responses:
A JSON encoded string contains all the valid shipping methods with shipping method ids.

Supported HTTP methods: POST

{
	"recipient_company_name":"Testcompany",
	"recipient_contact_name": "Test",
	"recipient_phone": "1234355",
	"recipient_building": "Testbuilding",
	"recipient_address_body": "38A Ngaiwi St",
	"recipient_suburb": "Orakei",
	"recipient_city": "Auckland",
	"recipient_postcode": "1071",
	"recipient_country_code": "NZ",
	"recipient_instruction": "Testinstruction",
	"recipient_email": "test@parcelport.co.nz",
	"authority_to_leave": "0",
	"sender_address_body": "12 Pitt St",
	"sender_city": "Auckland",
	"sender_country_code":"NZ",
	"parcels": [
		{"cust_ref": "ref1","volume":0.01,"weight":0.05},
		{ "cust_ref": "ref2","volume":0.004,"weight":1 }
	]
}

***

