# Card Pin Offset Event
Event is generated when Pin Offset is updated
#### Version: 1.0.0

### Schema
```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "description": "This event is generated when Pin Offset is updated",
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
            "pinOffset": {
              "type": "string",
              "description": "Personal identification number offset. Required. Used by the card vendor to calculate the PIN number for the card. Based on your FI's setup."
            },
            "pinOffsetChangedDate": {
              "type": "string",
              "description": "Personal identification number offset changed. Date of the most recent PINOffset change.",
              "format": "YYYY-MM-DD"
            }
          }
        },
        "new": {
          "type": "object",
          "properties": {
            "pinOffset": {
              "type": "string",
              "description": "Personal identification number offset. Required. Used by the card vendor to calculate the PIN number for the card. Based on your FI's setup."
            },
            "pinOffsetChangedDate": {
              "type": "string",
              "description": "Personal identification number offset changed. Date of the most recent PINOffset change.",
              "format": "YYYY-MM-DD"
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
        "id": "d37e38f9-5b77-471d-9a90-7bc4161b6bcc",
        "eventTitle": "PIN Offset",
        "eventType": "Card",
        "eventCode": "PINOffset",
        "operationType": "Update",
        "eventDateTime": "2023-05-05T16:44:47Z",
        "eventVersion": "1.0.0",
        "source":"C"
    },
    "data": {
        "financialInstitutionId": "65200397",
        "cardNumber": "4000100020003477",
        "nonTransToken": "WUPIL5DQTZGM3477",
        "memberNumber": "0",
        "old": {
            "pinOffset": "sdgfh234#",
            "pinOffsetChangedDate": ""
        },
        "new": {
            "pinOffset": "sgsd42asfd$",
            "pinOffsetChangedDate": "2023-05-15"
        }
    }
}

```
