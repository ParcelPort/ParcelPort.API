# ParcelPort System API(v1.0)

Parcel Port API provides an access to enable your customer to send parcels using our system.

***

# Get api-key and api-salt
Allows third-party systems to get Payport customers’ API authorization info (customer_id, api_key and api_salt) from Payport System.

Request URL:
http://freightdemo.payport.co.nz/customerapi/auth/request_api_info
Required Parameters:
---------------------------------------
* “username”[Compulsory]
* “password”[Compulsory]
* “trust_key” [Optional]
---------------------------------------
“username” refers to the Payport customer login account name.
“password” refers to the Payport login password.
“trust_key” refers to the trust keys given by Payport. Only the trustworthy
customers of Payport can get trust keys. With a valid trust key, Payport system can
automatically create api_key and api_salt for a customer who does not have any
API request information. 

Expected responses:
JSON encoded string contains
--------------------------------------- 
* “customer_id”
* “api_key”
* “api_salt”
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

