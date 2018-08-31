# Get booking

Creates a pick up event for the requested Pace service.

*This API can only be called after the API authentication is approved (the correct
auth string has been passed). 

URL: http://api.parcelport.co.nz/api/bookings?client_id=187&consignment_ref=001870375897&instruction=test%20only%20no%20pickup%20up

## Required Parameters:
* client_id [Require, e.g. "187"]
* consignment_ref [Require, e.g. "00187037343"]
* instruction [Optional]
