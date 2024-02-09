# Prior Card Logic
## Event to provide information on the utilization of the logic put in place to populate previous card on Card Add Event
#### Version: 1.0.0

## Schema
```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "description": “Event to provide information on the utilization of the logic put in place to populate previous card on Card Add Event”,
  "properties": {
    "header": {
      "type": "object",
      "properties": {
        "id": {
          "type": "string",
          "description": "Generic identifier that contains no sensitive data and represents a unique value for the event being presented"
        },
        "eventTitle": {
          "type": "string",
          "description": "Indicates the title of event"
        },
        "eventType": {
          "type": "string",
          "description": "Indicates the type of event"
        },
        "eventCode": {
          "type": "string",
          "description": ""
        },
        "operationType": {
          "type": "string",
          "description": "Indicates the type of change"
        },
        "eventDateTime": {
          "type": "string",
          "description": "Date/time when change occured"
        },
        "eventVersion": {
          "type": "string",
          "description": "Version of the event (starts at \"1.0.\")"
        }
      }
    },
    "data": {
      "type": "object",
      "properties": {
        "financialInstitutionId": {
          "type": "string",
          "description": "Financial institution identifier - FIID"
        },
        "cardNumber": {
          "type": "string",
          "description": "Decrypted card number provided in place of the true PAN as additional level of security"
        },
        "nonTransToken": {
          "type": "string",
          "description": "NTT card number provided"
        },
        "memberNumber": {
          "type": "string",
          "description": "Unique number associated with each member of the card",
          "format": " 1 digit; depending on card prefix, values include 0 (zero) or 1–9"
        },
        "priorCardFoundByCardLogic": {
          "type": "string",
          "description": "Invoking Prioir Card Found Logic, Values : Y = Prior Card logic invoked and previous card match found, N = Prior Card logic invoked and no previous card match found",
          "enum": [
            "Y",
            "N"
          ]
        }
      },
      "required": [
        "cardNumber",
        "memberNumber",
        "financialInstitutionId"
      ]
    }
  }
}
```

## Example
```
{
    "header": {
        "id": "2a9867f7-cb47-4966-8494-1b7e541a2e2f",
        "eventTitle": "Card Prior Card Logic",
        "eventType": "Card",
        "eventCode": "Prior Card Logic",
        "operationType": "Add",
        "eventDateTime": "2023-08-03T07:45:57Z",
        "eventVersion": "1.0.0"
    },
    "data": {
        "cardNumber": "4000100020003477",
        "nonTransToken": "WUPIL5DQTZGM3477",
        "memberNumber": "0",
        "financialInstitutionId": "77778333",
        "priorCardFoundByCardLogic":"Y"
    }
}

```
