# Card Limits Event
## Event is generated when a card limit is updated.
#### Version: 1.0.0

## Schema
```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "description": "This event is generated when a card limit is updated.",
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
            "dailyLimits": {
              "type": "object",
              "properties": {
                "atmTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for ATM transctions"
                },
                "atmOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for offline ATM transactions"
                },
                "posTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for Point of Sale transactions"
                },
                "posOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for offline Point of Sale transactions"
                },
                "signatureDebitPOSTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for signature debit Point of Sale transactions"
                },
                "signatureDebitPOSOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for offline debit Point of Sale transactions"
                },
                "cashAdvanceTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend for cash advance transactions"
                },
                "cashAdvanceOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend for offline cash advance transactions"
                },
                "customerNPTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend for Customer Not Present transactions"
                },
                "customerNPOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend for offline Customer Not Present transactions"
                },
                "cashEquivTotalAmount": {
                  "type": "string",
                  "description": "Daily limit total spend for cash equivalent transactions"
                },
                "cashEquivOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit total spend for offline cash equivalent transactions"
                },
                "aggregateTotalAmount": {
                  "type": "string",
                  "description": "Daily limit spend for aggregate total transactions"
                },
                "aggregateOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit spend for offline aggregate total transctions"
                },
                "mtFundingAmtPerTranTotalAmount": {
                  "type": "string",
                  "description": "Daily limit spend for Money Transfer amount per transaction"
                },
                "mtFundingAmtPerTranOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit spend for offline Money Transfer per transaction"
                },
                "mtFundingDlyCntTotal": {
                  "type": "string",
                  "description": "Daily transaction count limit for Money Transfer transactions"
                },
                "mtFundingDlyCntOffline": {
                  "type": "string",
                  "description": "Daily transaction offline count limit for Money Transfer transctions"
                },
                "mtFundingDlyTotalAmount": {
                  "type": "string",
                  "description": "Daily limit spend for Money Transfer total transactions"
                },
                "mtFundingDlyOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit spend for offline Money Transfer total transctions"
                },
                "mtCreditPerTranTotalAmount": {
                  "type": "string",
                  "description": "Limit for a credit for Money Transfer per transaction"
                },
                "mtCreditPerTranOfflineAmount": {
                  "type": "string",
                  "description": "Limit for an offline credit for Money Transfer per transaction"
                },
                "mtCreditDlyCntTotal": {
                  "type": "string",
                  "description": "Daily transaction count limit for credits for Money Transfer transctions"
                },
                "mtCreditDlyCntOffline": {
                  "type": "string",
                  "description": "Daily transaction count limit for offline credits for Money Transfer transactions"
                },
                "mtCreditDlyTotalAmount": {
                  "type": "string",
                  "description": "Daily limit for credits total amount for Money Transfer transactions"
                },
                "mtCreditDlyOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit for offline credits total amount for Money Transfer transactions"
                }
              }
            },
            "velocityLimits": {
              "type": "object",
              "properties": {
                "atmMaxCardUsage": {
                  "type": "string",
                  "description": "Velocity limit for maximum ATM card usage"
                },
                "posMaxCardUsage": {
                  "type": "string",
                  "description": "Velocity limit for maximum Point of Sale card usage"
                },
                "cashEquivMaxCardUsage": {
                  "type": "string",
                  "description": "Velocity limit for maximum cash equivalent card usage"
                },
                "aggMaxCardUsage": {
                  "type": "string",
                  "description": "Velocity limit for maximum aggregate card usage"
                },
                "atmTimeInterval": {
                  "type": "string",
                  "description": "Velocity limit for ATM interval time",
                  "format": "HH:MM",
                  "example": "12:00"
                },
                "posTimeInterval": {
                  "type": "string",
                  "description": "Velocity limit for Point of Sale interval time",
                  "format": "HH:MM",
                  "example": "10:00"
                },
                "cashEquivTimeInterval": {
                  "type": "string",
                  "description": "Velocity limit for Cash Equivalent interval time",
                  "format": "HH:MM",
                  "example": "24:00"
                },
                "aggTimeInterval": {
                  "type": "string",
                  "description": "Velocity limit for aggregate interval time",
                  "format": "HH:MM",
                  "example": "12:00"
                }
              }
            },
            "openToBuyLimits": {
              "type": "object",
              "properties": {
                "accountOpenToBuyTotalAmount": {
                  "type": "string",
                  "description": "Account Open to Buy Total Amount limit"
                },
                "accountOpenToBuyOfflineAmount": {
                  "type": "string",
                  "description": "Account Open to Buy Offline Total Amount limit"
                },
                "cardOpenToBuyTotalAmount": {
                  "type": "string",
                  "description": "Card Open to Buy Total Amount limit"
                },
                "cardOpenToBuyOfflineAmount": {
                  "type": "string",
                  "description": "Card Open to Buy Offline Total Amount limit"
                }
              }
            }
          }
        },
        "new": {
          "type": "object",
          "properties": {
            "dailyLimits": {
              "type": "object",
              "properties": {
                "atmTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for ATM transctions"
                },
                "atmOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for offline ATM transactions"
                },
                "posTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for Point of Sale transactions"
                },
                "posOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for offline Point of Sale transactions"
                },
                "signatureDebitPOSTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for signature debit Point of Sale transactions"
                },
                "signatureDebitPOSOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend amount for offline debit Point of Sale transactions"
                },
                "cashAdvanceTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend for cash advance transactions"
                },
                "cashAdvanceOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend for offline cash advance transactions"
                },
                "customerNPTotalAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend for Customer Not Present transactions"
                },
                "customerNPOfflineAmount": {
                  "type": "string",
                  "description": "Daily Limit total spend for offline Customer Not Present transactions"
                },
                "cashEquivTotalAmount": {
                  "type": "string",
                  "description": "Daily limit total spend for cash equivalent transactions"
                },
                "cashEquivOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit total spend for offline cash equivalent transactions"
                },
                "aggregateTotalAmount": {
                  "type": "string",
                  "description": "Daily limit spend for aggregate total transactions"
                },
                "aggregateOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit spend for offline aggregate total transctions"
                },
                "mtFundingAmtPerTranTotalAmount": {
                  "type": "string",
                  "description": "Daily limit spend for Money Transfer amount per transaction"
                },
                "mtFundingAmtPerTranOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit spend for offline Money Transfer per transaction"
                },
                "mtFundingDlyCntTotal": {
                  "type": "string",
                  "description": "Daily transaction count limit for Money Transfer transactions"
                },
                "mtFundingDlyCntOffline": {
                  "type": "string",
                  "description": "Daily transaction offline count limit for Money Transfer transctions"
                },
                "mtFundingDlyTotalAmount": {
                  "type": "string",
                  "description": "Daily limit spend for Money Transfer total transactions"
                },
                "mtFundingDlyOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit spend for offline Money Transfer total transctions"
                },
                "mtCreditPerTranTotalAmount": {
                  "type": "string",
                  "description": "Limit for a credit for Money Transfer per transaction"
                },
                "mtCreditPerTranOfflineAmount": {
                  "type": "string",
                  "description": "Limit for an offline credit for Money Transfer per transaction"
                },
                "mtCreditDlyCntTotal": {
                  "type": "string",
                  "description": "Daily transaction count limit for credits for Money Transfer transctions"
                },
                "mtCreditDlyCntOffline": {
                  "type": "string",
                  "description": "Daily transaction count limit for offline credits for Money Transfer transactions"
                },
                "mtCreditDlyTotalAmount": {
                  "type": "string",
                  "description": "Daily limit for credits total amount for Money Transfer transactions"
                },
                "mtCreditDlyOfflineAmount": {
                  "type": "string",
                  "description": "Daily limit for offline credits total amount for Money Transfer transactions"
                }
              }
            },
            "velocityLimits": {
              "type": "object",
              "properties": {
                "atmMaxCardUsage": {
                  "type": "string",
                  "description": "Velocity limit for maximum ATM card usage"
                },
                "posMaxCardUsage": {
                  "type": "string",
                  "description": "Velocity limit for maximum Point of Sale card usage"
                },
                "cashEquivMaxCardUsage": {
                  "type": "string",
                  "description": "Velocity limit for maximum cash equivalent card usage"
                },
                "aggMaxCardUsage": {
                  "type": "string",
                  "description": "Velocity limit for maximum aggregate card usage"
                },
                "atmTimeInterval": {
                  "type": "string",
                  "description": "Velocity limit for ATM interval time",
                  "format": "HH:MM",
                  "example": "24:00"
                },
                "posTimeInterval": {
                  "type": "string",
                  "description": "Velocity limit for Point of Sale interval time",
                  "format": "HH:MM",
                  "example": "12:00"
                },
                "cashEquivTimeInterval": {
                  "type": "string",
                  "description": "Velocity limit for Cash Equivalent interval time",
                  "format": "HH:MM",
                  "example": "10:00"
                },
                "aggTimeInterval": {
                  "type": "string",
                  "description": "Velocity limit for aggregate interval time",
                  "format": "HH:MM",
                  "example": "04:00"
                }
              }
            },
            "openToBuyLimits": {
              "type": "object",
              "properties": {
                "accountOpenToBuyTotalAmount": {
                  "type": "string",
                  "description": "Account Open to Buy Total Amount limit"
                },
                "accountOpenToBuyOfflineAmount": {
                  "type": "string",
                  "description": "Account Open to Buy Offline Total Amount limit"
                },
                "cardOpenToBuyTotalAmount": {
                  "type": "string",
                  "description": "Card Open to Buy Total Amount limit"
                },
                "cardOpenToBuyOfflineAmount": {
                  "type": "string",
                  "description": "Card Open to Buy Offline Total Amount limit"
                }
              }
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

## Example
```
{
  "header": {
    "id": "d37e38f9-5b77-471d-9a90-7bc4161b6bcc",
    "eventTitle": "Limits",
    "eventType": "Card",
    "eventCode": "Limits",
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
      "dailyLimits": {
        "atmTotalAmount": "2000",
        "atmOfflineAmount": "200",
        "posTotalAmount": "3000",
        "posOfflineAmount": "400",
        "signatureDebitPOSTotalAmount": "0",
        "signatureDebitPOSOfflineAmount": "0",
        "cashAdvanceTotalAmount": "0",
        "cashAdvanceOfflineAmount": "0",
        "customerNPTotalAmount": "0",
        "customerNPOfflineAmount": "0",
        "cashEquivTotalAmount": "500",
        "cashEquivOfflineAmount": "100",
        "aggregateTotalAmount": "0",
        "aggregateOfflineAmount": "0",
        "mtFundingAmtPerTranTotalAmount": "0",
        "mtFundingAmtPerTranOfflineAmount": "0",
        "mtFundingDlyCntTotal": "0",
        "mtFundingDlyCntOffline": "0",
        "mtFundingDlyTotalAmount": "0",
        "mtFundingDlyOfflineAmount": "0",
        "mtCreditPerTranTotalAmount": "0",
        "mtCreditPerTranOfflineAmount": "0",
        "mtCreditDlyCntTotal": "0",
        "mtCreditDlyCntOffline": "0",
        "mtCreditDlyTotalAmount": "0",
        "mtCreditDlyOfflineAmount": "0"
      },
      "velocityLimits": {
        "atmMaxCardUsage": "20",
        "posMaxCardUsage": "4",
        "cashEquivMaxCardUsage": "4",
        "aggMaxCardUsage": "20",
        "atmTimeInterval": "610",
        "posTimeInterval": "610",
        "cashEquivTimeInterval": "610",
        "aggTimeInterval": "610"
      },
      "openToBuyLimits": {
        "accountOpenToBuyTotalAmount": "9999",
        "accountOpenToBuyOfflineAmount": "123",
        "cardOpenToBuyTotalAmount": "9999",
        "cardOpenToBuyOfflineAmount": "123"
      }
    },
    "new": {
      "dailyLimits": {
        "atmTotalAmount": "1000",
        "atmOfflineAmount": "100",
        "posTotalAmount": "3000",
        "posOfflineAmount": "300",
        "signatureDebitPOSTotalAmount": "10",
        "signatureDebitPOSOfflineAmount": "10",
        "cashAdvanceTotalAmount": "10",
        "cashAdvanceOfflineAmount": "10",
        "customerNPTotalAmount": "10",
        "customerNPOfflineAmount": "10",
        "cashEquivTotalAmount": "400",
        "cashEquivOfflineAmount": "200",
        "aggregateTotalAmount": "20",
        "aggregateOfflineAmount": "20",
        "mtFundingAmtPerTranTotalAmount": "20",
        "mtFundingAmtPerTranOfflineAmount": "20",
        "mtFundingDlyCntTotal": "30",
        "mtFundingDlyCntOffline": "40",
        "mtFundingDlyTotalAmount": "30",
        "mtFundingDlyOfflineAmount": "40",
        "mtCreditPerTranTotalAmount": "50",
        "mtCreditPerTranOfflineAmount": "10",
        "mtCreditDlyCntTotal": "20",
        "mtCreditDlyCntOffline": "90",
        "mtCreditDlyTotalAmount": "60",
        "mtCreditDlyOfflineAmount": "50"
      },
      "velocityLimits": {
        "atmMaxCardUsage": "30",
        "posMaxCardUsage": "3",
        "cashEquivMaxCardUsage": "3",
        "aggMaxCardUsage": "10",
        "atmTimeInterval": "24:00",
        "posTimeInterval": "24:00",
        "cashEquivTimeInterval": "12:00",
        "aggTimeInterval": "24:00"
      },
      "openToBuyLimits": {
        "accountOpenToBuyTotalAmount": "1000",
        "accountOpenToBuyOfflineAmount": "223",
        "cardOpenToBuyTotalAmount": "1000",
        "cardOpenToBuyOfflineAmount": "223"
      }
    }
  }
}

```
