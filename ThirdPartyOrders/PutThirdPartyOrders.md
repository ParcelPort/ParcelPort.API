# Import a list of third party orders

Allows third-party systems to put a list of orders from their system

URL: https://api.parcelport.co.nz/api/1.0/thirdpartyorders

*This API can only be called after the API authentication is approved (the correct
auth string has been passed). 

## Parameters:
* client_id [Require]
* ref_number [Require, your order Id]
* recipient_contact_name [Optional, contact name]
* recipient_email [Optional, email]
* recipient_company_name [Optional, company name]
* recipient_phone [Optional, contact phone]
* recipient_address_1 [Optional, full address detail]
* recipient_address_suburb [Optional, suburb]
* recipient_address_city [Optional, city]
* recipient_address_country [Optional, country code, e.g., "NZ" for NewZealand]
* recipient_address_postcode [Optional, postcode]

*third_party_order_items*
- **title** - [Require name of the product]
- **quantity** - [Require quantity of the product]
- **width** - [Optional Width of the product]
- **length** - [Optional Length of the product]
- **height** - [Optional Volumn of the product]

## Example
Request
PUT https://api.parcelport.co.nz/api/1.0/thirdpartyorders

**Headers**
Content-Type: application/json;

**Authorization**
Bearer:bSEX9PltRH8uoHLmFdnt115OqEPPQTrrHpht6Bwq0yos9EW7o6vcBtrV23AF2TcuA8FJTabH_t9x2hDo_tP840QIXfUmg0AGmRBfRHfeTeCjBGrK4ezMuLQ0jsyoDAb3cxUhkMniuJHYfSWhKlvyuQZPDqAffr4ggCY9qiojTgRm1s-EubJZK941SrtXBmTQKnkAWcru5MmXQvm0ziNAfZ_JhCKGoNHhpmnJVfQvGYMQNjMRknoE6GZl63GFZZ9tjMz2ICBPqEJsX67fWOoB2adbr58hA72omCMgLaX-1-DhYjlEnb_qhGljklPL3Qo6ohgykA

**Body**
``` json
[  
  {  
     "client_id":110,
     "ref_number":"11001",
     "recipient_contact_name":"Tony",
     "recipient_email":"test@parecelport.co.nz",
     "recipient_company_name":"testcompany",
     "recipient_phone":"12345678",
     "recipient_address_1":"17 witbrock Crecent",
     "recipient_address_suburb":"Burnside",
     "recipient_address_city":"Christchurch",
     "recipient_address_country": "NZ",
     "recipient_address_postcode": "8053",
     
     "third_party_orders_items":[  
        {  
           "title":"TV",
           "quantity":1,
           "weight":1.5,
           "width":30,
           "length":50,
           "height":10
        },
        {  
           "title":"Playstaion",
           "quantity":1,
           "weight":2,
           "width":20,
           "length":20,
           "height":10
        }
     ]
  },
  {  
     "client_id":110,
     "ref_number":"11002",
     "recipient_contact_name":"Jing",
     "recipient_email":"test@parecelport.co.nz",
     "recipient_company_name":"testcompany",
     "recipient_phone":"12345678",
     "recipient_address_1":"27 witbrock Crecent",
     "recipient_address_suburb":"Burnside",
     "recipient_address_city":"Christchurch",
     "recipient_address_country": "NZ",
     "recipient_address_postcode": "8053",
     
     "third_party_orders_items":[  
        {  
           "title":"Laptop",
           "quantity":1,
           "weight":1.5,
           "width":30,
           "length":50,
           "height":10
        },
        {  
           "title":"IPad",
           "quantity":1,
           "weight":2,
           "width":20,
           "length":20,
           "height":10
        }
     ]
  }
]
```
**Responses**
A JSON encoded string contains the third party order Id for each order

``` json
[
    {
        "refNumber": "11001",
        "isSuccess": true,
        "thirdPartyOrdersId": 117285,
        "error": ""
    },
    {
        "refNumber": "11002",
        "isSuccess": true,
        "thirdPartyOrdersId": 117286,
        "error": ""
    }
]
```

***