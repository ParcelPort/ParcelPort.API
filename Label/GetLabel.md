# Get label

Request for getting a URL to download the label in PDF from our main site https://freight.payport.co.nz/.

*This API can only be called after the API authentication is approved (the correct
auth string has been passed). 

URL: https://api.parcelport.co.nz/api/1.0/labels?client_id={clientId}&consignmentRef={consignmentRef}

## Required Parameters:
* client_id [Require, client Id]
* consignmentRef [Require, e.g. "00187037343"]

## Example
Request
GET https://api.parcelport.co.nz/api/1.0/labels?client_id=187&consignmentRef=0000187034567

**Headers**
Content-Type: application/json;

**Authorization**
Bearer:bSEX9PltRH8uoHLmFdnt115OqEPPQTrrHpht6Bwq0yos9EW7o6vcBtrV23AF2TcuA8FJTabH_t9x2hDo_tP840QIXfUmg0AGmRBfRHfeTeCjBGrK4ezMuLQ0jsyoDAb3cxUhkMniuJHYfSWhKlvyuQZPDqAffr4ggCY9qiojTgRm1s-EubJZK941SrtXBmTQKnkAWcru5MmXQvm0ziNAfZ_JhCKGoNHhpmnJVfQvGYMQNjMRknoE6GZl63GFZZ9tjMz2ICBPqEJsX67fWOoB2adbr58hA72omCMgLaX-1-DhYjlEnb_qhGljklPL3Qo6ohgykA

**Responses**
``` json
{
    "url": "http://test.parcelport.co.nz/Consignment/DownloadPDF?ConsignmentSel=DW/bS/ZjRLU=",
    "success": true,
    "message": ""
}
```

