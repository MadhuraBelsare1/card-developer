## Card Activation Event

 Event is generated when Card is Activated.
 
#### Version: 1.0.0

### Schema
```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "description": "This event is generated when a Card is activated.",
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
              "description": "Required. Month and year the card record is set to expire. If you enter a date in this field that is less than the old expiration date, a confirmation message displays, enabling you to continue or cancel. If this date is changed, an Account Updater Service (AUS) update record is sent to the networks, unless the option is selected, indicating the cardholder has opted out of AUS.",
              "format": "MM/YY",
              "example": "12/23"
            },
            "oldExpirationDate": {
              "type": "string",
              "description": "Previous expiration date of the selected card. This date could possibly be greater than the date in the Expiration Datefield. If you enter a date in this field that is greater than the expiration date, a confirmation message displays, enabling you to continue or cancel.",
              "format": "MM/YY",
              "example": "12/23"
            },
            "lastActivationAttemptDate": {
              "type": "string",
              "description": "Displays the date the cardholder last attempted to activate the card.",
              "format": "YY-MM-DD",
              "example": "86-12-24"
            },
            "methodUsed": {
              "type": "string",
              "description": "Indicates how the card was activated. If the record was activated manually using force activation, it displays as Operator Activate, otherwise it displays the method used by the cardholder to activate.If the field is blank, the card is not yet activated. Values: 1-First PIN'd (via ATM),2-VRU Activation,3-VRU Caller ID,4-VRU Code and Caller ID,5-Operator Activate",
              "enum": [
                "1",
                "2",
                "3",
                "4",
                "5"
              ]
            },
            "activateStatus": {
              "type": "string",
              "description": "Displays a card's current activation status. Values: 000-Card not activated,001-Card activated,002-Actvn before available date,003-Card record not found,004-Card status is Lost/Stolen,005-Card status is closed,006-No activation required,007-Exp. date doesn't match,008-Card already activated,009-Attempt after deadline,010-Max attempts exceeded,011-Caller ID invalid,012-Activation code invalid,013-PIN check not performed,014-Invalid Actvn method,015-IVR Auth Failed",
              "enum": [
                "000",
                "001",
                "002",
                "003",
                "004",
                "005",
                "006",
                "007",
                "008",
                "009",
                "010",
                "011",
                "012",
                "013",
                "014",
                "015"
              ]
            },
            "phoneUsed": {
              "type": "string",
              "description": "Displays the phone number the cardholder is calling from when attempting to activate the card. It is matched against the Verification Caller ID field value when your FI uses caller ID activation."
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
            },
            "lastActivationAttemptDate": {
              "type": "string",
              "description": "Displays the date the cardholder last attempted to activate the card.",
              "format": "YY-MM-DD",
              "example": "86-12-24"
            },
            "methodUsed": {
              "type": "string",
              "description": "Indicates how the card was activated. If the record was activated manually using force activation, it displays as Operator Activate, otherwise it displays the method used by the cardholder to activate.If the field is blank, the card is not yet activated. Values: 1-First PIN'd (via ATM),2-VRU Activation,3-VRU Caller ID,4-VRU Code and Caller ID,5-Operator Activate",
              "enum": [
                "1",
                "2",
                "3",
                "4",
                "5"
              ]
            },
            "activateStatus": {
              "type": "string",
              "description": "Displays a card's current activation status. Values: 000-Card not activated,001-Card activated,002-Actvn before available date,003-Card record not found,004-Card status is Lost/Stolen,005-Card status is closed,006-No activation required,007-Exp. date doesn't match,008-Card already activated,009-Attempt after deadline,010-Max attempts exceeded,011-Caller ID invalid,012-Activation code invalid,013-PIN check not performed,014-Invalid Actvn method,015-IVR Auth Failed",
              "enum": [
                "000",
                "001",
                "002",
                "003",
                "004",
                "005",
                "006",
                "007",
                "008",
                "009",
                "010",
                "011",
                "012",
                "013",
                "014",
                "015"
              ]
            },
            "phoneUsed": {
              "type": "string",
              "description": "Displays the phone number the cardholder is calling from when attempting to activate the card. It is matched against the Verification Caller ID field value when your FI uses caller ID activation."
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
    "id": "4efd588f-3e10-4e63-99c2-919fdf511d56",
    "eventTitle": "Card Activation",
    "eventType": "Card",
    "eventCode": "Activation",
    "operationType": "Update",
    "eventDateTime": "2023-04-27T20:16:36Z",
    "eventVersion": "1.0.0",
    "source":"C"
  },
  "data": {
    "financialInstitutionId": "65200397",
    "cardNumber": "4000100020003477",
    "nonTransToken": "WUPIL5DQTZGM3477",
    "memberNumber": "0",
    "old": {
      "phoneUsed":"",
      "expirationDate": "04/26",
      "oldExpirationDate": "05/24",
      "methodUsed": "",
      "activateStatus": "000",
      "lastActivationAttemptDate": ""
    },
    "new": {
      "phoneUsed":"1234567890",
      "expirationDate": "04/28",
      "oldExpirationDate": "04/26",
      "methodUsed": "5",
      "activateStatus": "001",
      "lastActivationAttemptDate": "23-03-22"
    }
  }
}
```
