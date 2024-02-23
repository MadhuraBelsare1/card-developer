# Card Expiration Date Event
 Event is generated when a Card expiration date is updated.
#### Version: 1.0.0

### Schema
```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "description": "This event is generated when a Card expiration date is updated.",
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
        },
        "source": {
          "type": "string",
          "description": "The source to add/update the card record Values :  1 = External API,2 = Card Console,3 = Card Hub,4 = ECHO,5 = Test API,6 = Domain Services,A = Admin (not currently used),B = Batch Processing,C = CWSi,D = CM2 Conversion or Kit,E = CM2 Remote Card Maintenance,F = CM2 FHM (ISO or HISO),F = FUN server,G = CM2 Conversion (Internal RCM),H = Card Alert Tracking,I = Integrated Desktop,J = Case Tracker (reserved),k = HOT requestor,L= PIN activation server,M = Pin By Phone (Unix),N = RuleManager,O = Reissue (Tandem),P = Reissue (Unix),Q = AlertBroker Gateway,R = Refresh,V = VRU,U  = Unknown",
          "enum": [
            "1",
            "2",
            "3",
            "4",
            "5",
            "6",
            "A",
            "B",
            "C",
            "D",
            "E",
            "F",
            "G",
            "H",
            "I",
            "J",
            "K",
            "L",
            "M",
            "N",
            "O",
            "P",
            "Q",
            "R",
            "V",
            "U"
          ]
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
          "description": "Encrypted card number provided in place of the true PAN as additional level of security"
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
        "old": {
          "type": "object",
          "properties": {
            "expirationDate": {
              "type": "string",
              "description": "Required. Month and year the card record is set to expire. If you enter a date in this field that is less than the old expiration date, a confirmation message displays, enabling you to continue or cancel.If this date is changed, an Account Updater Service (AUS) update record is sent to the networks, unless the option is selected, indicating the cardholder has opted out of AUS.",
              "format": "MM/YY",
              "example": "12/23"
            },
            "oldExpirationDate": {
              "type": "string",
              "description": "Previous expiration date of the selected card. This date could possibly be greater than the date in the Expiration Datefield. If you enter a date in this field that is greater than the expiration date, a confirmation message displays, enabling you to continue or cancel.",
              "format": "MM/YY",
              "example": "12/23"
            }
          }
        },
        "new": {
          "type": "object",
          "properties": {
            "expirationDate": {
              "type": "string",
              "description": "Required. Month and year the card record is set to expire. If you enter a date in this field that is less than the old expiration date, a confirmation message displays, enabling you to continue or cancel. If this date is changed, an Account Updater Service (AUS) update record is sent to the networks, unless the option is selected, indicating the cardholder has opted out of AUS.",
              "format": "MM/YY",
              "example": "12/23"
            },
            "oldExpirationDate": {
              "type": "string",
              "description": "Previous expiration date of the selected card. This date could possibly be greater than the date in the Expiration Datefield. If you enter a date in this field that is greater than the expiration date, a confirmation message displays, enabling you to continue or cancel.",
              "format": "MM/YY",
              "example": "12/23"
            }
          }
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
### Example
```
{
    "header": {
        "id": "df5e4eb9-fdea-41eb-be44-3a9e0579f482",
        "eventTitle": "Expiration Date",
        "eventType": "Card",
        "eventCode": "Expiration",
        "operationType": "Update",
        "eventDateTime": "2023-05-02T12:07:33Z",
        "eventVersion": "1.0.0",
        "source":"C"
    },
    "data": {
        "financialInstitutionId": "65200397",
        "cardNumber": "4000100020003477",
        "nonTransToken": "WUPIL5DQTZGM3477",
        "memberNumber": "0",
        "old": {
            "oldExpirationDate": "",
            "expirationDate": "04/26"
        },
        "new": {
            "oldExpirationDate": "04/26",
            "expirationDate": "04/28"
        }
    }
}

```
