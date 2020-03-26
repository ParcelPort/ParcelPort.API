# POST booking

Creates a pick up event for the requested Pace service.

*This API can only be called after the API authentication is approved (the correct
auth string has been passed). 

URL: https://api.parcelport.co.nz/api/1.0/bookings?client_id={client_id}&consignmentRef={consignmentRef}

## Required Parameters:
* client_id [Require, e.g. "187"]
* consignmentRef [Require, e.g. "00187037343"]

## Example
Request
POST https://api.parcelport.co.nz/api/1.0/bookings?client_id=187&consignmentRef=00187034567

**Headers**
Content-Type: application/json;

**Authorization**
Bearer:bSEX9PltRH8uoHLmFdnt115OqEPPQTrrHpht6Bwq0yos9EW7o6vcBtrV23AF2TcuA8FJTabH_t9x2hDo_tP840QIXfUmg0AGmRBfRHfeTeCjBGrK4ezMuLQ0jsyoDAb3cxUhkMniuJHYfSWhKlvyuQZPDqAffr4ggCY9qiojTgRm1s-EubJZK941SrtXBmTQKnkAWcru5MmXQvm0ziNAfZ_JhCKGoNHhpmnJVfQvGYMQNjMRknoE6GZl63GFZZ9tjMz2ICBPqEJsX67fWOoB2adbr58hA72omCMgLaX-1-DhYjlEnb_qhGljklPL3Qo6ohgykA

**Body**
``` json
{
  "booking":{
      "pickup_option": 0,
  }
}
```

**Responses**
``` json
{
    "success": true
}
```