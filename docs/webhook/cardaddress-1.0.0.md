# Card Address Event
## Event is generated when there is a change on the Card Address.
#### Version: 1.0.0

## Schema
```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
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
		  "description": "Decrypted/masted card number"
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
            "primaryAddress": {
              "type": "object",
              "properties": {
                "addressLine1": {
                  "type": "string",
                  "description": "First line of the cardholder's address."
                },
                "addressLine2": {
                  "type": "string",
                  "description": "Second line of the cardholder's address."
                },
                "city": {
                  "type": "string",
                  "description": "City of the cardholder's address."
                },
                "state": {
                  "type": "string",
                  "description": "State code of the cardholder's address.",
                  "format": "Format - 2 characters",
                  "example": "NJ"
                },
                "country": {
                  "type": "string",
                  "description": "Country associated with the cardholder's address."
                },
                "zip": {
                  "type": "string",
                  "description": "Postal code of the cardholder's address. Format - 5-digit (NNNNN) or 9-digit (NNNNN-NNNN) code for U.S.",
                  "example": "30004 or 30004-0895"
                }
              }
            },
            "alternateAddress": {
              "type": "object",
              "properties": {
                "addressLine1": {
                  "type": "string",
                  "description": " First line of the cardholder's alternate address."
                },
                "addressLine2": {
                  "type": "string",
                  "description": "Second line of the cardholder's alternate address."
                },
                "city": {
                  "type": "string",
                  "description": "City of the cardholder's alternate address."
                },
                "state": {
                  "type": "string",
                  "description": "State code of the cardholder's alternate address.",
                  "format": "Format - 2 characters",
                  "example": "NJ"
                },
                "country": {
                  "type": "string",
                  "description": "Country associated with the cardholder's alternate address."
                },
                "zip": {
                  "type": "string",
                  "description": "Postal code of the cardholder's alternate address. Format - 5-digit (NNNNN) or 9-digit (NNNNN-NNNN) code for U.S.",
                  "example": "30004 or 30004-0895"
                }
              }
            }
          }
        },
        "new": {
          "type": "object",
          "properties": {
            "primaryAddress": {
              "type": "object",
              "properties": {
                "addressLine1": {
                  "type": "string",
                  "description": "First line of the cardholder's address."
                },
                "addressLine2": {
                  "type": "string",
                  "description": "Second line of the cardholder's address."
                },
                "city": {
                  "type": "string",
                  "description": "City of the cardholder's address."
                },
                "state": {
                  "type": "string",
                  "description": "State code of the cardholder's address.",
                  "format": "Format - 2 characters",
                  "example": "NJ"
                },
                "country": {
                  "type": "string",
                  "description": "Country associated with the cardholder's alternate address."
                },
                "zip": {
                  "type": "string",
                  "description": "Postal code of the cardholder's alternate address. Format - 5-digit (NNNNN) or 9-digit (NNNNN-NNNN) code for U.S.",
                  "example": "30004 or 30004-0895"
                }
              }
            },
            "alternateAddress": {
              "type": "object",
              "properties": {
                "addressLine1": {
                  "type": "string",
                  "description": " First line of the cardholder's alternate address."
                },
                "addressLine2": {
                  "type": "string",
                  "description": "Second line of the cardholder's alternate address."
                },
                "city": {
                  "type": "string",
                  "description": "City of the cardholder's alternate address."
                },
                "state": {
                  "type": "string",
                  "description": "State code of the cardholder's alternate address.",
                  "format": "Format - 2 characters",
                  "example": "NJ"
                },
                "country": {
                  "type": "string",
                  "description": "Country associated with the cardholder's alternate address."
                },
                "zip": {
                  "type": "string",
                  "description": "Postal code of the cardholder's alternate address. Format - 5-digit (NNNNN) or 9-digit (NNNNN-NNNN) code for U.S.",
                  "example": "30004 or 30004-0895"
                }
              }
            }
          }
        }
      },
      "required": [
        "cardNumber",
        "memberNumber"
      ]
    }
  }
}
```

## Example
```
{
  "header": {
    "id": "36f537d2-9835-4894-83bf-653afbafb2dc",
    "eventTitle": "Demographic Updates",
    "eventType": "Card",
    "eventCode": "Address",
    "operationType": "Update",
    "eventDateTime": "2023-04-27T20:02:13Z",
    "eventVersion": "1.0.0",
    "source":"C"
  },
  "data": {
    "financialInstitutionId": "65200397",
    "cardNumber": "4000100020005487",
    "nonTransToken": "WUPIL5DQTZGM5487",
    "memberNumber": "0",
    "old": {
      "primaryAddress": {
        "addressLine1": "ADR1",
        "addressLine2": "ADR2",
        "city": "ISELIN",
        "state": "NJ",
        "country": "USA",
        "zip": "08830"
      },
      "alternateAddress": {
        "addressLine1": "ALTADR1",
        "addressLine2": "ALTADR2",
        "city": "ISELIN",
        "state": "NJ",
        "country": "USA",
        "zip": "08854"
      }
    },
    "new": {
      "primaryAddress": {
        "addressLine1": "ADRLINE1",
        "addressLine2": "ADRLINE2",
        "city": "EDISON",
        "state": "NY",
        "country": "USA",
        "zip": "08834"
      },
      "alternateAddress": {
        "addressLine1": "ALTADRLINE1",
        "addressLine2": "ALTADRLINE2",
        "city": "EDISON",
        "state": "NY",
        "country": "USA",
        "zip": "08824"
      }
    }
  }
}

```





