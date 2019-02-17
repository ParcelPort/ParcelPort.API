# Get Tracking History

Request for tracking history of a consignment

*This API can only be called after the API authentication is approved (the correct
auth string has been passed). 

URL: https://api.parcelport.co.nz/api/1.0/tracking?consignment_ref={consignmentRef}

## Required Parameters:
* consignmentRef [Require, e.g. "00187037343"]

## Example
Request
GET https://api.parcelport.co.nz/api/1.0/tracking?consignmentRef=001870375905

**Headers**
Content-Type: application/json;

**Authorization**
Bearer:bSEX9PltRH8uoHLmFdnt115OqEPPQTrrHpht6Bwq0yos9EW7o6vcBtrV23AF2TcuA8FJTabH_t9x2hDo_tP840QIXfUmg0AGmRBfRHfeTeCjBGrK4ezMuLQ0jsyoDAb3cxUhkMniuJHYfSWhKlvyuQZPDqAffr4ggCY9qiojTgRm1s-EubJZK941SrtXBmTQKnkAWcru5MmXQvm0ziNAfZ_JhCKGoNHhpmnJVfQvGYMQNjMRknoE6GZl63GFZZ9tjMz2ICBPqEJsX67fWOoB2adbr58hA72omCMgLaX-1-DhYjlEnb_qhGljklPL3Qo6ohgykA

**Responses**
``` json
[
    {
        "pc": 2727123,
        "description": "Pick up booked, waiting for pickup",
        "date_added": "2019-02-13T17:36:59.91",
        "status_time": "2019-02-13T17:36:59.91",
        "notes": "GE322435603NZ"
    }
]
```
* Return an empty result if there are no any tracking.