# Card Requested Event
This event is generated when applying for new card.
#### Version: 1.0.0

### Schema

```
{
   "$schema":"http://json-schema.org/draft-04/schema#",
   "type":"object",
   "description":"This event is generated when applying for new card.",
   "properties":{
      "header":{
         "type":"object",
         "properties":{
            "id":{
               "type":"string",
               "description":"Generic identifier that contains no sensitive data and represents a unique value for the event being presented"
            },
            "eventTitle":{
               "type":"string",
               "description":"Indicates the title of event"
            },
            "eventType":{
               "type":"string",
               "description":"Indicates the type of event"
            },
            "eventDateTime":{
               "type":"string",
               "description":"Date/time when change occured",
               "Format":"yyyy-MM-dd'T'HH:mm:ss'Z'",
               "example":"2023-10-05T14:45:15Z"
            },
            "eventVersion":{
               "type":"string",
               "description":"Version of the event (starts at \"1.0.\")"
            }
         }
      },
      "data":{
         "type":"object",
         "properties":{
            "originalProcessingDate":{
               "type":"string",
               "description":"procesing date when user apply for new card.",
               "format":"yyyy-MM-dd'T'HH:mm:ss'Z'",
               "example":"2023-10-05T14:45:15Z"
            },
            "productType":{
               "type":"string",
               "description":""
            },
            "financialInstitutionId":{
               "type":"integer",
               "description":"Financial institution identifier - FIID"
            },
            "cardNumber":{
               "type":"string",
               "description":"Encrypted card number provided in place of the true cardNumber as additional level of security"
            },
            "mailingNameLine1":{
               "type":"string",
               "description":""
            },
            "mailingNameLine2":{
               "type":"string",
               "description":""
            },
            "mailingAddressLine3":{
               "type":"string",
               "description":"First line of the cardholder's address."
            },
            "mailingAddressLine4":{
               "type":"string",
               "description":"Second line of the cardholder's address."
            },
            "mailingAddressLine5":{
               "type":"string",
               "description":"Combination of cardholder's address city, state, zip code.",
               "Format":"city  + 2 characters of state + 5-digit (NNNNN) or 9-digit (NNNNN-NNNN)",
               "example":"EDISON NY 30004 or EDISON NY 30004-0895"
            },
            "embossedNameLine1":{
               "type":"string",
               "description":"The primary cardholder name that prints on the card."
            },
            "additionalEmbossedName":{
               "type":"string",
               "description":"Encrypted primary cardholder name that prints on the card."
            },
            "orderStatus":{
               "type":"string",
               "description":"Current status of ordered card"
            },
            "numberOfCards":{
               "type":"string",
               "description":""
            },
            "imageIdentificationValue":{
               "type":"string",
               "description":""
            }
         }
      }
   }
}
```

### Example
```
{
    "header": {
        "id": 6279775,
        "eventTitle": "Card Mailtracker",
        "eventType": "Card",
        "eventDateTime": "2023-10-05T14:45:15Z",
        "eventVersion": "1.0.0"
    },
    "data": {
        "originalProcessingDate": "2023-10-05T14:45:15Z",
        "productType": "",
        "financialInstitutionId": 65200397,
        "cardNumber": "685240DQ0BMR3477",
        "mailingNameLine1": "",
        "mailingNameLine2": "",
        "mailingAddressLine3": "ADRLINE1",
        "mailingAddressLine4": "ADRLINE2",
        "mailingAddressLine5": "EDISON NY 30004",
        "embossedNameLine1": "DONALD AUBREY",
        "additionalEmbossedName": "AUBREY/ DONALD",
        "orderStatus": "New Order",
        "numberOfCards": "",
        "imageIdentificationValue": ""
    }
}
```
