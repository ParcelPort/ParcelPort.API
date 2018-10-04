# ParcelPort System API(v1.0)

Parcel Port API provides an access to enable your customer to send parcels using our system.

***

# Get token
Allows third-party systems to get Payport customers’ API authorization token from Payport System. The token will expire in 30Mins

Request URL:
http://api.parcelport.co.nz/token

## Required Parameters:
* username [Require]
* password [Require]
* grant_type [Optional]

Supported HTTP methods: POST
Example call in Postman

Content-Type: application/x-www-form-urlencoded
Body:{
    username:"Test"
    password:"Password"
    grant_type: "password"
}

Response:
{
    "access_token": "U995BbNx_JQZPozAd6QZPBUc6M7PMwXQUMS_dU42IJ-bDd635VLC1q-ksDO2EnUCsJvo6hrFiiE_KkXcsDOguj1wISMudM45DTWNwE9E-4Ik0DdK6e-U-KU8CSdXyD8K0lJArHMpff7m1DWIV0OgBDY73S7w18P12ygXRZBcbiwkynQpKwDgR6WzQouTmSOoXcwYajV8aDo7fKNqyDn32n7hY79ADz8-yfRUK_f7_ynIvvyuoJI43NsFNy46d4YYjD9zyU-rz0tu-kTVkWfq4zVT3msOfiMZCSkCPgUuOeXvglsf-iyktWZZRAg4p1cEVVc3-Wo0wRuuMwqoA0Dx_Q",
    "token_type": "bearer",
    "expires_in": 1799,
    "client_id": "187",
    "userName": "saintsco",
    ".issued": "Thu, 30 Aug 2018 23:31:53 GMT",
    ".expires": "Fri, 31 Aug 2018 00:01:53 GMT"
} 

***

# Shipping
- **[<code>POST</code> /api/1.0/shippingoptions](Shipping/GetShippingMethod.md)** returns a list of available shipping methods

# Make a consignment
- **[<code>POST</code> /api/1.0/consignment](Consignment/PostConsignment.md)** Post a consignment

# Label
- **[<code>GET</code> /api/1.0/labels](Label/GetLabel.md)** Get a url of label(PDF)

# Booking
- **[<code>GET</code> /api/1.0/bookings](Booking/GetBooking.md)** Booking a pickup time

# Tracking
- **[<code>GET</code> /api/1.0/tracking](Tracking/GetTracking.md)** Get tracking history of the consignment