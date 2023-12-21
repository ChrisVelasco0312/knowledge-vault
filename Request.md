```json
{
  "serviceNumber": "string",
  "creationDate": "2023-12-21T00:11:46.047Z",
  "serviceType": "string",
  "zone": "string",
  "orderStep": "string",
  "callReason": "string",
  "product": "string",
  "serial": "string",
  "attention": {
    "id": "string",
    "startDate": "2023-12-21T00:11:46.047Z",
    "endDate": "2023-12-21T00:11:46.047Z",
    "closeTypeDescription": "string",
    "closeDescription": "string",
    "causeDescription": "string",
    "tecnhnician": {
      "documentId": "string",
      "name": "string",
      "warehouseCode": "string"
    },
    "materials": [
      {
        "code": "string",
        "quantity": 0,
        "description": "string",
        "value": 0,
        "subtotal": 0
      }
    ],
    "collect": {
      "subtotal": 0,
      "iva": 0,
      "total": 0,
      "paymentForms": [
        {
          "description": "string",
          "total": 0,
          "businessCode": "string"
        }
      ]
    },
    "product": {
      "code": "string",
      "description": "string",
      "serial": "string"
    },
    "location": [
      0
    ],
    "client": {
      "documentType": "string",
      "documentId": "string",
      "name": "string",
      "city": "string",
      "cityCode": "string",
      "address": "string",
      "email": "string",
      "habeasData": true
    }
  }
}
```