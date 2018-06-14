# ParcelPort System API(v1.0)

Parcel Port API provides an access to enable your customer to send parcels using our system.

***

# Get api-key and api-salt
Allows third-party systems to get Payport customers’ API authorization info (customer_id, api_key and api_salt) from Payport System.

Request URL:
http://freightdemo.payport.co.nz/customerapi/auth/request_api_info

## Required Parameters:
* username [Require]
* password [Require]
* trust_key [Optional]

“username” refers to the Payport customer login account name.
“password” refers to the Payport login password.
“trust_key” refers to the trust keys given by Payport. Only the trustworthy
customers of Payport can get trust keys. With a valid trust key, Payport system can
automatically create api_key and api_salt for a customer who does not have any
API request information. 

Expected responses:

JSON encoded string contains
--------------------------------------- 
* customer_id
* api_key
* api_salt
---------------------------------------
Supported HTTP methods: POST or GET
Example call in Postman

http://freightdemo.payport.co.nz/customerapi/auth/request_api_info?username=eva&password=xxxxxx&trust_key=123123joiuioadsfs1231231111

Response:
{
 "$id": "1",
 "success": 1,
 "customer_id": 44,
 "api_key": "8c716e66396adbcf981bae49d250df94",
 "api_salt": "a70ffbabe6ae0645624bed2b16f35b13"
} 

***

# Authentication
Getting API authentication from Payport is the prerequisite to carrying out each
API request. The API authentication procedure includes two steps.
Step 1. Request authentication string:
Request with customer id, api key (request key) and api salt (pairing key). Payport
will response an “auth string” for Step 2.

Reqeuest URL:
http://freightdemo.payport.co.nz/customerapi/auth?customer_id=44&request_key=8c716e66396adbcf981bae49d250df94&timestamp=20170411122100

## Required Parameters:
* customer_id [Require, numeric only]
* request_key [Require, AKA “api_key”]
* timestamp [Require]

“customer_id” refers to the Payport customer id.
“request_key” refers to the api_key.
“timestamp” refers to the current system timestamp(Format: yyyyMMddHHmmss).
Payport only tolerate +/-600 seconds.
Expected responses:
JSON encoded string contains:
* “request_id”
* “auth_string”
Supported HTTP methods: POST or GET

***

# Shipping
- **[<code>POST</code> /customerapi/shipping](Shipping/GetShippingMethod.md)** returns a list of available shipping methods


# Make a consignment
- **[<code>POST</code> /customerapi/consignment](Consignment/PostConsignment.md)** Post a consignment