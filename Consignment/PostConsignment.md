# Make consignment / Get consignment tracking number

Allows third-party systems to make consignments and get consignment tracking
numbers based on the passed shipping method id, send address, recipient address
and parcel(s)’ dimensions. 

URL: http://freightdemo.payport.co.nz/customerapi/consignment?customer_id=xxxxx&request_id=xxxxxx&auth_string=xxxxxxx

*This API can only be called after the API authentication is approved (the correct
auth string has been passed). 

## Required Parameters:
* carrier_method_id [Require, e.g. "phms"]
* carrier_method_code [Require, e.g. "MS"]
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
* carrier_id [Optional]
* pickup_option [Optional, 1/0]
* allow_return [Optional, 1/0]
* email_to_recipient [Optional, 1/0]
* parcel [Require, parcel list, JSON encoded string only]

Expected responses:
A JSON encoded string contains the tracking number of the consignment and
tracking Link

Supported HTTP methods: POST

{
	"carrier_method_id": "phms",
	"carrier_method_code": "MS",
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
	"sender_address_body": "12 pitt st",
	"sender_city": "Auckland",
	"sender_country_code":"NZ",
	"carrier_id": "ph",
	"pickup_option": 1,
	"allow_return": 0,
	"email_to_recipient": 1,
	"parcels": [
		{"cust_ref": "ref1","volume":0.01,"weight":0.05},
		{ "cust_ref": "ref2","volume":0.004,"weight":1 }
	]
}