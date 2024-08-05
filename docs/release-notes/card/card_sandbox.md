# Test Cases

<span style="color:#ff6600;">**Card API Endpoints**</span>

When testing these endpoints, please use the test cases and test data from the Sandbox.

## Activations

**Credit**

### Credit Activate v1: Activate inactive card
This case activates a card.

#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations
```
{
      "cardNumber": "4000100020003001"
  }
```
##### Response
**HTTP Code:** 200 OK
```
{
      "cardType": "CREDIT",
      "cardActivationStatus": "ACTIVATED"
  }
```

### Credit Activate v1: Search for inactive card
This case demonstrates when the card is inactive.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search
```
{
      "cardNumber": "4000100020003001"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardType": "CREDIT",
      "cardActivationStatus": "ACTIVATION_REQUIRED"
  }
```

### Credit Activate v1: Search for active card
This case demonstrates when the card is active.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search
```
{
      "cardNumber": "4000200030004001"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardType": "CREDIT",
      "cardActivationStatus": "NO_ACTIVATION_REQUIRED"
  }
```

**Debit**

### Debit Activate v1: Activate inactive card using card number
This case activates a debit card.

#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations
```
{
      "cardNumber": "4000100020003000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400010XXXXXX3000",
      "cardType": "DEBIT",
      "activationRequiredByDate": "2021-10-31",
      "availableForUseDate": "2021-07-26",
      "cardActivationDate": "2021-09-23",
      "cardActivationStatus": "ACTIVATED",
      "lastActivationAttemptDate": "2021-09-23",
      "activationMethod": "OPERATOR_ACTIVATE",
      "numberOfAttempts": "0",
      "verificationCallerID": "9900020"
  }
```
### Debit Activate v1: Activate inactive card using NTT
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations
```
{
      "nonTransToken": "hggLkjgJGSwh3000"
  }
```  
#### Response
**HTTP Code:** 200 OK
```
{
      "nonTransToken": "hggLkjgJGSwh3000",
      "cardType": "DEBIT",
      "activationRequiredByDate": "2021-10-31",
      "availableForUseDate": "2021-07-26",
      "cardActivationDate": "2021-09-23",
      "cardActivationStatus": "ACTIVATED",
      "lastActivationAttemptDate": "2021-09-23",
      "activationMethod": "OPERATOR_ACTIVATE",
      "numberOfAttempts": "0",
      "verificationCallerID": "9900020"
  }
```
### Debit Activate v1: Search for inactive card using card number
This case demonstrates when the debit card is inactive.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search
```
{
      "cardNumber": "4000100020003000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400010XXXXXX3000",
      "cardType": "DEBIT",
      "activationRequiredByDate": "2021-10-31",
      "availableForUseDate": "2021-07-26",
      "cardActivationStatus": "NOT_ACTIVATED",
      "numberOfAttempts": "0"
  }
```

### Debit Activate v1: Search for inactive card using NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search
```
{
      "nonTransToken": "hggLkjgJGSwh3000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "nonTransToken": "hggLkjgJGSwh3000",
      "cardType": "DEBIT",
      "activationRequiredByDate": "2021-10-31",
      "availableForUseDate": "2021-07-26",
      "cardActivationStatus": "NOT_ACTIVATED",
      "numberOfAttempts": "0"
  }
```

### Debit Activate v1: Search for active card using card number
This case demonstrates when the debit card is activated.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search
```
{
      "cardNumber": "4000200030004000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "cardType": "DEBIT",
      "activationRequiredByDate": "2022-12-31",
      "cardActivationDate": "2021-09-21",
      "cardActivationStatus": "ACTIVATED",
      "lastActivationAttemptDate": "2021-09-21",
      "activationMethod": "OPERATOR_ACTIVATE",
      "numberOfAttempts": "1"
  }
```

### Debit Activate v1: Search for active card using NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search
```
{
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "cardType": "DEBIT",
      "activationRequiredByDate": "2022-12-31",
      "cardActivationDate": "2021-09-21",
      "cardActivationStatus": "ACTIVATED",
      "lastActivationAttemptDate": "2021-09-21",
      "activationMethod": "OPERATOR_ACTIVATE",
      "numberOfAttempts": "1"
  }
```

## Add
**Version 2**

**Credit**

**Add Credit Card**
### Not Using Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/card
```
{
  "cardNumber": "",
  "cardType": "CREDIT",
  "creditOnly": {
    "plasticsCount": "00",
    "cardStatus": "NORMAL",
    "statusReasonCode": "NORMAL",
    "association": "PRIMARY",
    "customerRoleTypeCode": "02",
    "cardStock": "00",
    "producePlasticIdentifier": "Y",
    "creditCardholderAddress": {
      "isFormattedAddress": false,
      "addressLine1": "123 Any Street",
      "addressLine2": "Apt 100",
      "addressLine3": "LAKE VIEW",
      "addressLine4": "AVENUE",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "addressType": "PLASTIC",
      "categoryCode": "TEMPORARY",
      "beginDate": "2021-08-03",
      "endDate": "2022-08-03"
    },
    "creditCardholderName": {
      "cardholderName": "Doe, John H",
      "personalizedEmbossingText": "Home Team",
      "specialHandling": "NONE"
    },
    "creditContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "123005678",
      "taxIdType": "EIN",
      "motherMaidenName": "Smith"
    },
    "creditAssociatedAccounts": {
      "accountNumber": "123456789",
      "accountType": "Individual",
      "accountStatus": "ACTIVE"
    }
  }
}
```
#### Response
**HTTP Code:** 201 Created
```
{
  "cardNumber": "4000100020003001",
  "cardType": "CREDIT",
  "emvCard": "CONTACT",
  "creditOnly": {
    "plasticsCount": "00",
    "cardStatus": "NORMAL",
    "statusReasonCode": "NORMAL",
    "expirationDate": "10/23",
    "association": "PRIMARY",
    "customerRoleTypeCode": "02",
    "cardStock": "00",
    "producePlasticIdentifier": "Y",
    "creditCardholderAddress": {
      "isFormattedAddress": false,
      "addressLine1": "123 Any Street",
      "addressLine2": "Apt 100",
      "addressLine3": "LAKE VIEW",
      "addressLine4": "AVENUE",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "addressType": "PLASTIC",
      "categoryCode": "TEMPORARY",
      "beginDate": "2021-08-03",
      "endDate": "2022-08-03"
    },
    "creditCardholderName": {
      "cardholderName": "Doe, John H",
      "personalizedEmbossingText": "Home Team",
      "specialHandling": "NONE"
    },
    "creditContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "XXXXX5678",
      "taxIdType": "EIN",
      "motherMaidenName": "Smith"
    },
    "creditAssociatedAccounts": {
      "accountNumber": "123456789",
      "accountType": "Individual",
      "accountStatus": "ACTIVE"
    }
  }
}
```
### Not Using Card Number and Using Full Card and Token Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/card
```
{
  "cardNumber": "",
  "nonTransTokenFlag": true,
  "responseFormat": "FULL_CARD_AND_TOKEN",
  "cardType": "CREDIT",
  "creditOnly": {
    "plasticsCount": "00",
    "cardStatus": "NORMAL",
    "statusReasonCode": "NORMAL",
    "association": "PRIMARY",
    "customerRoleTypeCode": "02",
    "cardStock": "00",
    "producePlasticIdentifier": "Y",
    "creditCardholderAddress": {
      "isFormattedAddress": false,
      "addressLine1": "123 Any Street",
      "addressLine2": "Apt 100",
      "addressLine3": "LAKE VIEW",
      "addressLine4": "AVENUE",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "addressType": "PLASTIC",
      "categoryCode": "TEMPORARY",
      "beginDate": "2021-08-03",
      "endDate": "2022-08-03"
    },
    "creditCardholderName": {
      "cardholderName": "Doe, John H",
      "personalizedEmbossingText": "Home Team",
      "specialHandling": "NONE"
    },
    "creditContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "123005678",
      "taxIdType": "EIN",
      "motherMaidenName": "Smith"
    },
    "creditAssociatedAccounts": {
      "accountNumber": "123456789",
      "accountType": "Individual",
      "accountStatus": "ACTIVE"
    }
  }
}
```
#### Response
**HTTP Code:** 201 Created
```
{
  "cardNumber": "4000200030004001",
  "nonTransToken": "pSAZIXCAXrAo4001",
  "cardType": "CREDIT",
  "emvCard": "CONTACT",
  "creditOnly": {
    "plasticsCount": "00",
    "cardStatus": "NORMAL",
    "statusReasonCode": "NORMAL",
    "expirationDate": "10/23",
    "association": "PRIMARY",
    "customerRoleTypeCode": "02",
    "cardStock": "00",
    "producePlasticIdentifier": "Y",
    "creditCardholderAddress": {
      "isFormattedAddress": false,
      "addressLine1": "123 Any Street",
      "addressLine2": "Apt 100",
      "addressLine3": "LAKE VIEW",
      "addressLine4": "AVENUE",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "addressType": "PLASTIC",
      "categoryCode": "TEMPORARY",
      "beginDate": "2021-08-03",
      "endDate": "2022-08-03"
    },
    "creditCardholderName": {
      "cardholderName": "Doe, John H",
      "personalizedEmbossingText": "Home Team",
      "specialHandling": "NONE"
    },
    "creditContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "XXXXX5678",
      "taxIdType": "EIN",
      "motherMaidenName": "Smith"
    },
    "creditAssociatedAccounts": {
      "accountNumber": "123456789",
      "accountType": "Individual",
      "accountStatus": "ACTIVE"
    }
  }
}
```
### Not Using Card Number and Using Masked Card and Token Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/card
```
{
  "cardNumber": "",
  "nonTransTokenFlag": true,
  "responseFormat": "MASKED_CARD_AND_TOKEN",
  "cardType": "CREDIT",
  "creditOnly": {
    "plasticsCount": "00",
    "cardStatus": "NORMAL",
    "statusReasonCode": "NORMAL",
    "association": "PRIMARY",
    "customerRoleTypeCode": "02",
    "cardStock": "00",
    "producePlasticIdentifier": "Y",
    "creditCardholderAddress": {
      "isFormattedAddress": false,
      "addressLine1": "123 Any Street",
      "addressLine2": "Apt 100",
      "addressLine3": "LAKE VIEW",
      "addressLine4": "AVENUE",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "addressType": "PLASTIC",
      "categoryCode": "TEMPORARY",
      "beginDate": "2021-08-03",
      "endDate": "2022-08-03"
    },
    "creditCardholderName": {
      "cardholderName": "Doe, John H",
      "personalizedEmbossingText": "Home Team",
      "specialHandling": "NONE"
    },
    "creditContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "123005678",
      "taxIdType": "EIN",
      "motherMaidenName": "Smith"
    },
    "creditAssociatedAccounts": {
      "accountNumber": "123456789",
      "accountType": "Individual",
      "accountStatus": "ACTIVE"
    }
  }
}
```
##### Response
**HTTP Code:** 201 Created
```
{
  "cardNumber": "400020XXXXXX4001",
  "nonTransToken": "pSAZIXCAXrAo4001",
  "cardType": "CREDIT",
  "emvCard": "CONTACT",
  "creditOnly": {
    "plasticsCount": "00",
    "cardStatus": "NORMAL",
    "statusReasonCode": "NORMAL",
    "expirationDate": "10/23",
    "association": "PRIMARY",
    "customerRoleTypeCode": "02",
    "cardStock": "00",
    "producePlasticIdentifier": "Y",
    "creditCardholderAddress": {
      "isFormattedAddress": false,
      "addressLine1": "123 Any Street",
      "addressLine2": "Apt 100",
      "addressLine3": "LAKE VIEW",
      "addressLine4": "AVENUE",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "addressType": "PLASTIC",
      "categoryCode": "TEMPORARY",
      "beginDate": "2021-08-03",
      "endDate": "2022-08-03"
    },
    "creditCardholderName": {
      "cardholderName": "Doe, John H",
      "personalizedEmbossingText": "Home Team",
      "specialHandling": "NONE"
    },
    "creditContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "XXXXX5678",
      "taxIdType": "EIN",
      "motherMaidenName": "Smith"
    },
    "creditAssociatedAccounts": {
      "accountNumber": "123456789",
      "accountType": "Individual",
      "accountStatus": "ACTIVE"
    }
  }
}
```
### Not Using Card Number and Using Token Only Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/card
```
{
  "cardNumber": "",
  "nonTransTokenFlag": true,
  "responseFormat": "TOKEN_ONLY",
  "cardType": "CREDIT",
  "creditOnly": {
    "plasticsCount": "00",
    "cardStatus": "NORMAL",
    "statusReasonCode": "NORMAL",
    "association": "PRIMARY",
    "customerRoleTypeCode": "02",
    "cardStock": "00",
    "producePlasticIdentifier": "Y",
    "creditCardholderAddress": {
      "isFormattedAddress": false,
      "addressLine1": "123 Any Street",
      "addressLine2": "Apt 100",
      "addressLine3": "LAKE VIEW",
      "addressLine4": "AVENUE",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "addressType": "PLASTIC",
      "categoryCode": "TEMPORARY",
      "beginDate": "2021-08-03",
      "endDate": "2022-08-03"
    },
    "creditCardholderName": {
      "cardholderName": "Doe, John H",
      "personalizedEmbossingText": "Home Team",
      "specialHandling": "NONE"
    },
    "creditContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "123005678",
      "taxIdType": "EIN",
      "motherMaidenName": "Smith"
    },
    "creditAssociatedAccounts": {
      "accountNumber": "123456789",
      "accountType": "Individual",
      "accountStatus": "ACTIVE"
    }
  }
}
```
#### Response
**HTTP Code:** 201 Created
```
{
  "nonTransToken": "pSAZIXCAXrAo4001",
  "cardType": "CREDIT",
  "emvCard": "CONTACT",
  "creditOnly": {
    "plasticsCount": "00",
    "cardStatus": "NORMAL",
    "statusReasonCode": "NORMAL",
    "expirationDate": "10/23",
    "association": "PRIMARY",
    "customerRoleTypeCode": "02",
    "cardStock": "00",
    "producePlasticIdentifier": "Y",
    "creditCardholderAddress": {
      "isFormattedAddress": false,
      "addressLine1": "123 Any Street",
      "addressLine2": "Apt 100",
      "addressLine3": "LAKE VIEW",
      "addressLine4": "AVENUE",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "addressType": "PLASTIC",
      "categoryCode": "TEMPORARY",
      "beginDate": "2021-08-03",
      "endDate": "2022-08-03"
    },
    "creditCardholderName": {
      "cardholderName": "Doe, John H",
      "personalizedEmbossingText": "Home Team",
      "specialHandling": "NONE"
    },
    "creditContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "XXXXX5678",
      "taxIdType": "EIN",
      "motherMaidenName": "Smith"
    },
    "creditAssociatedAccounts": {
      "accountNumber": "123456789",
      "accountType": "Individual",
      "accountStatus": "ACTIVE"
    }
  }
}
```
**Templates**

### Retrieve Credit Template with Account Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/template
```
{
    "creditOnly": {
        "accountNumber": "123456789"
    }
}
```
                        
#### Response
**HTTP Code:** 200 OK

```                            
{
    "cardNumber": "",
    "cardType": "CREDIT",
    "creditOnly": {
        "plasticsCount": "00",
        "cardStatus": "NORMAL",
        "statusReasonCode": "NORMAL",
        "association": "PRIMARY",
        "customerRoleTypeCode": "02",
        "cardStock": "00",
        "producePlasticIdentifier": "Y",
        "creditCardholderAddress": {
            "isFormattedAddress": false,
            "addressLine1": "123 Any Street",
            "addressLine2": "Apt 100",
            "addressLine3": "LAKEVIEW",
            "addressLine4": "AVENUE",
            "city": "Newark",
            "countryCode": "USA",
            "stateCode": "NJ",
            "zipCode": "12345",
            "addressType": "PLASTIC",
            "categoryCode": "TEMPORARY",
            "beginDate": "2021-08-03",
            "endDate": "2022-08-03"
        },
        "creditCardholderName": {
            "cardholderName": "Doe, John H",
            "personalizedEmbossingText": "Home Team",
            "specialHandling": "NONE"
        },
        "creditContactInfo": {
            "allowVoiceCommunication": false,
            "allowTextCommunication": false,
            "homePhone": "1005550001",
            "workPhone": "1005550001",
            "cellPhone": "1005550001",
            "emailAddress": "jdoe@example.com",
            "dateOfBirth": "1990-08-24",
            "taxIdOrSsn": "XXXXX5678",
            "taxIdType": "EIN",
            "motherMaidenName": "Smith"
        },
        "creditAssociatedAccounts": {
            "accountNumber": "123456789",
            "accountType": "Individual",
            "accountStatus": "ACTIVE"
        }
    }
}
```
## Add Credit Card
**Version 1**

**Credit**

### Card Number Provided

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/card
```
{
      "cardNumber": "4000200030004001",
      "cardType": "CREDIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "creditOnly": {
          "plasticsCount": "00",
          "cardStatus": "NORMAL",
          "statusReasonCode": "NORMAL",
          "association": "PRIMARY",
          "customerRoleTypeCode": "01",
          "cardStock": "00",
          "producePlasticIdentifier": "N",
          "creditPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3"
          },
          "creditCardholderAddress": {
              "isFormattedAddress": true,
              "addressLine1": "123 Any Street",
              "addressLine2": "Apt 100",
              "addressLine3": "LAKE VIEW",
              "addressLine4": "AVENUE",
              "city": "Newark",
              "country": "USA",
              "state": "NJ",
              "zipCode": "12345",
              "addressType": "BILLING",
              "categoryCode": "PERMANENT",
              "beginDate": "2021-08-03",
              "endDate": "2022-08-03"
          },
          "creditCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "specialHandling": "NONE"
          },
          "creditContactInfo": {
              "allowVoiceCommunication": false,
              "allowTextCommunication": false,
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "emailAddress": "jdoe@example.com",
              "dateOfBirth": "1990-08-24",
              "taxIdOrSsn": "987001234",
              "taxIdType": "SSN",
              "motherMaidenName": "Chris Smith"
          },
          "creditAssociatedAccounts": {
              "accountNumber": "123456789",
              "accountType": "Consumer",
              "accountStatus": "ACTIVE"
          }
      }
  }
```
#### Response
**HTTP Code:** 201 Created
```
{
      "card": {
          "cardNumber": "4000200030004001",
          "expirationDate": "10/23",
          "cardStatus": "NORMAL",
          "statusReasonCode": "NORMAL",
          "plasticsCount": "00",
          "association": "PRIMARY",
          "customerRoleTypeCode": "01",
          "maxAuthorizationPerDayCount": 0,
          "emvCard": "CONTACT",
          "cardStock": "00",
          "cardholderAddress": [
              {
                  "isFormattedAddress": true,
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "addressLine3": "LAKE VIEW",
                  "addressLine4": "AVENUE",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "BILLING",
                  "categoryCode": "PERMANENT",
                  "beginDate": "2021-08-03",
                  "endDate": "2022-08-03"
              }
          ]
      },
      "cardholderName": {
          "cardholderName": "Smith, Alex J",
          "personalizedEmbossingText": "Home Team",
          "specialHandling": "NONE"
      },
      "contactInfo": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "emailAddress": "jdoe@email.com",
          "dateOfBirth": "1990-08-24",
          "taxIdOrSsn": "XXXXX1234",
          "taxIdType": "SSN",
          "motherMaidenName": "Chris Smith"
      },
      "associatedAccounts": [
          {
              "accountNumber": "123456789",
              "accountType": "Consumer",
              "accountStatus": "ACTIVE"
          }
      ]
  }
```

### No Card Number Provided
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/card
```
{
      "cardNumber": "",
      "cardType": "CREDIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "creditOnly": {
          "plasticsCount": "00",
          "cardStatus": "NORMAL",
          "statusReasonCode": "NORMAL",
          "association": "PRIMARY",
          "customerRoleTypeCode": "01",
          "cardStock": "00",
          "producePlasticIdentifier": "N",
          "creditPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3"
          },
          "creditCardholderAddress": {
              "isFormattedAddress": true,
              "addressLine1": "123 Any Street",
              "addressLine2": "Apt 100",
              "addressLine3": "LAKE VIEW",
              "addressLine4": "AVENUE",
              "city": "Newark",
              "country": "USA",
              "state": "NJ",
              "zipCode": "12345",
              "addressType": "BILLING",
              "categoryCode": "PERMANENT",
              "beginDate": "2021-08-03",
              "endDate": "2022-08-03"
          },
          "creditCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "specialHandling": "NONE"
          },
          "creditContactInfo": {
              "allowVoiceCommunication": false,
              "allowTextCommunication": false,
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "emailAddress": "jdoe@example.com",
              "dateOfBirth": "1990-08-24",
              "taxIdOrSsn": "987001234",
              "taxIdType": "SSN",
              "motherMaidenName": "Chris Smith"
          },
          "creditAssociatedAccounts": {
              "accountNumber": "123456789",
              "accountType": "Consumer",
              "accountStatus": "ACTIVE"
          }
      }
  }
```
#### Response
**HTTP Code:** 201 Created
```
{
      "card": {
          "cardNumber": "4000200030004001",
          "expirationDate": "10/23",
          "cardStatus": "NORMAL",
          "statusReasonCode": "NORMAL",
          "plasticsCount": "00",
          "association": "PRIMARY",
          "customerRoleTypeCode": "01",
          "maxAuthorizationPerDayCount": 0,
          "emvCard": "CONTACT",
          "cardStock": "00",
          "cardholderAddress": [
              {
                  "isFormattedAddress": true,
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "addressLine3": "LAKE VIEW",
                  "addressLine4": "AVENUE",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "BILLING",
                  "categoryCode": "PERMANENT",
                  "beginDate": "2021-08-03",
                  "endDate": "2022-08-03"
              }
          ]
      },
      "cardholderName": {
          "cardholderName": "Smith, Alex J",
          "personalizedEmbossingText": "Home Team",
          "specialHandling": "NONE"
      },
      "contactInfo": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "emailAddress": "jdoe@email.com",
          "dateOfBirth": "1990-08-24",
          "taxIdOrSsn": "XXXXX1234",
          "taxIdType": "SSN",
          "motherMaidenName": "Chris Smith"
      },
      "associatedAccounts": [
          {
              "accountNumber": "123456789",
              "accountType": "Consumer",
              "accountStatus": "ACTIVE"
          }
      ]
}
```
**Templates**

### Retrieve Credit Template with Account Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/template
```
{
      "accountNumber": "123456789"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "",
      "cardType": "CREDIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "creditOnly": {
          "plasticsCount": "00",
          "cardStatus": "NORMAL",
          "statusReasonCode": "NORMAL",
          "association": "PRIMARY",
          "customerRoleTypeCode": "02",
          "cardStock": "00",
          "producePlasticIdentifier": "Y",
          "creditPINInfo": {
              "pinOffset": "1234",
              "maximumPINTriesAllowed": "4"
          },
          "creditCardholderAddress": {
              "isFormattedAddress": false,
              "addressLine1": "123 Any Street",
              "addressLine2": "Apt 100",
              "addressLine3": "LAKEVIEW",
              "addressLine4": "AVENUE",
              "city": "Newark",
              "country": "USA",
              "state": "New Jersey",
              "zipCode": "12345",
              "addressType": "PLASTIC",
              "categoryCode": "TEMPORARY",
              "beginDate": "2021-08-03",
              "endDate": "2022-08-03"
          },
          "creditCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "specialHandling": "NONE"
          },
          "creditContactInfo": {
              "allowVoiceCommunication": false,
              "allowTextCommunication": false,
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactPhone": "1005550001",
              "textAddress": "1005550001",
              "emailAddress": "alexsmith@example.com",
              "dateOfBirth": "1990-08-24",
              "taxIdOrSsn": "XXXXX5678",
              "taxIdType": "EIN",
              "motherMaidenName": "Smith"
          },
          "creditAssociatedAccounts": {
              "accountNumber": "123456789",
              "accountType": "Individual",
              "accountStatus": "ACTIVE"
          }
      }
  }
```

### Retrieve Credit Template with Prior Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v1/cards/template
```
{
      "priorCardNumber": "4000200030004001"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "",
      "cardType": "CREDIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "creditOnly": {
          "plasticsCount": "00",
          "cardStatus": "NORMAL",
          "statusReasonCode": "NORMAL",
          "association": "PRIMARY",
          "customerRoleTypeCode": "02",
          "cardStock": "00",
          "producePlasticIdentifier": "Y",
          "creditPINInfo": {
              "pinOffset": "1234",
              "maximumPINTriesAllowed": "4"
          },
          "creditCardholderAddress": {
              "isFormattedAddress": false,
              "addressLine1": "123 Any Street",
              "addressLine2": "Apt 100",
              "addressLine3": "LAKEVIEW",
              "addressLine4": "AVENUE",
              "city": "Newark",
              "country": "USA",
              "state": "New Jersey",
              "zipCode": "12345",
              "addressType": "PLASTIC",
              "categoryCode": "TEMPORARY",
              "beginDate": "2021-08-03",
              "endDate": "2022-08-03"
          },
          "creditCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "specialHandling": "NONE"
          },
          "creditContactInfo": {
              "allowVoiceCommunication": false,
              "allowTextCommunication": false,
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactPhone": "1005550001",
              "textAddress": "1005550001",
              "emailAddress": "alexsmith@example.com",
              "dateOfBirth": "1990-08-24",
              "taxIdOrSsn": "XXXXX5678",
              "taxIdType": "EIN",
              "motherMaidenName": "Smith"
          },
          "creditAssociatedAccounts": {
              "accountNumber": "123456789",
              "accountType": "Individual",
              "accountStatus": "ACTIVE"
          }
      }
  }
```
**Version 2**

**Debit**

**Add Debit Card**
### Using Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/card
```
{
  "cardNumber": "4000100020003000",
  "cardType": "DEBIT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234"
    },
    "debitPriorCardInfo": {
      "priorCardNumber": "4000100020003000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "123005678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```
#### Response
**HTTP Code:** 201 Created
```
{
  "cardNumber": "400010XXXXXX3000",
  "cardType": "DEBIT",
  "emvCard": "CONTACT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234",
      "maximumPINTriesAllowed": "4",
      "pinOffsetChangeDate": "2014-10-02"
    },
    "debitPriorCardInfo": {
      "priorCardNumber": "400010XXXXXX3000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "XXXXX5678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```

### Not Using Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/card
```
{
  "cardNumber": "",
  "cardType": "DEBIT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234"
    },
    "debitPriorCardInfo": {
      "priorCardNumber": "4000100020003000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "123005678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```
#### Response
**HTTP Code:** 201 Created
```
{
  "cardNumber": "4000100020003000",
  "cardType": "DEBIT",
  "emvCard": "CONTACT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234",
      "maximumPINTriesAllowed": "4",
      "pinOffsetChangeDate": "2014-10-02"
    },
    "debitPriorCardInfo": {
      "priorCardNumber": "400010XXXXXX3000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "XXXXX5678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```

### Not Using Card Number and Using Full Card and Token Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/card
```
{
  "cardNumber": "",
  "nonTransTokenFlag": true,
  "responseFormat": "FULL_CARD_AND_TOKEN",
  "cardType": "DEBIT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234"
    },
    "debitPriorCardInfo": {
      "priorCardNumber": "4000100020004000",
      "priorNonTransToken": "WUPIL5DQTZGM4000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "123005678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```
#### Response
**HTTP Code:** 201 Created
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "cardType": "DEBIT",
  "emvCard": "CONTACT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234",
      "maximumPINTriesAllowed": "4",
      "pinOffsetChangeDate": "2014-10-02"
    },
    "debitPriorCardInfo": {
      "priorCardNumber": "4000100020004000",
      "priorNonTransToken": "WUPIL5DQTZGM4000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "XXXXX5678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```

### Not Using Card Number and Using Masked Card and Token Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/card
```
{
  "cardNumber": "",
  "nonTransTokenFlag": true,
  "responseFormat": "MASKED_CARD_AND_TOKEN",
  "cardType": "DEBIT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234"
    },
    "debitPriorCardInfo": {
      "priorCardNumber": "4000100020004000",
      "priorNonTransToken": "WUPIL5DQTZGM4000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "123005678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```
#### Response
**HTTP Code:** 201 Created
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "cardType": "DEBIT",
  "emvCard": "CONTACT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234",
      "maximumPINTriesAllowed": "4",
      "pinOffsetChangeDate": "2014-10-02"
    },
    "debitPriorCardInfo": {
      "priorCardNumber": "400010XXXXXX4000",
      "priorNonTransToken": "WUPIL5DQTZGM4000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "XXXXX5678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```

### Not Using Card Number and Using Token Only Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/card
```
{
  "cardNumber": "",
  "nonTransTokenFlag": true,
  "responseFormat": "TOKEN_ONLY",
  "cardType": "DEBIT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234"
    },
    "debitPriorCardInfo": {
      "priorCardNumber": "4000100020004000",
      "priorNonTransToken": "WUPIL5DQTZGM4000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "123005678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```
#### Response
**HTTP Code:** 201 Created
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "cardType": "DEBIT",
  "emvCard": "CONTACT",
  "debitOnly": {
    "cardStatus": "ACTIVE",
    "statusReasonCode": "NONE",
    "memberNumber": "0",
    "expirationDate": "10/23",
    "cardClass": "AAA00",
    "memberSinceDate": "09/23",
    "branch": "0000",
    "reissuePerCardClass": true,
    "updaterServiceOptOut": false,
    "debitPINInfo": {
      "pinOffset": "1234",
      "maximumPINTriesAllowed": "4",
      "pinOffsetChangeDate": "2014-10-02"
    },
    "debitPriorCardInfo": {
      "priorNonTransToken": "WUPIL5DQTZGM4000",
      "priorMemberNumber": "0",
      "priorCardExpirationDate": "10/23"
    },
    "debitCardholderAddressPrimary": {
      "addressLine1": "123 Any Street",
      "addressLine2": "123 Any Lane",
      "city": "Newark",
      "countryCode": "USA",
      "stateCode": "NJ",
      "zipCode": "12345",
      "cardMailerIndicator": true,
      "pinMailerIndicator": true
    },
    "debitCardholderAddressAlternate": {
      "addressLine1": "456 Any Street",
      "addressLine2": "456 Any Lane",
      "city": "Naples",
      "countryCode": "USA",
      "stateCode": "FL",
      "zipCode": "33962",
      "cardMailerIndicator": false,
      "pinMailerIndicator": false
    },
    "debitCardholderName": {
      "cardholderName": "Doe, John H",
      "additionalEmbossLine": "Home Team",
      "photoId": "EFGH",
      "plasticId": "PM001",
      "rushType": "NONE",
      "orderType": "CARD",
      "nameSuffix": "MD"
    },
    "debitContactInfo": {
      "homePhone": "1005550001",
      "workPhone": "1005550001",
      "cellPhone": "1005550001",
      "alternateContactName": "Doe, John H",
      "textAddress": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "taxIdOrSsn": "XXXXX5678",
      "verificationText": "Driver's license",
      "motherMaidenName": "Smith",
      "activationType": "SOCIAL_SECURITY_NUMBER",
      "activationValue": "5678"
    },
    "debitAssociatedAccounts": [
      {
        "accountNumber": "987654321",
        "accountType": "CHECKING",
        "accountDescription": "Main account",
        "primaryAccount": "Y",
        "accountStatus": "ACTIVE"
      }
    ]
  }
}
```
**Templates**

### Retrieve Debit Template with cardNumber
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/template

```                            
{
    "debitOnly": {
        "cardNumber": "4000200030004000"
    }
}
```                        
                        
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "",
    "cardType": "DEBIT",
    "cardGeneratorIndicator": "S",
    "nonTransTokenFlag": true,
    "tspUpdateFlag": true,
    "debitOnly": {
        "cardStatus": "ACTIVE",
        "statusReasonCode": "NONE",
        "memberNumber": "0",
        "expirationDate": "10/23",
        "cardClass": "AAA00",
        "memberSinceDate": "09/23",
        "branch": "0000",
        "reissuePerCardClass": true,
        "updaterServiceOptOut": false,
        "debitPINInfo": {
            "pinOffset": "1234"
        },
        "debitPriorCardInfo": {
            "priorCardNumber": "400020XXXXXX4000",
            "priorNonTransToken": "",
            "priorMemberNumber": "0",
            "priorCardExpirationDate": "10/23"
        },
        "debitCardholderAddressPrimary": {
            "addressLine1": "123 Any Street",
            "addressLine2": "123 Any Lane",
            "city": "Newark",
            "countryCode": "USA",
            "stateCode": "NJ",
            "zipCode": "12345",
            "cardMailerIndicator": true,
            "pinMailerIndicator": true
        },
        "debitCardholderAddressAlternate": {
            "addressLine1": "456 Any Street",
            "addressLine2": "456 Any Lane",
            "city": "Naples",
            "countryCode": "USA",
            "stateCode": "FL",
            "zipCode": "33962",
            "cardMailerIndicator": false,
            "pinMailerIndicator": false
        },
        "debitCardholderName": {
            "cardholderName": "Doe, John H",
            "additionalEmbossLine": "Home Team",
            "photoId": "EFGH",
            "plasticId": "PM001",
            "rushType": "NONE",
            "orderType": "CARD",
            "nameSuffix": "MD"
        },
        "debitContactInfo": {
            "homePhone": "1005550001",
            "workPhone": "1005550001",
            "cellPhone": "1005550001",
            "alternateContactName": "Doe, John H",
            "textAddress": "0005550000",
            "emailAddress": "jdoe@example.com",
            "dateOfBirth": "1990-08-24",
            "taxIdOrSsn": "XXXXX5678",
            "verificationText": "Driver's license",
            "motherMaidenName": "Smith",
            "activationType": "SOCIAL_SECURITY_NUMBER",
            "activationValue": ""
        },
        "debitAssociatedAccounts": [
            {
                "accountNumber": "987654321",
                "accountType": "CHECKING",
                "accountDescription": "Main account",
                "primaryAccount": "Y",
                "accountStatus": "ACTIVE"
            }
        ]
    }
}
```
### Retrieve Debit Template with cardNumber and memberNumber
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/template

```                          
{
    "debitOnly": {
        "cardNumber": "4000200030004000",
        "memberNumber": "0"
    }
}
```                        
                        
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "",
    "cardType": "DEBIT",
    "cardGeneratorIndicator": "S",
    "nonTransTokenFlag": true,
    "tspUpdateFlag": true,
    "debitOnly": {
        "cardStatus": "ACTIVE",
        "statusReasonCode": "NONE",
        "memberNumber": "0",
        "expirationDate": "10/23",
        "cardClass": "AAA00",
        "memberSinceDate": "09/23",
        "branch": "0000",
        "reissuePerCardClass": true,
        "updaterServiceOptOut": false,
        "debitPINInfo": {
            "pinOffset": "1234"
        },
        "debitPriorCardInfo": {
            "priorCardNumber": "400020XXXXXX4000",
            "priorNonTransToken": "",
            "priorMemberNumber": "0",
            "priorCardExpirationDate": "10/23"
        },
        "debitCardholderAddressPrimary": {
            "addressLine1": "123 Any Street",
            "addressLine2": "123 Any Lane",
            "city": "Newark",
            "countryCode": "USA",
            "stateCode": "NJ",
            "zipCode": "12345",
            "cardMailerIndicator": true,
            "pinMailerIndicator": true
        },
        "debitCardholderAddressAlternate": {
            "addressLine1": "456 Any Street",
            "addressLine2": "456 Any Lane",
            "city": "Naples",
            "countryCode": "USA",
            "stateCode": "FL",
            "zipCode": "33962",
            "cardMailerIndicator": false,
            "pinMailerIndicator": false
        },
        "debitCardholderName": {
            "cardholderName": "Doe, John H",
            "additionalEmbossLine": "Home Team",
            "photoId": "EFGH",
            "plasticId": "PM001",
            "rushType": "NONE",
            "orderType": "CARD",
            "nameSuffix": "MD"
        },
        "debitContactInfo": {
            "homePhone": "1005550001",
            "workPhone": "1005550001",
            "cellPhone": "1005550001",
            "alternateContactName": "Doe, John H",
            "textAddress": "0005550000",
            "emailAddress": "jdoe@example.com",
            "dateOfBirth": "1990-08-24",
            "taxIdOrSsn": "XXXXX5678",
            "verificationText": "Driver's license",
            "motherMaidenName": "Smith",
            "activationType": "SOCIAL_SECURITY_NUMBER",
            "activationValue": ""
        },
        "debitAssociatedAccounts": [
            {
                "accountNumber": "987654321",
                "accountType": "CHECKING",
                "accountDescription": "Main account",
                "primaryAccount": "Y",
                "accountStatus": "ACTIVE"
            }
        ]
    }
}
```  
### Retrieve Debit Template with cardClass
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/template

```                            
{
    "debitOnly": {
        "cardClass": "AAA00"
    }
}
```                        
                        
#### Response
**HTTP Code:** 200 OK

```                            
{
    "cardNumber": "",
    "cardType": "DEBIT",
    "cardGeneratorIndicator": "S",
    "nonTransTokenFlag": true,
    "tspUpdateFlag": true,
    "debitOnly": {
        "cardStatus": "ACTIVE",
        "statusReasonCode": "NONE",
        "memberNumber": "0",
        "expirationDate": "",
        "cardClass": "AAA00",
        "memberSinceDate": "09/23",
        "branch": "0000",
        "reissuePerCardClass": true,
        "updaterServiceOptOut": false,
        "debitPINInfo": {
            "pinOffset": ""
        },
        "debitPriorCardInfo": {
            "priorCardNumber": "",
            "priorNonTransToken": "",
            "priorMemberNumber": "",
            "priorCardExpirationDate": ""
        },
        "debitCardholderAddressPrimary": {
            "addressLine1": "",
            "addressLine2": "",
            "city": "",
            "countryCode": "",
            "stateCode": "",
            "zipCode": "",
            "cardMailerIndicator": true,
            "pinMailerIndicator": true
        },
        "debitCardholderAddressAlternate": {
            "addressLine1": "",
            "addressLine2": "",
            "city": "",
            "countryCode": "",
            "stateCode": "",
            "zipCode": "",
            "cardMailerIndicator": false,
            "pinMailerIndicator": false
        },
        "debitCardholderName": {
            "cardholderName": "",
            "additionalEmbossLine": "",
            "photoId": "",
            "plasticId": "",
            "rushType": "NONE",
            "orderType": "CARD",
            "nameSuffix": ""
        },
        "debitContactInfo": {
            "homePhone": "",
            "workPhone": "",
            "cellPhone": "",
            "alternateContactName": "",
            "textAddress": "",
            "emailAddress": "",
            "dateOfBirth": "",
            "taxIdOrSsn": "",
            "verificationText": "",
            "motherMaidenName": "",
            "activationType": "SOCIAL_SECURITY_NUMBER",
            "activationValue": ""
        },
        "debitAssociatedAccounts": [
            {
                "accountNumber": "",
                "accountType": "",
                "accountDescription": "",
                "primaryAccount": "Y",
                "accountStatus": "ACTIVE"
            }
        ]
    }
}
```

### Retrieve Debit Template with nonTransToken
#### Request
**HTTP Method:**POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/template

```                            
{
    "debitOnly": {
        "nonTransToken": "piUVBJKZGfks4000"
    }
}
```    
                        
#### Response
**HTTP Code:** 200 OK

```                            
{
    "cardNumber": "",
    "cardType": "DEBIT",
    "cardGeneratorIndicator": "S",
    "nonTransTokenFlag": true,
    "tspUpdateFlag": true,
    "debitOnly": {
        "cardStatus": "ACTIVE",
        "statusReasonCode": "NONE",
        "memberNumber": "0",
        "expirationDate": "10/23",
        "cardClass": "AAA00",
        "memberSinceDate": "09/23",
        "branch": "0000",
        "reissuePerCardClass": true,
        "updaterServiceOptOut": false,
        "debitPINInfo": {
            "pinOffset": "1234"
        },
        "debitPriorCardInfo": {
            "priorCardNumber": "",
            "priorNonTransToken": "piUVBJKZGfks4000",
            "priorMemberNumber": "0",
            "priorCardExpirationDate": "10/23"
        },
        "debitCardholderAddressPrimary": {
            "addressLine1": "123 Any Street",
            "addressLine2": "123 Any Lane",
            "city": "Newark",
            "countryCode": "USA",
            "stateCode": "NJ",
            "zipCode": "12345",
            "cardMailerIndicator": true,
            "pinMailerIndicator": true
        },
        "debitCardholderAddressAlternate": {
            "addressLine1": "456 Any Street",
            "addressLine2": "456 Any Lane",
            "city": "Naples",
            "countryCode": "USA",
            "stateCode": "FL",
            "zipCode": "33962",
            "cardMailerIndicator": false,
            "pinMailerIndicator": false
        },
        "debitCardholderName": {
            "cardholderName": "Doe, John H",
            "additionalEmbossLine": "Home Team",
            "photoId": "EFGH",
            "plasticId": "PM001",
            "rushType": "NONE",
            "orderType": "CARD",
            "nameSuffix": "MD"
        },
        "debitContactInfo": {
            "homePhone": "1005550001",
            "workPhone": "1005550001",
            "cellPhone": "1005550001",
            "alternateContactName": "Doe, John H",
            "textAddress": "0005550000",
            "emailAddress": "jdoe@example.com",
            "dateOfBirth": "1990-08-24",
            "taxIdOrSsn": "XXXXX5678",
            "verificationText": "Driver's license",
            "motherMaidenName": "Smith",
            "activationType": "SOCIAL_SECURITY_NUMBER",
            "activationValue": ""
        },
        "debitAssociatedAccounts": [
            {
                "accountNumber": "987654321",
                "accountType": "CHECKING",
                "accountDescription": "Main account",
                "primaryAccount": "Y",
                "accountStatus": "ACTIVE"
            }
        ]
    }
}
```                        

**Version 1**

**Debit**

**Add Debit Card**

### Using Card Number Provided Masked Card Only Default ###
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/card
```
{
      "cardNumber": "4000100020003000",
      "cardType": "DEBIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "debitOnly": {
          "cardStatus": "ACTIVE",
          "statusReasonCode": "NONE",
          "memberNumber": "0",
          "cardClass": "AAA00",
          "memberSinceDate": "12/09",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "debitPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "debitPriorCardInfo": {
              "priorCardNumber": "4000100020003000",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "debitCardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "PRIMARY",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ],
          "debitCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "rushType": "NONE",
              "orderType": "CARD"
          },
          "debitContactInfo": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactName": "JOHN DOE",
              "textAddress": "0005550000",
              "emailAddress": "jdoe@example.com",
              "dateOfBirth": "2014-10-02",
              "taxIdOrSsn": "987001234",
              "verificationText": "My name is John",
              "motherMaidenName": "Chris Smith",
              "activationType": "MOTHERS_MAIDEN_NAME",
              "activationValue": "Chris Smith"
          },
          "debitAssociatedAccounts": [
              {
                  "accountNumber": "123456789",
                  "accountType": "CHECKING",
                  "accountDescription": "Main account",
                  "primaryAccount": "Y",
                  "accountStatus": "ACTIVE"
              }
          ]
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "card": {
          "cardNumber": "400010XXXXXX3000",
          "memberNumber": "0",
          "expirationDate": "10/23",
          "cardStatus": "ACTIVE",
          "memberSinceDate": "12/09",
          "logo": "APIP",
          "cardClass": "AAA00",
          "statusReasonCode": "NONE",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "cardPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "priorCardInformation": {
              "priorCardNumber": "400010XXXXXX3000",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "cardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "PRIMARY",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ]
      },
      "cardholderName": {
          "cardholderName": "Smith, Alex J",
          "personalizedEmbossingText": "Home Team",
          "photoId": "EFGH",
          "plasticId": "PM001",
          "rushType": "NONE",
          "orderType": "CARD"
      },
      "contactInfo": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "alternateContactName": "JOHN DOE",
          "emailAddress": "jdoe@example.com",
          "dateOfBirth": "2014-10-02",
          "taxIdOrSsn": "XXXXX1234",
          "verificationText": "My name is John",
          "motherMaidenName": "Chris Smith",
          "activationType": "MOTHERS_MAIDEN_NAME",
          "activationValue": "Chris Smith"
      },
      "associatedAccounts": [
          {
              "accountNumber": "123456789",
              "accountType": "CHECKING",
              "accountDescription": "Main account",
              "primaryAccount": "Y",
              "accountStatus": "ACTIVE"
          }
      ]
  }
```
### Not Using Card Number Full Card and Token Reponse
No card number in request, nonTransTokenFlag true, responseFormat FULL_CARD_AND_TOKEN

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/card
```
{
      "cardNumber": "",
      "nonTransTokenFlag": true,
      "responseFormat": "FULL_CARD_AND_TOKEN",
      "cardType": "DEBIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "debitOnly": {
          "cardStatus": "ACTIVE",
          "statusReasonCode": "NONE",
          "memberNumber": "0",
          "cardClass": "AAA00",
          "memberSinceDate": "12/09",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "debitPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "debitPriorCardInfo": {
              "priorNonTransToken": "piUVBJKZGfks4000",
              "priorCardNumber": "",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "debitCardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "PRIMARY",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ],
          "debitCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "rushType": "NONE",
              "orderType": "CARD"
          },
          "debitContactInfo": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactName": "JOHN DOE",
              "textAddress": "0005550000",
              "emailAddress": "jdoe@example.com",
              "dateOfBirth": "2014-10-02",
              "taxIdOrSsn": "987001234",
              "verificationText": "My name is John",
              "motherMaidenName": "Chris Smith",
              "activationType": "MOTHERS_MAIDEN_NAME",
              "activationValue": "Chris Smith"
          },
          "debitAssociatedAccounts": [
              {
                  "accountNumber": "123456789",
                  "accountType": "CHECKING",
                  "accountDescription": "Main account",
                  "primaryAccount": "Y",
                  "accountStatus": "ACTIVE"
              }
          ]
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "card": {
          "cardNumber": "4000100020003000",
          "nonTransToken": "WUPIL5DQTZGM3000",
          "cardType": "DEBIT",
          "logo": "APIP",
          "memberNumber": "0",
          "expirationDate": "10/23",
          "cardStatus": "ACTIVE",
          "memberSinceDate": "12/09",
          "cardClass": "AAA00",
          "statusReasonCode": "NONE",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "cardPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "priorCardInformation": {
              "priorNonTransToken": "piUVBJKZGfks4000",
              "priorCardNumber": "400020XXXXXX4001",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "cardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "PRIMARY",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ]
      },
      "cardholderName": {
          "cardholderName": "Smith, Alex J",
          "personalizedEmbossingText": "Home Team",
          "photoId": "EFGH",
          "plasticId": "PM001",
          "rushType": "NONE",
          "orderType": "CARD"
      },
      "contactInfo": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "alternateContactName": "JOHN DOE",
          "emailAddress": "jdoe@example.com",
          "dateOfBirth": "2014-10-02",
          "taxIdOrSsn": "XXXXX1234",
          "verificationText": "My name is John",
          "motherMaidenName": "Chris Smith",
          "activationType": "MOTHERS_MAIDEN_NAME",
          "activationValue": "Chris Smith"
      },
      "associatedAccounts": [
          {
              "accountNumber": "123456789",
              "accountType": "CHECKING",
              "accountDescription": "Main account",
              "primaryAccount": "Y",
              "accountStatus": "ACTIVE"
          }
      ]
  }
```

### Not Using Card Number and using Masked Card and Token Response
No card number in request, nonTransTokenFlag true, responseFormat MASKED_CARD_AND_TOKEN

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/card
```
{
      "cardNumber": "",
      "nonTransTokenFlag": true,
      "responseFormat": "MASKED_CARD_AND_TOKEN",
      "cardType": "DEBIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "debitOnly": {
          "cardStatus": "ACTIVE",
          "statusReasonCode": "NONE",
          "memberNumber": "0",
          "cardClass": "AAA00",
          "memberSinceDate": "12/09",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "debitPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "debitPriorCardInfo": {
              "priorNonTransToken": "piUVBJKZGfks4000",
              "priorCardNumber": "",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "debitCardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "PRIMARY",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ],
          "debitCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "rushType": "NONE",
              "orderType": "CARD"
          },
          "debitContactInfo": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactName": "JOHN DOE",
              "textAddress": "0005550000",
              "emailAddress": "jdoe@example.com",
              "dateOfBirth": "2014-10-02",
              "taxIdOrSsn": "987001234",
              "verificationText": "My name is John",
              "motherMaidenName": "Chris Smith",
              "activationType": "MOTHERS_MAIDEN_NAME",
              "activationValue": "Chris Smith"
          },
          "debitAssociatedAccounts": [
              {
                  "accountNumber": "123456789",
                  "accountType": "CHECKING",
                  "accountDescription": "Main account",
                  "primaryAccount": "Y",
                  "accountStatus": "ACTIVE"
              }
          ]
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "card": {
          "cardNumber": "400010XXXXXX3000",
          "nonTransToken": "WUPIL5DQTZGM3000",
          "cardType": "DEBIT",
          "logo": "APIP",
          "memberNumber": "0",
          "expirationDate": "10/23",
          "cardStatus": "ACTIVE",
          "memberSinceDate": "12/09",
          "cardClass": "AAA00",
          "statusReasonCode": "NONE",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "cardPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "priorCardInformation": {
              "priorNonTransToken": "piUVBJKZGfks4000",
              "priorCardNumber": "400010XXXXXX3000",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "cardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "PRIMARY",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ]
      },
      "cardholderName": {
          "cardholderName": "Smith, Alex J",
          "personalizedEmbossingText": "Home Team",
          "photoId": "EFGH",
          "plasticId": "PM001",
          "rushType": "NONE",
          "orderType": "CARD"
      },
      "contactInfo": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "alternateContactName": "JOHN DOE",
          "emailAddress": "jdoe@example.com",
          "dateOfBirth": "2014-10-02",
          "taxIdOrSsn": "XXXXX1234",
          "verificationText": "My name is John",
          "motherMaidenName": "Chris Smith",
          "activationType": "MOTHERS_MAIDEN_NAME",
          "activationValue": "Chris Smith"
      },
      "associatedAccounts": [
          {
              "accountNumber": "123456789",
              "accountType": "CHECKING",
              "accountDescription": "Main account",
              "primaryAccount": "Y",
              "accountStatus": "ACTIVE"
          }
      ]
  }
```

### Not Using Card Number, Token Only Response
No card number in request, nonTransTokenFlag true, responseFormat TOKEN_ONLY.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/card
```
{
      "cardNumber": "",
      "nonTransTokenFlag": true,
      "responseFormat": "TOKEN_ONLY",
      "cardType": "DEBIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "debitOnly": {
          "cardStatus": "ACTIVE",
          "statusReasonCode": "NONE",
          "memberNumber": "0",
          "cardClass": "AAA00",
          "memberSinceDate": "12/09",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "debitPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "debitPriorCardInfo": {
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23",
              "priorNonTransToken": "piUVBJKZGfks4000"
          },
          "debitCardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "PRIMARY",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ],
          "debitCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "rushType": "NONE",
              "orderType": "CARD"
          },
          "debitContactInfo": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactName": "JOHN DOE",
              "textAddress": "0005550000",
              "emailAddress": "jdoe@example.com",
              "dateOfBirth": "2014-10-02",
              "taxIdOrSsn": "987001234",
              "verificationText": "My name is John",
              "motherMaidenName": "Chris Smith",
              "activationType": "MOTHERS_MAIDEN_NAME",
              "activationValue": "Chris Smith"
          },
          "debitAssociatedAccounts": [
              {
                  "accountNumber": "123456789",
                  "accountType": "CHECKING",
                  "accountDescription": "Main account",
                  "primaryAccount": "Y",
                  "accountStatus": "ACTIVE"
              }
          ]
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "card": {
          "nonTransToken": "WUPIL5DQTZGM3000",
          "memberNumber": "0",
          "cardType": "DEBIT",
          "logo": "APIP",
          "expirationDate": "10/23",
          "cardStatus": "ACTIVE",
          "memberSinceDate": "12/09",
          "cardClass": "AAA00",
          "statusReasonCode": "NONE",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "cardPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "priorCardInformation": {
              "priorNonTransToken": "piUVBJKZGfks4000",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "cardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "12345",
                  "addressType": "PRIMARY",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ]
      },
      "cardholderName": {
          "cardholderName": "Smith, Alex J",
          "personalizedEmbossingText": "Home Team",
          "photoId": "EFGH",
          "plasticId": "PM001",
          "rushType": "NONE",
          "orderType": "CARD"
      },
      "contactInfo": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "alternateContactName": "JOHN DOE",
          "emailAddress": "jdoe@example.com",
          "dateOfBirth": "2014-10-02",
          "taxIdOrSsn": "XXXXX1234",
          "verificationText": "My name is John",
          "motherMaidenName": "Chris Smith",
          "activationType": "MOTHERS_MAIDEN_NAME",
          "activationValue": "Chris Smith"
      },
      "associatedAccounts": [
          {
              "accountNumber": "123456789",
              "accountType": "CHECKING",
              "accountDescription": "Main account",
              "primaryAccount": "Y",
              "accountStatus": "ACTIVE"
          }
      ]
}
```

### Using Card Class
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v1/cards/template
```
{
      "cardClass": "AAA00",
      "cardType": "DEBIT"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "",
      "cardType": "DEBIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "debitOnly": {
          "cardStatus": "ACTIVE",
          "statusReasonCode": "NONE",
          "memberNumber": "0",
          "oldCardExpirationDate": "10/23",
          "cardClass": "AAA00",
          "memberSinceDate": "12/09",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "debitPINInfo": {
              "pinOffset": "1234",
              "maximumPINTriesAllowed": "4",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "debitPriorCardInfo": {
              "priorCardNumber": "444111XXXXXX7685",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "debitCardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "New Jersey",
                  "zipCode": "12345",
                  "addressType": "PLASTIC",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ],
          "debitCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "rushType": "NONE",
              "orderType": "CARD",
              "nameSuffix": "string"
          },
          "debitContactInfo": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactPhone": "1005550001",
              "textAddress": "1005550001",
              "emailAddress": "alexsmith@example.com",
              "dateOfBirth": "1990-08-24",
              "taxIdOrSsn": "xxxxx5678",
              "verificationText": "string",
              "motherMaidenName": "Smith",
              "activationType": "MOTHERS_MAIDEN_NAME",
              "activationValue": "string"
          },
          "debitAssociatedAccounts": [
              {
                  "accountNumber": "987654321",
                  "accountType": "CHECKING",
                  "accountDescription": "Main Account",
                  "primaryAccount": "Y",
                  "accountStatus": "ACTIVE"
              }
          ]
      }
  }
```
**Templates**

### Using Prior Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v1/cards/template
```
{
      "priorCardNumber": "4000200030004000",
      "cardType": "DEBIT"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "",
      "cardType": "DEBIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "debitOnly": {
          "cardStatus": "ACTIVE",
          "statusReasonCode": "NONE",
          "memberNumber": "0",
          "oldCardExpirationDate": "10/23",
          "cardClass": "AAA00",
          "memberSinceDate": "12/09",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "debitPINInfo": {
              "pinOffset": "1234",
              "maximumPINTriesAllowed": "4",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "debitPriorCardInfo": {
              "priorCardNumber": "444111XXXXXX7685",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "debitCardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "New Jersey",
                  "zipCode": "12345",
                  "addressType": "PLASTIC",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ],
          "debitCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "rushType": "NONE",
              "orderType": "CARD",
              "nameSuffix": "string"
          },
          "debitContactInfo": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactPhone": "1005550001",
              "textAddress": "1005550001",
              "emailAddress": "alexsmith@example.com",
              "dateOfBirth": "1990-08-24",
              "taxIdOrSsn": "xxxxx5678",
              "verificationText": "string",
              "motherMaidenName": "Smith",
              "activationType": "MOTHERS_MAIDEN_NAME",
              "activationValue": "string"
          },
          "debitAssociatedAccounts": [
              {
                  "accountNumber": "987654321",
                  "accountType": "CHECKING",
                  "accountDescription": "Main Account",
                  "primaryAccount": "Y",
                  "accountStatus": "ACTIVE"
              }
          ]
      }
  }
```

### Using Prior NTT
You must remove the nonTransToken field from the response template before using it as an Add Card request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/template
```
{
      "priorNonTransToken": "piUVBJKZGfks4000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "nonTransToken": "",
      "cardNumber": "",
      "cardType": "DEBIT",
      "expirationDate": "11/25",
      "emvCard": "CONTACT",
      "debitOnly": {
          "cardStatus": "ACTIVE",
          "statusReasonCode": "NONE",
          "memberNumber": "0",
          "oldCardExpirationDate": "",
          "cardClass": "AAA00",
          "memberSinceDate": "11/22",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "No",
          "debitPINInfo": {
              "pinOffset": "0000",
              "maximumPINTriesAllowed": "3",
              "pinOffsetChangeDate": "2020-10-02"
          },
          "debitPriorCardInfo": {
              "priorCardNumber": "",
              "priorNonTransToken": "piUVBJKZGfks4000",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "02/25"
          },
          "debitCardholderAddress": [
              {
                  "addressLine1": "650 STREET",
                  "addressLine2": "ALPHA STREET",
                  "city": "NEWYORK",
                  "country": "USA",
                  "state": "NE",
                  "zipCode": "90203",
                  "addressType": "PRIMARY",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": false
              },
              {
                  "addressLine1": "44, SECOND STREET",
                  "addressLine2": "ALPHA STREET",
                  "city": "CHARLOTTE",
                  "country": "USA",
                  "state": "NJ",
                  "zipCode": "90203",
                  "addressType": "ALTERNATE",
                  "cardMailerIndicator": false,
                  "pinMailerIndicator": false
              }
          ],
          "debitCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "photoId": "STRING",
              "rushType": "NONE",
              "orderType": "CARD",
              "nameSuffix": "MR"
          },
          "debitContactInfo": {
              "homePhone": "36256462",
              "workPhone": "23623326",
              "cellPhone": "",
              "alternateContactName": "",
              "textAddress": "test address",
              "emailAddress": "",
              "dateOfBirth": "1990-08-24",
              "taxIdOrSsn": "XXXXX5678",
              "verificationText": "",
              "motherMaidenName": "",
              "activationType": "USER_SELECTED_SECURITY_CODE",
              "activationValue": ""
          },
          "debitAssociatedAccounts": [
              {
                  "accountNumber": "987654321",
                  "accountType": "SAVINGS",
                  "accountDescription": "123456789",
                  "primaryAccount": "Y",
                  "accountStatus": "ACTIVE"
              }
          ]
      }
  }
```

### Using Account Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v1/cards/template
```
{
      "accountNumber": "987654321",
      "cardType": "DEBIT"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "",
      "cardType": "DEBIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "debitOnly": {
          "cardStatus": "ACTIVE",
          "statusReasonCode": "NONE",
          "memberNumber": "0",
          "oldCardExpirationDate": "10/23",
          "cardClass": "AAA00",
          "memberSinceDate": "12/09",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "debitPINInfo": {
              "pinOffset": "1234",
              "maximumPINTriesAllowed": "4",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "debitPriorCardInfo": {
              "priorCardNumber": "444111XXXXXX7685",
              "priorNonTransToken": "YXXhCXvCinTLmA4000",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "debitCardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "New Jersey",
                  "zipCode": "12345",
                  "addressType": "PLASTIC",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ],
          "debitCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "rushType": "NONE",
              "orderType": "CARD",
              "nameSuffix": "string"
          },
          "debitContactInfo": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactPhone": "1005550001",
              "textAddress": "1005550001",
              "emailAddress": "alexsmith@example.com",
              "dateOfBirth": "1990-08-24",
              "taxIdOrSsn": "xxxxx5678",
              "verificationText": "string",
              "motherMaidenName": "Smith",
              "activationType": "MOTHERS_MAIDEN_NAME",
              "activationValue": "string"
          },
          "debitAssociatedAccounts": [
              {
                  "accountNumber": "987654321",
                  "accountType": "CHECKING",
                  "accountDescription": "Main Account",
                  "primaryAccount": "Y",
                  "accountStatus": "ACTIVE"
              }
          ]
      }
  }
```

### Using Card Class
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v1/cards/template
```
{
      "cardClass": "AAA00",
      "cardType": "DEBIT"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "",
      "cardType": "DEBIT",
      "expirationDate": "10/23",
      "emvCard": "CONTACT",
      "debitOnly": {
          "cardStatus": "ACTIVE",
          "statusReasonCode": "NONE",
          "memberNumber": "0",
          "oldCardExpirationDate": "10/23",
          "cardClass": "AAA00",
          "memberSinceDate": "12/09",
          "branch": "0000",
          "reissuePerCardClass": "Yes",
          "updaterServiceOptOut": "Yes",
          "debitPINInfo": {
              "pinOffset": "1234",
              "maximumPINTriesAllowed": "4",
              "pinOffsetChangeDate": "2014-10-02"
          },
          "debitPriorCardInfo": {
              "priorCardNumber": "444111XXXXXX7685",
              "priorMemberNumber": "0",
              "priorCardExpirationDate": "10/23"
          },
          "debitCardholderAddress": [
              {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "New Jersey",
                  "zipCode": "12345",
                  "addressType": "PLASTIC",
                  "cardMailerIndicator": true,
                  "pinMailerIndicator": true
              }
          ],
          "debitCardholderName": {
              "cardholderName": "Smith, Alex J",
              "personalizedEmbossingText": "Home Team",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "rushType": "NONE",
              "orderType": "CARD",
              "nameSuffix": "string"
          },
          "debitContactInfo": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "alternateContactPhone": "1005550001",
              "textAddress": "1005550001",
              "emailAddress": "alexsmith@example.com",
              "dateOfBirth": "1990-08-24",
              "taxIdOrSsn": "xxxxx5678",
              "verificationText": "string",
              "motherMaidenName": "Smith",
              "activationType": "MOTHERS_MAIDEN_NAME",
              "activationValue": "string"
          },
          "debitAssociatedAccounts": [
              {
                  "accountNumber": "987654321",
                  "accountType": "CHECKING",
                  "accountDescription": "Main Account",
                  "primaryAccount": "Y",
                  "accountStatus": "ACTIVE"
              }
          ]
      }
  }
```

**Version 1**

**Debit**

**NTT Generate**
### Using Card Number and Without Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
****HTTP Code:** 201** Created
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
### Using Card Number Full Card and Token Format
**#### Request**
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "FULL_CARD_AND_TOKEN",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 201** Created
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
### Using Card Number Full Card Only Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt
```{
      "cardNumber": "4000200030004000",
      "responseFormat": "FULL_CARD_ONLY",
      "memberNumber": "0"
  }
```
#### Response
****HTTP Code:** 201** Created
```
{
      "cardNumber": "4000200030004000"
  }
```
### Using Card Number Masked Card and Token Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "MASKED_CARD_AND_TOKEN",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 201** Created
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
### Using Card Number Masked Card Only Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "MASKED_CARD_ONLY",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 201 Created
```{
      "cardNumber": "400020XXXXXX4000"
  }
```
### Using Card Number Token Only Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "TOKEN_ONLY",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 201 Created
```
{
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
**Version 1**

**Credit**

**NTT Search**
### Using Card Number Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004001"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001"
}
```
### Using Card Number, Full Card Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004001",
    "responseFormat" : "FULL_CARD_ONLY"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "4000200030004001"
}
```
### Using Card Number, Full Card and Token
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004001",
    "responseFormat" : "FULL_CARD_AND_TOKEN"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "4000200030004001",
    "nonTransToken": "pSAZIXCAXrAo4001"
}
```
### Using Card Number, Masked Card Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004001",
    "responseFormat" : "MASKED_CARD_ONLY"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4001"
}
```
### Using Card Number, Masked Card and Token
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004001",
    "responseFormat" : "MASKED_CARD_AND_TOKEN"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001"
}
```
### Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004001",
    "nonTransToken": "pSAZIXCAXrAo4001"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001"
}
```
### Using NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "nonTransToken": "pSAZIXCAXrAo4001"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001"
}
```
### Using Card Number, Token Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004001",
    "responseFormat" : "TOKEN_ONLY"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "nonTransToken": "pSAZIXCAXrAo4001"
}
```

**Version 1**

**Debit**

**NTT Search**
### Using Card Number Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000"
}
```
### Using Card Number, Full Card Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004000",
    "responseFormat" : "FULL_CARD_ONLY"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "4000200030004000"
}
```
### Using Card Number, Full Card and Token
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004000",
    "responseFormat": "FULL_CARD_AND_TOKEN"
}
```
#### Response
**HTTP Code**: 200 OK
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000"
}
```
### Using Card Number, Masked Card Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004000",
    "responseFormat" : "MASKED_CARD_ONLY"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4000"
}
```
### Using Card Number, Masked Card and Token
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004000",
    "responseFormat": "MASKED_CARD_AND_TOKEN"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000"
}
```
### Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000"
}
```
### Using Card Number, Token Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004000",
    "responseFormat" : "TOKEN_ONLY"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "nonTransToken": "piUVBJKZGfks4000"
}
```
### Using NTT Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "nonTransToken": "piUVBJKZGfks4000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000"
}
```
## Audit
### Retrieve Details of Audit Records
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/audit/details
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "auditLogDateTime": "2021-07-20T08:00:00Z",
      "auditLogAction": "UPDATE",
      "pageLimit": 50,
      "pageOffset": 1
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400010xxxxxx4000",
      "memberNumber": "0",
      "auditRecordDetails": [
          {
              "fieldName": "Account Type",
              "before": "Checking",
              "after": "Savings"
          }
      ]
  }
```
### Retrieve Audit Records for a Card
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/audit/search
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "fromDateTime": "2021-07-20T07:00:00Z",
      "toDateTime": "2021-08-20T07:00:00Z",
      "pageLimit": 50,
      "pageOffset": 1
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400010xxxxxx4000",
      "memberNumber": "0",
      "auditLogSearch": [
          {
              "auditLogDateTime": "2021-07-20T08:00:00Z",
              "auditLogSource": "ATM",
              "auditLogAction": "UPDATE",
              "recordType": "Card Details (DAF)",
              "auditLogId": "Alex"
          }
      ]
```



## Compromised Cards

**Credit and Debit**

### Get Compromised Cards
This API returns a list of compromised cards for both debit and credit. The request has one of the following required parameters; cardnumber, networkalert or fromdate and todate.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/compromised/search
```
{
  "cardNumber": "4000200030004000",
  "networkAlert": "CompCredCard1234",
  "fromDate": "2021-07-20",
  "toDate": "2021-12-28",
  "pageLimit": 50,
  "pageOffset": 1
}
```
##### Response
**HTTP Code:** 200 OK
```
{
"compromisedCards": [
    {
      "cardNumber": "400020XXXXXX4000",
      "clientId": "string",
      "networkAlert": "CompCredCard1234",
      "networkAlertDate": "2021-12-30",
      "severityLevel": "A",
      "compromiseSource": "FALCOMPCARD TEST 1",
      "sourceAlertDescription": "NO ACTION TAKEN"
    }
   ]
  }
```

**Credit**

### Get Details of Compromised Card 
This case returns the details of compromised cards for crdit when a credit card number is submitted.

#### Request
**HTTP Method:** POST
**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/compromised/details/search
```
{
  "cardNumber": "4000200030004000",
  "networkAlert": "CompCard1234"
}
```
##### Response
**HTTP Code:** 200 OK
```
{
  "debitOnly": null,
  "creditOnly": {
    "system": "0000",
    "principal": "0000",
    "agent": "0000",
    "cardStatus": "L–Lost/Stolen",
    "accountStatus": "A–Authorization prohibited",
    "previousAction": "NO ACTION TAKEN",
    "dateLastMaintainance": "2021-07-20",
    "expiryDate": "2025-07-20",
    "cardStatusReasonCode": "88–Fraud",
    "compromisedDate": "2021-07-20",
    "account": "1451550129",
    "transferredAccount": "Yes",
    "transferredCard": "Yes"
  }
}
```
**Debit**

### Get Details of Compromised Card 
This case returns the details of compromised cards for debit when a debit card number is submitted.

#### Request
**HTTP Method:** POST
**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/compromised/details/search
```
{
  "cardNumber": "4000200030004000",
  "networkAlert": "CompCard1234"
}
```
##### Response
**HTTP Code:** 200 OK
```
{
  "debitOnly": {
    "eftRiskAlertNumber": "62800",
    "dateLastMaintainance": "2021-07-20"
  },
  "creditOnly": null
}
```



## Demographics

**Version 4**

**Debit**

**Demographics Search**
### Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v4/cards/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderDemographics": [
          {
              "cardNumber": "400020XXXXXX4000",
              "nonTransToken": "piUVBJKZGfks4000",
              "memberNumber": "0",
              "tcpa": [
                  {
                      "tcpaType": "ENFACT",
                      "mediaType": "VOICE",
                      "revoked": true,
                      "lastUpdatedDateTime": "2022-09-26T15:50:45Z",
                      "lastUpdatedBy": "Jesse Doe"
                  }
              ],
              "contact": {
                  "emailAddress": "alexsmith@example.com",
                  "homePhone": "1005550001",
                  "workPhone": "1005550001",
                  "cellPhone": "1005550001",
                  "textAddress": "1005550001",
                  "enfact": {
                      "languagePreference": "ENGLISH"
                  }
              },
              "preferences": {
                  "homePhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "workPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "cellPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "textAddress": {
                      "enfact": {
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForText": true
                      }
                  },
                  "emailAddress": {
                      "enfact": {
                          "consentForEmail": true
                      },
                      "stepUp": {
                          "consentForEmail": true
                      }
                  }
              },
              "debitCardholderAddress": [
                  {
                      "addressType": "PRIMARY",
                      "addressLine1": "123 Any Street",
                      "addressLine2": "123 Any Lane",
                      "city": "Newark",
                      "stateCode": "NJ",
                      "zipCode": "12345",
                      "countryCode": "USA",
                      "cardMailerIndicator": true,
                      "pinMailerIndicator": true
                  }
              ]
          }
      ]
  }
  ```
### Using Card Number
#### Request
**HTTP Method**: POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v4/cards/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderDemographics": [
          {
              "cardNumber": "400020XXXXXX4000",
              "nonTransToken": "piUVBJKZGfks4000",
              "memberNumber": "0",
              "tcpa": [
                  {
                      "tcpaType": "ENFACT",
                      "mediaType": "VOICE",
                      "revoked": true,
                      "lastUpdatedDateTime": "2022-09-26T15:50:45Z",
                      "lastUpdatedBy": "Jesse Doe"
                  }
              ],
              "contact": {
                  "emailAddress": "alexsmith@example.com",
                  "homePhone": "1005550001",
                  "workPhone": "1005550001",
                  "cellPhone": "1005550001",
                  "textAddress": "1005550001",
                  "enfact": {
                      "languagePreference": "ENGLISH"
                  }
              },
              "preferences": {
                  "homePhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "workPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "cellPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "textAddress": {
                      "enfact": {
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForText": true
                      }
                  },
                  "emailAddress": {
                      "enfact": {
                          "consentForEmail": true
                      },
                      "stepUp": {
                          "consentForEmail": true
                      }
                  }
              },
              "debitCardholderAddress": [
                  {
                      "addressType": "PRIMARY",
                      "addressLine1": "123 Any Street",
                      "addressLine2": "123 Any Lane",
                      "city": "Newark",
                      "stateCode": "NJ",
                      "zipCode": "12345",
                      "countryCode": "USA",
                      "cardMailerIndicator": true,
                      "pinMailerIndicator": true
                  }
              ]
          }
      ]
  }
```
### Using NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v4/cards/cardholders/demographics/search
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderDemographics": [
          {
              "cardNumber": "400020XXXXXX4000",
              "nonTransToken": "piUVBJKZGfks4000",
              "memberNumber": "0",
              "tcpa": [
                  {
                      "tcpaType": "ENFACT",
                      "mediaType": "VOICE",
                      "revoked": true,
                      "lastUpdatedDateTime": "2022-09-26T15:50:45Z",
                      "lastUpdatedBy": "Jesse Doe"
                  }
              ],
              "contact": {
                  "emailAddress": "alexsmith@example.com",
                  "homePhone": "1005550001",
                  "workPhone": "1005550001",
                  "cellPhone": "1005550001",
                  "textAddress": "1005550001",
                  "enfact": {
                      "languagePreference": "ENGLISH"
                  }
              },
              "preferences": {
                  "homePhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "workPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "cellPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "textAddress": {
                      "enfact": {
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForText": true
                      }
                  },
                  "emailAddress": {
                      "enfact": {
                          "consentForEmail": true
                      },
                      "stepUp": {
                          "consentForEmail": true
                      }
                  }
              },
              "debitCardholderAddress": [
                  {
                      "addressType": "PRIMARY",
                      "addressLine1": "123 Any Street",
                      "addressLine2": "123 Any Lane",
                      "city": "Newark",
                      "stateCode": "NJ",
                      "zipCode": "12345",
                      "countryCode": "USA",
                      "cardMailerIndicator": true,
                      "pinMailerIndicator": true
                  }
              ]
          }
      ]
  }
```
**Version 2**

**Credit**
### Search
This case is a Demographics search.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004001",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderDemographics": [
          {
              "cardNumber": "400020XXXXXX4001",
              "memberNumber": "0",
              "tcpa": [
                  {
                      "tcpaType": "ENFACT",
                      "mediaType": "VOICE",
                      "revoked": true,
                      "lastUpdatedDateTime": "2022-09-26 15:50:45",
                      "lastUpdatedBy": "Jesse Doe"
                  }
              ],
              "contact": {
                  "emailAddress": "jessedoe@example.com",
                  "homePhone": "1005550001",
                  "workPhone": "1005550001",
                  "cellPhone": "1005550001",
                  "textAddress": "1005550001",
                  "enfact": {
                      "languagePreference": "ENGLISH"
                  }
              },
              "preferences": {
                  "homePhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "workPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "cellPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "textAddress": {
                      "enfact": {
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForText": true
                      }
                  },
                  "emailAddress": {
                      "enfact": {
                          "consentForEmail": true
                      },
                      "stepUp": {
                          "consentForEmail": true
                      }
                  }
              },
              "credittAdditionalInfo": {
                  "accountNumber": "123456789",
                  "externalCustomerId": "xxxxx6789",
                  "prefix": "DR",
                  "cardholderName": "Doe, John H",
                  "association": "PRIMARY",
                  "vip": true,
                  "gender": "NOT_SPECIFIED",
                  "dateOfBirth": "1990-08-24",
                  "employeeCode": true,
                  "motherMaidenName": "Smith",
                  "empId": "123005678",
                  "taxIdOrSsn": "xxxxx5678",
                  "ein": "xxxxx5678",
                  "dnaPersonId": "123005678",
                  "isDeceased": false,
                  "memoLine1": "This is an example added to a cardholder record.",
                  "memoLine2": "Customer requested name change, updating contact information on account.",
                  "employerName": "Fiserv",
                  "personalizedEmbossingText": "Jesse Doe",
                  "duplicateStatementsSecondary": false,
                  "duplicateLettersSecondary": false,
                  "specialHandling": "NONE"
              },
              "creditCardholderAddress": [
                  {
                      "addressType": "BILLING",
                      "addressLine1": "123 Any Street",
                      "addressLine2": "123 Any Lane",
                      "addressLine3": "123 Any Lane",
                      "addressLine4": "123 Any Lane",
                      "city": "Newark",
                      "stateCode": "NJ",
                      "zipCode": "12345",
                      "country": "USA",
                      "categoryCode": "PERMANENT",
                      "beginDate": "2021-08-03",
                      "endDate": "2021-08-03"
                  }
              ]
          }
      ]
  }
```
### Partial
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v3/cards/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004003",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 206 Partial Success #### Response
```
{
      "traceId": null,
      "spanId": null,
      "instance": "/api/cardholders/v4/demographics/search",
      "code": null,
      "moreDetails": null,
      "type": "Partial Content For Credit",
      "title": "PartialSuccess",
      "message": "#### Response is partially success for Credit Card.",
      "timestamp": "2022-11-24T20:06:24.553771"
  }
```
## Update
### Cardholder Contact Information Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/contact
```
{
      "cardNumber": "4000200030004001",
      "tcpa": [
          {
              "tcpaType": "ENFACT",
              "mediaType": "VOICE",
              "revoked": true
          }
      ],
      "contact": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "textAddress": "1005550001",
          "enfact": {
              "languagePreference": "ENGLISH"
          }
      },
      "preferences": {
          "homePhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "workPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "cellPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "textAddress": {
              "enfact": {
                  "consentForText": true
              },
              "stepUp": {
                  "consentForText": true
              }
          },
          "emailAddress": {
              "enfact": {
                  "consentForEmail": true
              },
              "stepUp": {
                  "consentForEmail": true
              }
          }
      }
  }
```
#### Response
**HTTP Code:** 204 No Content



### Cardholder Address Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v3/cardholders/address
```
{
      "cardNumber": "4000200030004001",
      "creditCardholderAddress": [
          {
              "addressType": "PLASTIC",
              "addressLine1": "123 Any Street",
              "addressLine2": "123 Any Lane",
              "addressLine3": "123 Any Lane",
              "addressLine4": "123 Any Lane",
              "city": "Newark",
              "countryCode": "USA",
              "stateCode": "NJ",
              "zipCode": "12345",
              "isValidAddress": "Yes",
              "beginDate": "2023-03-01",
              "endDate": "2023-03-31",
              "categoryCode": "TEMPORARY"
          }
      ]
  }
```
#### Response
**HTTP Code:** 204 No Content


**Version 3**

**Debit**

**Demographics Search**
### Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderDemographics": [
          {
              "cardNumber": "400020XXXXXX4000",
              "nonTransToken": "piUVBJKZGfks4000",
              "memberNumber": "0",
              "tcpa": [
                  {
                      "tcpaType": "ENFACT",
                      "mediaType": "VOICE",
                      "revoked": true,
                      "lastUpdatedDateTime": "2022-09-26 15:50:45",
                      "lastUpdatedBy": "Jesse Doe"
                  }
              ],
              "contact": {
                  "emailAddress": "jessedoe@example.com",
                  "homePhone": "1005550001",
                  "workPhone": "1005550001",
                  "cellPhone": "1005550001",
                  "textAddress": "1005550001",
                  "enfact": {
                      "languagePreference": "ENGLISH"
                  }
              },
              "preferences": {
                  "homePhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "workPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "cellPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "textAddress": {
                      "enfact": {
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForText": true
                      }
                  },
                  "emailAddress": {
                      "enfact": {
                          "consentForEmail": true
                      },
                      "stepUp": {
                          "consentForEmail": true
                      }
                  }
              },
              "debitAdditionalInfo": {
                  "accountNumber": "123456789",
                  "dateOfBirth": "1990-08-24",
                  "motherMaidenName": "Smith",
                  "taxIdOrSsn": "XXXXX5678",
                  "verificationText": "Driver's license",
                  "callerId": "1005550001",
                  "updateNameDetails": [
                      {
                          "cardholderName": "Doe, John H",
                          "priorCardholderName": "Doe, Jessie H",
                          "nameSuffix": "MD",
                          "additionalEmbossLine": "Jesse Doe",
                          "photoId": "EFGH",
                          "plasticId": "PM001"
                      }
                  ]
              },
              "debitCardholderAddress": [
                  {
                      "addressType": "PRIMARY",
                      "addressLine1": "123 Any Street",
                      "addressLine2": "123 Any Lane",
                      "city": "Newark",
                      "stateCode": "NJ",
                      "zipCode": "12345",
                      "country": "USA",
                      "cardMailerIndicator": true,
                      "pinMailerIndicator": true
                  }
              ],
              "atmPreferences": [
                  {
                      "languageCode": "ENGLISH",
                      "amount": 240,
                      "accountType": "CHECKING",
                      "receiptOption": "ASK_ME",
                      "terminalOwnerId": "USER01",
                      "sourceType": "A",
                      "action": "ADD",
                      "actionDateTime": {},
                      "updatedBy": "USER01"
                  }
              ]
          }
      ]
  }
```
### Using NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/demographics/search
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderDemographics": [
          {
              "cardNumber": "400020XXXXXX4000",
              "nonTransToken": "piUVBJKZGfks4000",
              "memberNumber": "0",
              "tcpa": [
                  {
                      "tcpaType": "ENFACT",
                      "mediaType": "VOICE",
                      "revoked": true,
                      "lastUpdatedDateTime": "2022-09-26 15:50:45",
                      "lastUpdatedBy": "Jesse Doe"
                  }
              ],
              "contact": {
                  "emailAddress": "jessedoe@example.com",
                  "homePhone": "1005550001",
                  "workPhone": "1005550001",
                  "cellPhone": "1005550001",
                  "textAddress": "1005550001",
                  "enfact": {
                      "languagePreference": "ENGLISH"
                  }
              },
              "preferences": {
                  "homePhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "workPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "cellPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "textAddress": {
                      "enfact": {
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForText": true
                      }
                  },
                  "emailAddress": {
                      "enfact": {
                          "consentForEmail": true
                      },
                      "stepUp": {
                          "consentForEmail": true
                      }
                  }
              },
              "debitAdditionalInfo": {
                  "accountNumber": "123456789",
                  "dateOfBirth": "1990-08-24",
                  "motherMaidenName": "Smith",
                  "taxIdOrSsn": "XXXXX5678",
                  "verificationText": "Driver's license",
                  "callerId": "1005550001",
                  "updateNameDetails": [
                      {
                          "cardholderName": "Doe, John H",
                          "priorCardholderName": "Doe, Jessie H",
                          "nameSuffix": "MD",
                          "additionalEmbossLine": "Jesse Doe",
                          "photoId": "EFGH",
                          "plasticId": "PM001"
                      }
                  ]
              },
              "debitCardholderAddress": [
                  {
                      "addressType": "PRIMARY",
                      "addressLine1": "123 Any Street",
                      "addressLine2": "123 Any Lane",
                      "city": "Newark",
                      "stateCode": "NJ",
                      "zipCode": "12345",
                      "country": "USA",
                      "cardMailerIndicator": true,
                      "pinMailerIndicator": true
                  }
              ],
              "atmPreferences": [
                  {
                      "languageCode": "ENGLISH",
                      "amount": 240,
                      "accountType": "CHECKING",
                      "receiptOption": "ASK_ME",
                      "terminalOwnerId": "USER01",
                      "sourceType": "A",
                      "action": "ADD",
                      "actionDateTime": {},
                      "updatedBy": "USER01"
                  }
              ]
          }
      ]
  }
```
### Using Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/demographics/search
```{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderDemographics": [
          {
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "tcpa": [
                  {
                      "tcpaType": "ENFACT",
                      "mediaType": "VOICE",
                      "revoked": true,
                      "lastUpdatedDateTime": "2022-09-26 15:50:45",
                      "lastUpdatedBy": "Jesse Doe"
                  }
              ],
              "contact": {
                  "emailAddress": "jessedoe@example.com",
                  "homePhone": "1005550001",
                  "workPhone": "1005550001",
                  "cellPhone": "1005550001",
                  "textAddress": "1005550001",
                  "enfact": {
                      "languagePreference": "ENGLISH"
                  }
              },
              "preferences": {
                  "homePhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "workPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "cellPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "textAddress": {
                      "enfact": {
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForText": true
                      }
                  },
                  "emailAddress": {
                      "enfact": {
                          "consentForEmail": true
                      },
                      "stepUp": {
                          "consentForEmail": true
                      }
                  }
              },
              "debitAdditionalInfo": {
                  "accountNumber": "123456789",
                  "dateOfBirth": "1990-08-24",
                  "motherMaidenName": "Smith",
                  "taxIdOrSsn": "XXXXX5678",
                  "verificationText": "Driver's license",
                  "callerId": "1005550001",
                  "updateNameDetails": [
                      {
                          "cardholderName": "Doe, John H",
                          "priorCardholderName": "Doe, Jessie H",
                          "nameSuffix": "MD",
                          "additionalEmbossLine": "Jesse Doe",
                          "photoId": "EFGH",
                          "plasticId": "PM001"
                      }
                  ]
              },
              "debitCardholderAddress": [
                  {
                      "addressType": "PRIMARY",
                      "addressLine1": "123 Any Street",
                      "addressLine2": "123 Any Lane",
                      "city": "Newark",
                      "stateCode": "NJ",
                      "zipCode": "12345",
                      "country": "USA",
                      "cardMailerIndicator": true,
                      "pinMailerIndicator": true
                  }
              ],
              "atmPreferences": [
                  {
                      "languageCode": "ENGLISH",
                      "amount": 240,
                      "accountType": "CHECKING",
                      "receiptOption": "ASK_ME",
                      "terminalOwnerId": "USER01",
                      "sourceType": "A",
                      "action": "ADD",
                      "actionDateTime": {},
                      "updatedBy": "USER01"
                  }
              ]
          }
      ]
  }
```
### Using Card Number for Partial
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v3/cards/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004002",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 206 Partial Success #### Response
```
{
      "traceId": null,
      "spanId": null,
      "instance": "/api/cardholders/v4/demographics/search",
      "code": null,
      "moreDetails": null,
      "type": "Partial Content For Debit",
      "title": "PartialSuccess",
      "message": "#### Response is partially success for Debit Card.",
      "timestamp": "2022-11-24T20:06:24.553771"
  }
  ```

## Update
### Cardholder Contact Information Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/contact
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "tcpa": [
          {
              "tcpaType": "ENFACT",
              "mediaType": "VOICE",
              "revoked": true
          }
      ],
      "contact": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "textAddress": "1005550001",
          "enfact": {
              "languagePreference": "ENGLISH"
          }
      },
      "preferences": {
          "homePhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "workPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "cellPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "textAddress": {
              "enfact": {
                  "consentForText": true
              },
              "stepUp": {
                  "consentForText": true
              }
          },
          "emailAddress": {
              "enfact": {
                  "consentForEmail": true
              },
              "stepUp": {
                  "consentForEmail": true
              }
          }
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

### Cardholder Contact Information Using NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/contact
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "tcpa": [
          {
              "tcpaType": "ENFACT",
              "mediaType": "VOICE",
              "revoked": true
          }
      ],
      "contact": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "textAddress": "1005550001",
          "enfact": {
              "languagePreference": "ENGLISH"
          }
      },
      "preferences": {
          "homePhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "workPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "cellPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "textAddress": {
              "enfact": {
                  "consentForText": true
              },
              "stepUp": {
                  "consentForText": true
              }
          },
          "emailAddress": {
              "enfact": {
                  "consentForEmail": true
              },
              "stepUp": {
                  "consentForEmail": true
              }
          }
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

### Cardholder Contact Information Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/contact
```
{
      "cardNumber": "4000200030004000",
      "tcpa": [
          {
              "tcpaType": "ENFACT",
              "mediaType": "VOICE",
              "revoked": true
          }
      ],
      "contact": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "textAddress": "1005550001",
          "enfact": {
              "languagePreference": "ENGLISH"
          }
      },
      "preferences": {
          "homePhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "workPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "cellPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "textAddress": {
              "enfact": {
                  "consentForText": true
              },
              "stepUp": {
                  "consentForText": true
              }
          },
          "emailAddress": {
              "enfact": {
                  "consentForEmail": true
              },
              "stepUp": {
                  "consentForEmail": true
              }
          }
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

### Cardholder Contact Information with Card Number and NTT as Empty
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/contact
```
{
      "cardNumber": "",
      "nonTransToken": "",
      "tcpa": [
          {
              "tcpaType": "ENFACT",
              "mediaType": "VOICE",
              "revoked": true
          }
      ],
      "contact": {
          "homePhone": "1005550001",
          "workPhone": "1005550001",
          "cellPhone": "1005550001",
          "textAddress": "1005550001",
          "enfact": {
              "languagePreference": "ENGLISH"
          }
      },
      "preferences": {
          "homePhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "workPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "cellPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "textAddress": {
              "enfact": {
                  "consentForText": true
              },
              "stepUp": {
                  "consentForText": true
              }
          },
          "emailAddress": {
              "enfact": {
                  "consentForEmail": true
              },
              "stepUp": {
                  "consentForEmail": true
              }
          }
      }
  }
```
#### Response
**HTTP Code:** 400 Invalid #### Request
```
{
      "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
      "title": "Invalid #### Request",
      "instance": "/cs/cards/v3/cardholders/contact",
      "status": 400,
      "detail": "Either cardNumber or nontranstoken should be included."
  }
  ```
### Cardholder Address with Card Number NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v3/cardholders/address
```{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "debitCardholderAddress": [
          {
              "addressType": "PRIMARY",
              "addressLine1": "123 Any Street",
              "addressLine2": "123 Any Lane",
              "city": "Newark",
              "countryCode": "USA",
              "stateCode": "NJ",
              "zipCode": "12345",
              "cardMailerIndicator": true,
              "pinMailerIndicator": false
          }
      ]
  }
```
#### Response
**HTTP Code:** 204 No Content

### Cardholder Address with Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v3/cardholders/address
```
{
      "cardNumber": "4000200030004000",
      "debitCardholderAddress": [
          {
              "addressType": "PRIMARY",
              "addressLine1": "123 Any Street",
              "addressLine2": "123 Any Lane",
              "city": "Newark",
              "countryCode": "USA",
              "stateCode": "NJ",
              "zipCode": "12345",
              "cardMailerIndicator": true,
              "pinMailerIndicator": false
          }
      ]
  }
```
#### Response
**HTTP Code:** 204 No Content

### Cardholder Address with NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v3/cardholders/address
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "debitCardholderAddress": [
          {
              "addressType": "PRIMARY",
              "addressLine1": "123 Any Street",
              "addressLine2": "123 Any Lane",
              "city": "Newark",
              "countryCode": "USA",
              "stateCode": "NJ",
              "zipCode": "12345",
              "cardMailerIndicator": true,
              "pinMailerIndicator": false
          }
      ]
  }
```
#### Response
**HTTP Code:** 204 No Content

**Version 1**

**Credit**

**Update**
### Cardholder Additional Information Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/additionalInfo
```
{
      "cardNumber": "4000200030004001",
      "creditAdditionalInfo": {
          "prefix": "DR.",
          "cardholderName": "Doe, John H",
          "association": "PRIMARY",
          "vip": true,
          "gender": "MALE",
          "dateOfBirth": "1990-08-24",
          "employeeCode": true,
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "123005678",
          "ein": "123005678",
          "dnaPersonId": "123005678",
          "isDeceased": false,
          "memoLine1": "This customer is hard of hearing.",
          "memoLine2": "Customer called wife is deceased sending information to remove wife from account.",
          "employerName": "Fiserv",
          "personalizedEmbossingText": "Home Team",
          "duplicateStatementsSecondary": false,
          "duplicateLettersSecondary": false,
          "specialHandling": "NONE"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

### Cardholder Address Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/address
```
{
      "cardNumber": "4000200030004001",
      "creditCardholderAddress": [
          {
              "addressType": "PLASTIC",
              "addressLine1": "123 Any Street",
              "addressLine2": "123 Any Lane",
              "addressLine3": "123 Any Lane",
              "addressLine4": "123 Any Lane",
              "city": "Newark",
              "country": "USA",
              "stateCode": "NJ",
              "zipCode": "12345",
              "isValidAddress": "Yes",
              "beginDate": "2023-03-01",
              "endDate": "2023-03-31",
              "categoryCode": "TEMPORARY"
          }
      ]
  }
```
#### Response
**HTTP Code:** 204 No Content


**Version 2**

**Debit**

**Demographics Search**
## Search
### Search cardholder demographics.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderDemographics": [
          {
              "cardNumber": "400020XXXXXX4000",
              "accountNumber": "XXXXX6789",
              "externalCustomerId": "XXXXX6789",
              "additionalInfo": {
                  "prefix": "Dr.",
                  "cardholderName": "John Smith",
                  "association": "PRIMARY",
                  "vip": true,
                  "gender": "NOT_SPECIFIED",
                  "dateOfBirth": "2014-10-02",
                  "employeeCode": false,
                  "motherMaidenName": "Smith",
                  "empId": "XXXXX5678",
                  "ssnOrTaxid": "XXXXX5678",
                  "ein": "XXXXX5678",
                  "dnaPersonId": "123005678",
                  "isDeceased": true,
                  "memoLine1": "This customer is hard of hearing.",
                  "memoLine2": "Customer called wife is deceased sending information to remove wife from account.",
                  "verificationText": "Driver's license",
                  "verificationZipCode": "12345",
                  "callerId": "000-555-0000",
                  "employerName": "Fiserv",
                  "personalizedEmbossingText": "Jesse Doe",
                  "duplicateStatementsSecondary": true,
                  "duplicateLettersSecondary": true,
                  "specialHandling": "NONE",
                  "nameDetails": [
                      {
                          "nameSuffix": "Sr.",
                          "priorCardholderName": "Jessie Doe",
                          "photoId": "EFGH",
                          "plasticId": "PM001"
                      }
                  ]
              },
              "address": [
                  {
                      "addressType": "PRIMARY",
                      "addressLine1": "123 Any Street",
                      "addressLine2": "123 Any Lane",
                      "addressLine3": "123 Any Lane",
                      "addressLine4": "123 Any Lane",
                      "city": "New Jersey",
                      "stateCode": "NJ",
                      "zipCode": "12345",
                      "countryCode": "USA",
                      "isCardMailer": true,
                      "isPinMailer": true,
                      "addressCategoryCode": "PERMANENT",
                      "beginDate": {},
                      "endDate": {}
                  }
              ],
              "tcpa": [
                  {
                      "tcpaType": "ENFACT",
                      "mediaType": "VOICE",
                      "revoked": true,
                      "lastUpdatedDateTime": "2022-09-26T15:50:45Z",
                      "lastUpdatedBy": "Jesse Doe"
                  }
              ],
              "contact": {
                  "voice": {
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "cellPhone": "1005550001"
                  },
                  "email": {
                      "emailAddress": "jessedoe@example.com"
                  },
                  "text": {
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "cellPhone": "1005550001",
                      "textAddress": "1005550001"
                  },
                  "enfact": {
                      "languagePreference": "ENGLISH"
                  }
              },
              "preferences": {
                  "homePhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "workPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "cellPhone": {
                      "enfact": {
                          "consentForVoice": true,
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForVoice": true,
                          "consentForText": true
                      }
                  },
                  "textAddress": {
                      "enfact": {
                          "consentForText": true
                      },
                      "stepUp": {
                          "consentForText": true
                      }
                  },
                  "emailAddress": {
                      "enfact": {
                          "consentForEmail": true
                      },
                      "stepUp": {
                          "consentForEmail": true
                      }
                  }
              },
              "atmPreferences": [
                  {
                      "preferredLanguageCode": "NONE",
                      "preferredAmount": 240,
                      "preferredAccount": "NONE",
                      "preferredReceiptOption": "NONE",
                      "terminalOwnerId": "USER01",
                      "sourceType": "A",
                      "action": "ADD",
                      "actionDateTime": "2014-10-02T15:01:23.045Z",
                      "updatedBy": "USER01"
                  }
              ]
          }
      ]
  }
```
## Update
### ATM Preferences Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/atmPreferences
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "atmPreferences": {
          "languageCode": "ENGLISH",
          "amount": 240,
          "accountType": "SAVINGS",
          "receiptOption": "ASK_ME"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

### ATM Preferences Using NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/atmPreferences
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "atmPreferences": {
          "languageCode": "ENGLISH",
          "amount": 240,
          "accountType": "SAVINGS",
          "receiptOption": "ASK_ME"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### 
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/atmPreferences
```
{
      "cardNumber": "4000200030004000",
      "atmPreferences": {
          "languageCode": "ENGLISH",
          "amount": 240,
          "accountType": "SAVINGS",
          "receiptOption": "ASK_ME"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### Cardholder Additional Information Using Nons Trans Token
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/additionalInfo
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "debitAdditionalInfo": {
          "memberNumber": "0",
          "dateOfBirth": "1990-08-24",
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "123005678",
          "verificationText": "My name is John",
          "callerId": "1005550001",
          "updateNameDetails": [
              {
                  "cardholderName": "Doe, John H",
                  "priorCardholderName": "Doe, Alex M",
                  "nameSuffix": "MD",
                  "additionalEmbossLine": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001"
              }
          ]
      }
  }
```
#### Response
**HTTP Code**: 204 No Content
### Cardholder Additional Information Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/additionalInfo
```
{
      "cardNumber": "4000200030004000",
      "debitAdditionalInfo": {
          "memberNumber": "0",
          "dateOfBirth": "1990-08-24",
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "123005678",
          "verificationText": "My name is John",
          "callerId": "1005550001",
          "updateNameDetails": [
              {
                  "cardholderName": "Doe, John H",
                  "priorCardholderName": "Doe, Alex M",
                  "nameSuffix": "MD",
                  "additionalEmbossLine": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001"
              }
          ]
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### Cardholder Additional Information with Negative Scenario
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/additionalInfo
```
{
      "debitAdditionalInfo": {
          "memberNumber": "0",
          "dateOfBirth": "1990-08-24",
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "123005678",
          "verificationText": "My name is John",
          "callerId": "1005550001",
          "updateNameDetails": [
              {
                  "cardholderName": "Doe, John H",
                  "priorCardholderName": "Doe, Alex M",
                  "nameSuffix": "MD",
                  "additionalEmbossLine": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001"
              }
          ]
      }
  }
```
#### Response
**HTTP Code:** 400 Invalid #### Request
```
{
      "traceId": "e6fe7d9fcf1d6c92",
      "spanId": "dd7f2b9cb13b46a8",
      "type": "Input Validation Exception",
      "title": "Bad #### Request",
      "message": "Please enter either cardNumber or nonTransToken.",
      "instance": "/api/v2/cardholders/additionalInfo",
      "timestamp": "2022-05-06T14:29:42.173912",
      "code": "400-121-108",
      "moreDetails": [
          {
              "code": "121-108",
              "detail": "Please enter either cardNumber or nonTransToken."
          }
      ]
  }
```
### Cardholder Address Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/address
```

      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "debitCardholderAddress": [
          {
              "addressType": "PRIMARY",
              "addressLine1": "123 Any Street",
              "addressLine2": "123 Any Lane",
              "city": "Newark",
              "country": "USA",
              "stateCode": "NJ",
              "zipCode": "12345",
              "cardMailerIndicator": true,
              "pinMailerIndicator": false
          }
      ]
  }
```
#### Response
**HTTP Code:** 204 No Content
### Cardholder Address with Card Number and NTT as Empty
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v2/cardholders/address
```

      "cardNumber": "",
      "nonTransToken": "",
      "debitCardholderAddress": [
          {
              "addressType": "PRIMARY",
              "addressLine1": "123 Any Street",
              "addressLine2": "123 Any Lane",
              "city": "Newark",
              "country": "USA",
              "stateCode": "NJ",
              "zipCode": "12345",
              "cardMailerIndicator": true,
              "pinMailerIndicator": false
          }
      ]
  }
```
#### Response
**HTTP Code:** 400 Invalid #### Request
```
{
      "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
      "title": "Invalid #### Request",
      "instance": "/cs/cards/v2/cardholders/address",
      "status": 400,
      "detail": "Either cardNumber or nonTransToken should be included."
  }
```
### Cardholder Address Using NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/address
```

      "nonTransToken": "piUVBJKZGfks4000",
      "debitCardholderAddress": [
          {
              "addressType": "PRIMARY",
              "addressLine1": "123 Any Street",
              "addressLine2": "123 Any Lane",
              "city": "Newark",
              "country": "USA",
              "stateCode": "NJ",
              "zipCode": "12345",
              "cardMailerIndicator": true,
              "pinMailerIndicator": false
          }
      ]
  }
```
#### Response
**HTTP Code:** 204 No Content

### Cardholder Address Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/address
```{
      "cardNumber": "4000200030004000",
      "debitCardholderAddress": [
          {
              "addressType": "PRIMARY",
              "addressLine1": "123 Any Street",
              "addressLine2": "123 Any Lane",
              "city": "Newark",
              "country": "USA",
              "stateCode": "NJ",
              "zipCode": "12345",
              "cardMailerIndicator": true,
              "pinMailerIndicator": false
          }
      ]
  }
```
#### Response
**HTTP Code:** 204 No Content

### Cardholder Contact Information Using Card Number
This updates the cardholder contact information.

#### Request
H**TTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/contact
```
{
      "cardNumber": "4000200030004000",
      "tcpa": [
          {
              "tcpaType": "ENFACT",
              "mediaType": "VOICE",
              "revoked": true
          }
      ],
      "contact": {
          "voice": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001"
          },
          "email": {
              "emailAddress": "jessedoe@example.com"
          },
          "text": {
              "homePhone": "1005550001",
              "workPhone": "1005550001",
              "cellPhone": "1005550001",
              "textAddress": "1005550001"
          },
          "enfact": {
              "languagePreference": "ENGLISH"
          }
      },
      "preferences": {
          "homePhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "workPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "cellPhone": {
              "enfact": {
                  "consentForVoice": true,
                  "consentForText": true
              },
              "stepUp": {
                  "consentForVoice": true,
                  "consentForText": true
              }
          },
          "textAddress": {
              "enfact": {
                  "consentForText": true
              },
              "stepUp": {
                  "consentForText": true
              }
          },
          "emailAddress": {
              "enfact": {
                  "consentForEmail": true
              },
              "stepUp": {
                  "consentForEmail": true
              }
          }
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

**Version 1**

**Debit**

**Search**
### Demographics Search
Search cardholder demographics.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004000"
  }
```
#### Response
**HTTP Code:** 200 OK
```{
      "cardholderDemographics": {
          "cardNumber": "4000200xxxxxx4000",
          "accountNumber": "xxxxx6789",
          "externalCustomerId": "xxxxx6789",
          "additionalInfo": {
              "prefix": "Dr.",
              "cardholderName": "John Smith",
              "association": "PRIMARY",
              "vip": true,
              "gender": "NOT_SPECIFIED",
              "dateOfBirth": "2014-10-02",
              "employeeCode": "123-00-5678",
              "motherMaidenName": "Smith",
              "empId": "123-000-5678",
              "ssnOrTaxId": "123-00-5678",
              "ein": "123-00-5678",
              "dnaPersonId": "123-00-5678",
              "isDeceased": true,
              "memoLine1": "This customer is hard of hearing.",
              "memoLine2": "Customer called wife is deceased.",
              "verificationText": "Please request to speak to Sr. not Jr.",
              "employerName": "Fiserv",
              "personalizedEmbossingText": "Jesse Doe",
              "duplicateStatementsSecondary": true,
              "duplicateLettersSecondary": true,
              "specialHandling": "NONE"
          },
          "address": [
              {
                  "addressType": "PRIMARY",
                  "addressLine1": "123 Any Street",
                  "addressLine2": "123 Any Lane",
                  "addressLine3": "123 Any Lane",
                  "addressLine4": "123 Any Lane",
                  "city": "New Jersey",
                  "stateCode": "NJ",
                  "zipCode": "12345",
                  "countryCode": "USA",
                  "isCardMailer": true,
                  "isPinMailer": true,
                  "addressCategoryCode": "PERMANENT",
                  "beginDate": "2014-10-02",
                  "endDate": "2014-10-02"
              }
          ],
          "tcpa": [
              {
                  "tcpaType": "ENFACT",
                  "consentForVoice": true,
                  "consentForText": true,
                  "lastUpdatedDate": "2020-01-01",
                  "lastUpdatedBy": "Jesse Doe"
              }
          ],
          "contact": {
              "voice": {
                  "homePhoneNumber": "000-555-0000",
                  "workPhoneNumber": "000-555-0000",
                  "mobilePhoneNumber": "000-555-0000",
                  "textAddress": "000-555-0000"
              },
              "email": {
                  "emailAddress": "jessedoe@example.com"
              },
              "text": {
                  "homePhoneNumber": "000-555-0000",
                  "workPhoneNumber": "000-555-0000",
                  "mobilePhoneNumber": "000-555-0000",
                  "textAddress": "000-555-0000"
              },
              "enfact": {
                  "enfactLanguagePreference": "ENGLISH"
              },
              "enfactVoice": {
                  "homePhone": true,
                  "workPhone": true,
                  "mobilePhone": true,
                  "emailAddress": true,
                  "textAddress": true
              },
              "enfactText": {
                  "homePhone": true,
                  "workPhone": true,
                  "mobilePhone": true,
                  "emailAddress": true,
                  "address": true,
                  "mobileText": true
              },
              "stepUpText": {
                  "homePhone": true,
                  "workPhone": true,
                  "mobilePhone": true,
                  "emailAddress": true,
                  "address": true,
                  "mobileText": true
              },
              "stepUpVoice": {
                  "homePhone": true,
                  "workPhone": true,
                  "mobilePhone": true,
                  "emailAddress": true,
                  "address": true,
                  "mobileText": true
              }
          }
      }
  }
```
## Update
### Update ATM Preferences
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/atmPreferences
```
{
      "cardNumber": "4000200030004000",
      "atmPreferences": {
          "preferredLanguageCode": "ENGLISH",
          "preferredAmount": 240,
          "preferredAccount": "CHECKING",
          "preferredReceiptOption": "ALWAYS"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### Update Cardholder Additional Information
This updates the cardholder additional information.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/additionalInfo
```{
      "cardNumber": "4000200030004000",
      "additionalInfo": {
          "prefix": "Dr.",
          "cardholderName": "John Doe",
          "association": "AUTHORIZED_USER",
          "vip": true,
          "gender": "NOT_SPECIFIED",
          "dateOfBirth": "1991-10-02",
          "employeeCode": true,
          "empId": "1234_FS",
          "ssnOrTaxid": "123005678",
          "ein": "123033056",
          "dnaPersonId": "123456789",
          "isDeceased": false,
          "memoLine1": "Memo line 1",
          "memoLine2": "Memo line 2",
          "employerName": "Fiserv",
          "motherMaidenName": "Smith",
          "verificationText": "Driver's license",
          "personalizedEmbossingText": "John Doe",
          "duplicateStatementsSecondary": "YES",
          "duplicateLettersSecondary": "YES",
          "specialAccountHandling": "NONE"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### Update Cardholder Address
This updates the cardholder address.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/address
```
{
      "cardNumber": "4000200030004000",
      "address": [
          {
              "addressType": "BILLING",
              "addressLine1": "EPM02",
              "addressLine2": "ST 2345",
              "city": "Chicago",
              "countryCode": "IND",
              "stateCode": "AP",
              "zipCode": "52316",
              "isCardMailer": false,
              "isPinMailer": true,
              "beginDate": "2022-02-24",
              "endDate": "2023-01-03",
              "addressCategoryCode": "TEMPORARY"
          }
      ]
  }
```
#### Response
**HTTP Code:** 204 No Content
### Update Cardholder Contact Information
This updates the cardholder contact information.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/contact
```
{
      "cardNumber": "4000200030004000",
      "tcpa": [
          {
              "tcpaType": "ENFACT",
              "consentForVoice": true,
              "consentForText": true,
              "lastUpdatedDate": "2022-02-14",
              "lastUpdatedBy": "kgoyal"
          }
      ],
      "contact": {
          "voice": {
              "homePhoneNumber": "757-674-7376",
              "mobilePhoneNumber": "666-666-6376",
              "workPhoneNumber": "787-967-5376",
              "textAddress": "787-967-5376"
          },
          "email": {
              "emailAddress": "fiserv77@gmail.com"
          },
          "text": {
              "homePhoneNumber": "000-555-0000",
              "workPhoneNumber": "000-555-0000",
              "mobilePhoneNumber": "000-555-0000",
              "textAddress": "000-555-0000"
          },
          "enfact": {
              "enfactLanguagePreference": "ENGLISH"
          },
          "enfactVoice": {
              "homePhone": true,
              "workPhone": true,
              "mobilePhone": true,
              "emailAddress": true,
              "textAddress": true
          },
          "enfactText": {
              "homePhone": true,
              "workPhone": true,
              "mobilePhone": true,
              "emailAddress": true,
              "address": true,
              "mobileText": true
          },
          "stepUpText": {
              "homePhone": true,
              "workPhone": true,
              "mobilePhone": true,
              "emailAddress": true,
              "address": true,
              "mobileText": true
          },
          "stepUpVoice": {
              "homePhone": true,
              "workPhone": true,
              "mobilePhone": true,
              "emailAddress": true,
              "address": true,
              "mobileText": true
          }
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

## Details
**Version 2**

**Credit**

### Update Additional Information Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/additionalInfo
```
{
      "cardNumber": "4000200030004001",
      "creditAdditionalInfo": {
          "prefix": "DR.",
          "cardholderName": "Doe, John H",
          "association": "PRIMARY",
          "vip": true,
          "gender": "MALE",
          "dateOfBirth": "1990-08-24",
          "employeeCode": true,
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "123005678",
          "ein": "123005678",
          "dnaPersonId": "123005678",
          "isDeceased": false,
          "memoLine1": "This is an example added to a cardholder record.",
          "memoLine2": "Customer requested name change, updating contact information on account",
          "employerName": "Fiserv",
          "personalizedEmbossingText": "Home Team",
          "duplicateStatementsSecondary": false,
          "duplicateLettersSecondary": false,
          "specialHandling": "NONE",
          "memberSinceDate": "03/22"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content


**Version 3**

**Debit**

### Update Additional Information Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/additionalInfo
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "debitAdditionalInfo": {
          "memberNumber": "0",
          "memberSinceDate": "03/22",
          "dateOfBirth": "1990-08-24",
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "123005678",
          "verificationText": "My name is John",
          "callerId": "1005550001",
          "updateNameDetails": [
              {
                  "cardholderName": "Doe, John H",
                  "priorCardholderName": "Doe, Alex M",
                  "nameSuffix": "MD",
                  "additionalEmbossLine": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001"
              }
          ]
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### Update Additional Information Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/additionalInfo
```
{
      "cardNumber": "4000200030004000",
      "debitAdditionalInfo": {
          "memberNumber": "0",
          "memberSinceDate": "03/22",
          "dateOfBirth": "1990-08-24",
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "123005678",
          "verificationText": "My name is John",
          "callerId": "1005550001",
          "updateNameDetails": [
              {
                  "cardholderName": "Doe, John H",
                  "priorCardholderName": "Doe, Alex M",
                  "nameSuffix": "MD",
                  "additionalEmbossLine": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001"
              }
          ]
      }
  }
```
#### Response
**HTTP Code**: 204 No Content
### Update Additional Information Using NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/additionalInfo
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "debitAdditionalInfo": {
          "memberNumber": "0",
          "memberSinceDate": "03/22",
          "dateOfBirth": "1990-08-24",
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "123005678",
          "verificationText": "My name is John",
          "callerId": "1005550001",
          "updateNameDetails": [
              {
                  "cardholderName": "Doe, John H",
                  "priorCardholderName": "Doe, Alex M",
                  "nameSuffix": "MD",
                  "additionalEmbossLine": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001"
              }
          ]
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### Update ATM Preferences Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/atmPreferences
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "atmPreferences": {
          "languageCode": "ENGLISH",
          "amount": 240,
          "accountType": "SAVINGS",
          "receiptOption": "ASK_ME"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### Update ATM Preferences Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/atmPreferences
```
{
      "cardNumber": "4000200030004000",
      "atmPreferences": {
          "languageCode": "ENGLISH",
          "amount": 240,
          "accountType": "SAVINGS",
          "receiptOption": "ASK_ME"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### Update ATM Preferences Using NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/atmPreferences
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "atmPreferences": {
          "languageCode": "ENGLISH",
          "amount": 240,
          "accountType": "SAVINGS",
          "receiptOption": "ASK_ME"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

**Version 2**

**Debit**

### Cardholder Search with Full Card Record
Retrieve cardholder information based on other commonly known information.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "cardNumber": "4000100020003000",
      "taxIdOrSsn": "123005678",
      "accountNumber": "987654321",
      "phone": "0005550000",
      "emailAddress": "jdoe@example.com",
      "dateOfBirth": "1990-08-24",
      "zipCode": "12345",
      "lastFourCardNumber": "4000",
      "lastFourAccountNumber": "6789",
      "lastName": "Doe",
      "lastFourTaxIdOrSsn": "5678"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, Jessie H"
              },
              "cards": [
                  {
                      "cardNumber": "4000100020003000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "0005550000",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "0005550000",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/28",
                      "emailAddress": "jdoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Card Number Only
Retrieve cardholder record using CardNumber Only in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "cardNumber": "4000100020003000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, Jessie H"
              },
              "cards": [
                  {
                      "cardNumber": "4000100020003000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "0005550001",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "0005550000",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/28",
                      "emailAddress": "jdoeh@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with NTT Only
Retrieve cardholder record using nonTransToken Only in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
#### Response
**HTTP Code**: 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, John H"
              },
              "cards": [
                  {
                      "cardNumber": "4000200030004000",
                      "nonTransToken": "piUVBJKZGfks4000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "1005550001",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "1005550001",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/28",
                      "emailAddress": "jessedoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with SSN/tax ID and last name
Returns cardholder records using SSN/tax id and last name only in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "taxIdOrSsn": "123005678",
      "lastName": "Doe"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, Jessie H"
              },
              "cards": [
                  {
                      "cardNumber": "4000100020003000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "0005550000",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "0005550000",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/23",
                      "emailAddress": "jdoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Email Only
Returns cardholder records using email address only in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "emailAddress": "jdoe@example.com"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, Jessie H"
              },
              "cards": [
                  {
                      "cardNumber": "4000100020003000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "0005550000",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "0005550000",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/28",
                      "emailAddress": "jdoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Account and Phone Numbers
Returns cardholder records using account and phone number only in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "accountNumber": "987654321",
      "phone": "0005550000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, Jessie H"
              },
              "cards": [
                  {
                      "cardNumber": "4000100020003000",
                      "accountNumbers": [
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "0005550000",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "0005550000",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/23",
                      "emailAddress": "jdoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Cardholder and NTT Only
Retrieve cardholder record using Card number and nonTransToken in the request.

#### Request
HTTP Method: POST
**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
#### Response
**HTTP Code:** 200 OK
```{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, John H"
              },
              "cards": [
                  {
                      "cardNumber": "4000200030004000",
                      "nonTransToken": "piUVBJKZGfks4000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "1005550001",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "1005550001",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/28",
                      "emailAddress": "jessedoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Card Number Full Card and Token Format
Returns cardholder records with NTT using cardNumber with FULL_CARD_AND_TOKEN format in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "FULL_CARD_AND_TOKEN"
  }
```
#### Response
**HTTP Code:** 200 OK
```{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, John H"
              },
              "cards": [
                  {
                      "cardNumber": "4000200030004000",
                      "nonTransToken": "piUVBJKZGfks4000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "1005550001",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "0005550000",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/28",
                      "emailAddress": "jessedoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Card Number Full Card Only Format
Returns cardholder records using cardNumber with FULL_CARD_ONLY format in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "FULL_CARD_ONLY"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, John H"
              },
              "cards": [
                  {
                      "cardNumber": "4000200030004000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "1005550001",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "1005550001",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/28",
                      "emailAddress": "jessedoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Card Number Token Only Format
Returns cardholder records using cardNumber with TOKEN_ONLY format in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "TOKEN_ONLY"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, John H"
              },
              "cards": [
                  {
                      "nonTransToken": "piUVBJKZGfks4000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "1005550001",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "1005550001",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/28",
                      "emailAddress": "jessedoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with NTT Masked Card Only Format
Returns cardholder records using nonTransToken with MASKED_CARD_ONLY format in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "responseFormat": "MASKED_CARD_ONLY"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Doe, John H"
              },
              "cards": [
                  {
                      "cardNumber": "400020XXXXXX4000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "memberNumber": "0",
                      "cardStatus": "NORMAL",
                      "statusReasonCode": "LOST",
                      "cardActivationStatus": "NOT_ACTIVATED",
                      "cardType": "DEBIT",
                      "association": "PRIMARY",
                      "zipCode": "12345",
                      "phone": "1005550001",
                      "cellPhone": "1005550001",
                      "homePhone": "1005550001",
                      "workPhone": "1005550001",
                      "textAddress": "1005550001",
                      "dateOfBirth": "1990-08-24",
                      "expirationDate": "10/28",
                      "emailAddress": "jessedoe@example.com",
                      "cardClass": "VSCK"
                  }
              ]
          }
      ]
  }
```

**Version 1**

**Credit**

### Additional Info Search with Credit Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/additionalInfo/search
```
{
      "cardNumber": "4000200030004001"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4001",
      "cardClass": "AAA00",
      "creditAdditionalInfo": {
          "accountNumber": "123456789",
          "externalCustomerId": "XXXXX6789",
          "prefix": "DR",
          "cardholderName": "Doe, John H",
          "association": "PRIMARY",
          "vip": true,
          "gender": "NOT_SPECIFIED",
          "dateOfBirth": "1990-08-24",
          "employeeCode": true,
          "motherMaidenName": "Smith",
          "empId": "123005678",
          "taxIdOrSsn": "XXXXX5678",
          "ein": "XXXXX5678",
          "dnaPersonId": "123005678",
          "isDeceased": false,
          "memoLine1": "This is an example added to a cardholder record.",
          "memoLine2": "Customer requested name change, updating contact information on account.",
          "employerName": "Fiserv",
          "personalizedEmbossingText": "Home Team",
          "duplicateStatementsSecondary": false,
          "duplicateLettersSecondary": false,
          "specialHandling": "NONE",
          "memberSinceDate": "03/22"
      }
  }
```
**Version 1**

**Debit**

### Cardholder Search with Full Record
Retrieve cardholder information based on other commonly known information.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search
```
{
      "cardNumber": "4000200030004000",
      "ssnOrTaxid": "987001234",
      "accNumber": "123456789",
      "phone": "0005550001",
      "emailAddress": "alexsmith@email.com",
      "dateOfBirth": "10/02/14",
      "postalCode": "12345",
      "lastFourCardNumber": "4000",
      "lastFourAccNumber": "6789",
      "lastName": "Smith"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Alex Smith"
              },
              "cards": [
                  {
                      "cardNumber": "4000200030004000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "cardMemberNumber": "0",
                      "cardStatus": "NORMAL",
                      "cardType": "CREDIT",
                      "association": "PRIMARY",
                      "expiryDate": "1023",
                      "dateOfBirth": "10/02/14",
                      "postalCode": "12345",
                      "phone": "0005550001",
                      "cellPhone": "0005550001",
                      "homePhone": "0005550001",
                      "workPhone": "0005550001",
                      "textAddress": "0005550001",
                      "emailAddress": "alexsmith@email.com"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Card Number Only
Returns cardholder records using cardNumber only in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search
```
{
      "cardNumber": "4000200030004000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Alex Smith"
              },
              "cards": [
                  {
                      "cardNumber": "4000200030004000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "cardMemberNumber": "0",
                      "cardStatus": "NORMAL",
                      "cardType": "CREDIT",
                      "association": "PRIMARY",
                      "expiryDate": "1023",
                      "dateOfBirth": "10/02/14",
                      "postalCode": "12345",
                      "phone": "0005550001",
                      "cellPhone": "0005550001",
                      "homePhone": "0005550001",
                      "workPhone": "0005550001",
                      "textAddress": "0005550001",
                      "emailAddress": "alexsmith@email.com"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with SSN/tax ID and Name
Returns cardholder records using SSN/tax id and last name only in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search
```
{
      "ssnOrTaxid": "123005678",
      "lastName": "Smith"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Alex Smith"
              },
              "cards": [
                  {
                      "cardNumber": "4000100020003000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "cardMemberNumber": "0",
                      "cardStatus": "ACTIVE",
                      "cardType": "DEBIT",
                      "expiryDate": "1023",
                      "dateOfBirth": "10/02/14",
                      "postalCode": "12345",
                      "phone": "0005550000",
                      "cellPhone": "0005550000",
                      "homePhone": "0005550000",
                      "workPhone": "0005550000",
                      "textAddress": "0005550000",
                      "emailAddress": "alexdoe@email.com"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Email Only
Returns cardholder records using email address only in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search
```
{
      "emailAddress": "alexsmith@email.com"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Alex Smith"
              },
              "cards": [
                  {
                      "cardNumber": "4000200030004000",
                      "accountNumbers": [
                          "123456789",
                          "987654321"
                      ],
                      "cardMemberNumber": "0",
                      "cardStatus": "NORMAL",
                      "cardType": "CREDIT",
                      "association": "PRIMARY",
                      "expiryDate": "1023",
                      "dateOfBirth": "10/02/14",
                      "postalCode": "12345",
                      "phone": "0005550001",
                      "cellPhone": "0005550001",
                      "homePhone": "0005550001",
                      "workPhone": "0005550001",
                      "textAddress": "0005550001",
                      "emailAddress": "alexsmith@email.com"
                  }
              ]
          }
      ]
  }
```
### Cardholder Search with Account and Phone Numbers
Returns cardholder records using account and phone number only in the request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search
```
{
      "accNumber": "123456789",
      "phone": "0005550001"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardholderCardsDetails": [
          {
              "cardholderDetails": {
                  "cardholderName": "Alex Smith"
              },
              "cards": [
                  {
                      "cardNumber": "4000200030004000",
                      "accountNumbers": [
                          "123456789"
                      ],
                      "cardMemberNumber": "0",
                      "cardStatus": "NORMAL",
                      "cardType": "CREDIT",
                      "association": "PRIMARY",
                      "expiryDate": "1023",
                      "dateOfBirth": "10/02/14",
                      "postalCode": "12345",
                      "phone": "0005550001",
                      "cellPhone": "0005550001",
                      "homePhone": "0005550001",
                      "workPhone": "0005550001",
                      "textAddress": "0005550001",
                      "emailAddress": "alexsmith@email.com"
                  }
              ]
          }
      ]
  }
```
### Additional Info Search with Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/additionalInfo/search
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cardClass": "AAA00",
      "debitAdditionalInfo": {
          "accountNumber": "123456789",
          "memberNumber": "0",
          "memberSinceDate": "03/22",
          "dateOfBirth": "1990-08-24",
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "XXXXX5678",
          "verificationText": "Driver's license",
          "callerId": "1005550001",
          "updateNameDetails": [
              {
                  "cardholderName": "Doe, John H",
                  "priorCardholderName": "Doe, Alex M",
                  "nameSuffix": "MD",
                  "additionalEmbossLine": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001"
              }
          ]
      }
  }
```
### Additional Info Search with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/additionalInfo/search
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cardClass": "AAA00",
      "debitAdditionalInfo": {
          "accountNumber": "123456789",
          "memberNumber": "0",
          "memberSinceDate": "03/22",
          "dateOfBirth": "1990-08-24",
          "motherMaidenName": "Smith",
          "taxIdOrSsn": "XXXXX5678",
          "verificationText": "Driver's license",
          "callerId": "1005550001",
          "updateNameDetails": [
              {
                  "cardholderName": "Doe, John H",
                  "priorCardholderName": "Doe, Alex M",
                  "nameSuffix": "MD",
                  "additionalEmbossLine": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001"
              }
          ]
      }
  }
```
### ATM Preferences Search with Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/atmPreferences/search
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code**: 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "atmPreferences": [
          {
              "language": "ENGLISH",
              "amount": "240",
              "accountType": "CHECKING",
              "receiptOption": "ASK_ME",
              "terminalOwnerId": "USER01",
              "sourceType": "A",
              "action": "UPDATE",
              "actionDateTime": "2014-10-02T15:01:23.045Z",
              "updatedBy": "USER01"
          }
      ]
  }
```
### ATM Preferences Search with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/atmPreferences/search
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "atmPreferences": [
          {
              "language": "ENGLISH",
              "amount": "240",
              "accountType": "CHECKING",
              "receiptOption": "ASK_ME",
              "terminalOwnerId": "USER01",
              "sourceType": "A",
              "action": "UPDATE",
              "actionDateTime": "2014-10-02T15:01:23.045Z",
              "updatedBy": "USER01"
          }
      ]
  }
```
### ATM Preferences Search with NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/atmPreferences/search
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "atmPreferences": [
          {
              "language": "ENGLISH",
              "amount": "240",
              "accountType": "CHECKING",
              "receiptOption": "ASK_ME",
              "terminalOwnerId": "USER01",
              "sourceType": "A",
              "action": "UPDATE",
              "actionDateTime": "2014-10-02T15:01:23.045Z",
              "updatedBy": "USER01"
          }
      ]
  }
```
## Display Digital Card
**Version 2**

**Debit**

### Auth Details with Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/authDetails
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cv2": "282",
      "expirationDate": "10/28"
  }
```

### Auth Details with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/authDetails
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cv2": "282",
      "expirationDate": "10/28"
  }
```
### Auth Details with NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/authDetails
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cv2": "282",
      "expirationDate": "10/28"
  }
```
**Version 1**

**Debit**

### Card Authorization Details
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/authDetails
```
{
      "cardNumber": "4000200030004000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "cv2": "888",
      "expirationDate": "0624"
  }
```
## Limits
**Version 2**

**Debit**

**Search Limits**
### Using Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/search
```
{
  "cardNumber": "4000200030004000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "2",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "0",
    "cardOpenToBuyTotalAmount": "0"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/search
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "2",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "0",
    "cardOpenToBuyTotalAmount": "0"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/search
```
{
  "nonTransToken": "piUVBJKZGfks4000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "2",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "0",
    "cardOpenToBuyTotalAmount": "0"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Token Only Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/search
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "TOKEN_ONLY",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "2",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "0",
    "cardOpenToBuyTotalAmount": "0"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Full Card Only Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/search
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_ONLY",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "2",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "0",
    "cardOpenToBuyTotalAmount": "0"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Full Card and Token Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/search
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_AND_TOKEN",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "2",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "0",
    "cardOpenToBuyTotalAmount": "0"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Masked Card Only Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/search
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_ONLY",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "2",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "0",
    "cardOpenToBuyTotalAmount": "0"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Masked Card and Token Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/search
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_AND_TOKEN",
  "memberNumber": "0"
}
```
####  #### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "2",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "0",
    "cardOpenToBuyTotalAmount": "0"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```

**Update Daily Limits**

### Using Card Number
#### Request
**HTTP Method**: PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/daily
```
{
  "cardNumber": "4000200030004000",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
```
### Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/daily
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
}
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
### Using NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/daily
```
{
      {
  "nonTransToken": "piUVBJKZGfks4000",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
````
### Using Card Number and Full Card Only Response Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/daily
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_ONLY",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
### Using Card Number and Full Card and Token Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/daily
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_AND_TOKEN",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
### Using Card Number and Masked Card Only Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/daily
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_ONLY",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
### Using Card Number and Masked Card and Token Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/daily
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_AND_TOKEN",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
### Using Card Number and Token Only Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/daily
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "TOKEN_ONLY",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
#### Response
**HTTP Code:** **HTTP Code:** 200 OK
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "nonExpiring": false,
    "limitExpirationDate": "2024-12-31",
    "limitType": "OVERRIDE",
    "aggregateOfflineAmount": "0",
    "aggregateTotalAmount": "0",
    "atmOfflineAmount": "200",
    "atmTotalAmount": "2000",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "100",
    "cashEquivTotalAmount": "500",
    "customerNPOfflineAmount": "0",
    "customerNPTotalAmount": "0",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "400",
    "posTotalAmount": "3000",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  }
}
```
## Update Open to Buy Limits
### Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
```
{
  "cardNumber": "4000200030004000",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
### Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "openToBuyLimits": {
	"accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
### Using NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
### Using Card Number and Token Only Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "TOKEN_ONLY",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
#### Response
**HTTP Code**: 200 OK
```{
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
### Using Card Number and Full Card Only Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_ONLY",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
### Using Card Number and Full Card and Token Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_AND_TOKEN",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
### Using Card Number and Masked Card Only Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_ONLY",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "memberNumber": "0",
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
### Using Card Number and Masked Card and Token Response Format
#### Request
**HTTP Method**: PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_AND_TOKEN",
  "memberNumber": "0",
  "openToBuyLimits": {
	"accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "openToBuyLimits": {
	"accountOpenToBuyOfflineAmount": "123",
    "accountOpenToBuyTotalAmount": "9999",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  }
}
```

## Update Velocity Limits
### Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
```
{
  "cardNumber": "4000200030004000",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
### Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
### Using NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
### Using Card Number and Token Only Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "TOKEN_ONLY",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
````
### Using Card Number and Full Card Only Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_ONLY",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
### Using Card Number and Full Card and Token Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_AND_TOKEN",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
### Using Card Number and Masked Card Only Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_ONLY",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
### Using Card Number and Masked Card and Token Response Format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_AND_TOKEN",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "velocityLimits": {
    "aggMaxCardUsage": "20",
    "aggTimeInterval": "10:10",
    "atmMaxCardUsage": "20",
    "atmTimeInterval": "10:10",
    "cashEquivMaxCardUsage": "4",
    "cashEquivTimeInterval": "10:10",
    "posMaxCardUsage": "4",
    "posTimeInterval": "10:10"
  }
}
```
## Set to Default Limits
### Using Card Number
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/default
```
{
  "cardNumber": "4000200030004000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "limitType": "CARD_CLASS",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "5",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and NTT
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/default
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "limitType": "CARD_CLASS",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "5",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using NTT
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/default
```
{
  "nonTransToken": "piUVBJKZGfks4000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "limitType": "CARD_CLASS",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "5",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Token Only Response Format
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/default
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "TOKEN_ONLY",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "limitType": "CARD_CLASS",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "5",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Full Card Only Response Format
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/default
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_ONLY",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "memberNumber": "0",
  "dailyLimits": {
    "limitType": "CARD_CLASS",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "5",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Full Card and Token Response Format
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/default
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "FULL_CARD_AND_TOKEN",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "limitType": "CARD_CLASS",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "5",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Masked Card Only Response Format
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/default
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_ONLY",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "memberNumber": "0",
  "dailyLimits": {
    "limitType": "CARD_CLASS",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "5",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```
### Using Card Number and Masked Card and Token Response Format
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/default
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_AND_TOKEN",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "dailyLimits": {
    "limitType": "CARD_CLASS",
    "aggregateOfflineAmount": "500",
    "aggregateTotalAmount": "2500",
    "atmOfflineAmount": "300",
    "atmTotalAmount": "600",
    "cashAdvanceOfflineAmount": "0",
    "cashAdvanceTotalAmount": "0",
    "cashEquivOfflineAmount": "5",
    "cashEquivTotalAmount": "10",
    "customerNPOfflineAmount": "500",
    "customerNPTotalAmount": "1500",
    "dayOfDepositAvailabilityTotalAmount": "0",
    "mtCreditDlyCntOffline": "0",
    "mtCreditDlyCntTotal": "0",
    "mtCreditDlyOfflineAmount": "0",
    "mtCreditDlyTotalAmount": "0",
    "mtCreditPerTranOfflineAmount": "0",
    "mtCreditPerTranTotalAmount": "0",
    "mtFundingAmtPerTranOfflineAmount": "0",
    "mtFundingAmtPerTranTotalAmount": "0",
    "mtFundingDlyCntOffline": "0",
    "mtFundingDlyCntTotal": "0",
    "mtFundingDlyOfflineAmount": "0",
    "mtFundingDlyTotalAmount": "0",
    "posOfflineAmount": "500",
    "posTotalAmount": "2500",
    "signatureDebitPOSOfflineAmount": "0",
    "signatureDebitPOSTotalAmount": "0"
  },
  "openToBuyLimits": {
    "accountOpenToBuyOfflineAmount": "0",
    "accountOpenToBuyTotalAmount": "0",
    "cardOpenToBuyOfflineAmount": "123",
    "cardOpenToBuyTotalAmount": "9999"
  },
  "velocityLimits": {
    "aggMaxCardUsage": "0",
    "aggTimeInterval": "00:00",
    "atmMaxCardUsage": "0",
    "atmTimeInterval": "00:00",
    "cashEquivMaxCardUsage": "0",
    "cashEquivTimeInterval": "00:00",
    "posMaxCardUsage": "0",
    "posTimeInterval": "00:00"
  }
}
```

## Order
**Version 3**

**Debit**

### Search with CardNumber For Credit
#### Request
****HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/order/search
```
{
    "cardNumber": "4000200030004001",
    "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "orders": [
        {
            "cardNumber": "400020XXXXXX4001",
            "nonTransToken": "pSAZIXCAXrAo4001",
            "transactionCode": "194",
            "cardPlasticsCount": "001",
            "specialHandling": "NONE",
            "cardholderOrderInfo": {
                "cardholderName": "Jesse Doe",
                "personalizedEmbossingText": "Home Team"
            }
        }
    ]
}
```
### Search with NTT and CardNumber For Credit

### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/order/search
```
{
    "cardNumber": "4000200030004001",
    "nonTransToken":"pSAZIXCAXrAo4001",
    "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "orders": [
        {
            "cardNumber": "400020XXXXXX4001",
            "nonTransToken": "pSAZIXCAXrAo4001",
            "transactionCode": "194",
            "cardPlasticsCount": "001",
            "specialHandling": "NONE",
            "cardholderOrderInfo": {
                "cardholderName": "Jesse Doe",
                "personalizedEmbossingText": "Home Team"
            }
        }
    ]
}
```

### Search with NTT For Credit
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/order/search
```
{
    "nonTransToken":"pSAZIXCAXrAo4001",
    "memberNumber": "0"
}
````
#### Response
**HTTP Code:** 200 OK
```
{
    "orders": [
        {
            "nonTransToken": "pSAZIXCAXrAo4001",
            "transactionCode": "194",
            "cardPlasticsCount": "001",
            "specialHandling": "NONE",
            "cardholderOrderInfo": {
                "cardholderName": "Jesse Doe",
                "personalizedEmbossingText": "Home Team"
            }
        }
    ]
}
```

### 



**Version 2**

**Debit**

### Cancel Debit Order with Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/order
```
{
      "cardNumber": "4000200030004000",
      "orderId": "436",
      "memberNumber": "0",
      "action": "CANCEL",
      "rushType": "NONE",
      "orderType": "CARD"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "card": {
          "cardNumber": "400020XXXXXX4000",
          "action": "CANCEL"
      }
  }
```
### Cancel Debit Order with NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/order
```
{
      "nonTransToken": "WUPIL5DQTZGM3000",
      "orderId": "436",
      "memberNumber": "0",
      "action": " CANCEL",
      "rushType": "NONE",
      "orderType": "CARD"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "card": {
          "nonTransToken": "WUPIL5DQTZGM3000",
          "action": "CANCEL"
      }
  }
```
### Search Debit Orders with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardsSearch without NTT and CardNumber
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/order/search
```
{
    "memberNumber": "0"
}
```
#### Response

**HTTP Code:** 400 Bad Request
```
{
    "type": "Input Validation Exception",
    "title": "Bad Request",
    "message": "Either cardNumber or nontranstoken should be included in the request",
    "instance": "uri=/api/cards/v4/order/search",
    "timestamp": "2022-05-06T14:29:42.173912",
    "code": "400-1003-13005",
    "traceId": "b17138add0abe76a",
    "spanId": "cae622c682896f9e",
    "moreDetails": [
        {
            "code": "1003-13005",
            "detail": "Either cardNumber or nontranstoken should be included in the request"
        }
    ]
}
````
```
{
      "cardNumber": "4000100020003000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "orders": [
          {
              "cardNumber": "400010XXXXXX3000",
              "orderStatus": "ACTIVE",
              "orderType": "CARD",
              "rushType": "REGULAR",
              "processedDate": "2022-08-03",
              "orderId": "4974",
              "orderDate": "2022-09-09",
              "orderReason": "NEW",
              "orderedBy": "Jesse Doe",
              "memberNumber": "0",
              "logo": "APIP",
              "lastMaintenanceBy": "Jesse Doe",
              "lastMaintainanceDate": "1990-08-24",
              "lastMaintainanceTime": "12:00",
              "cardholderOrderInfo": {
                  "nameSequenceNumber": "1",
                  "cardholderName": "Jesse Doe",
                  "personalizedEmbossingText": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001",
                  "nameSuffix": "MD"
              },
              "orderAddress": {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NewJersey",
                  "zipCode": "12345",
                  "addressType": "PRIMARY"
              },
              "cardMiscellaneous": {
                  "cardClass": "AAA00",
                  "emv": "CONTACT",
                  "pinVendor": "1234",
                  "vendor": "Home Supply"
              }
          }
      ]
  }
```
### Search Debit Orders with NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/order/search
```
{
      "nonTransToken": "WUPIL5DQTZGM3000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "orders": [
          {
              "nonTransToken": "WUPIL5DQTZGM3000",
              "orderStatus": "ACTIVE",
              "orderType": "CARD",
              "rushType": "REGULAR",
              "processedDate": "2022-08-03",
              "orderId": "4974",
              "orderDate": "2022-09-09",
              "orderReason": "NEW",
              "orderedBy": "Jesse Doe",
              "memberNumber": "0",
              "logo": "APIP",
              "lastMaintenanceBy": "Jesse Doe",
              "lastMaintainanceDate": "1990-08-24",
              "lastMaintainanceTime": "12:00",
              "cardholderOrderInfo": {
                  "nameSequenceNumber": "1",
                  "cardholderName": "Jesse Doe",
                  "personalizedEmbossingText": "Home Team",
                  "photoId": "EFGH",
                  "plasticId": "PM001",
                  "nameSuffix": "MD"
              },
              "orderAddress": {
                  "addressLine1": "123 Any Street",
                  "addressLine2": "Apt 100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NewJersey",
                  "zipCode": "12345",
                  "addressType": "PRIMARY"
              },
              "cardMiscellaneous": {
                  "cardClass": "AAA00",
                  "emv": "CONTACT",
                  "pinVendor": "1234",
                  "vendor": "Home Supply"
              }
          }
      ]
  }
```
### Update Debit Order with Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/order
```
{
      "cardNumber": "4000200030004000",
      "orderId": "436",
      "memberNumber": "0",
      "action": "UPDATE",
      "rushType": "NONE",
      "orderType": "CARD"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "card": {
          "cardNumber": "400020XXXXXX4000",
          "action": "UPDATE"
      }
  }
```
### Update Debit Order with NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/order
```
{
      "nonTransToken": "WUPIL5DQTZGM3000",
      "orderId": "436",
      "memberNumber": "0",
      "action": "UPDATE",
      "rushType": "NONE",
      "orderType": "CARD"
  }
```
#### Response
**HTTP Code:** **HTTP Code:** 200 OK
```
{
      "card": {
          "nonTransToken": "WUPIL5DQTZGM3000",
          "action": "UPDATE"
      }
  }
```
**Credit**

### Cancel Credit Order
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/order
```
{
      "cardNumber": "4000100020004001",
      "action": "CANCEL"
  }
```
#### Response
**HTTP Code:** 204 
### Search Credit Orders
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/order/search
```
{
      "cardNumber": "4000100020004001"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "orders": [
          {
              "cardNumber": "400020XXXXXX4001",
              "transactionCode": "194",
              "cardPlasticsCount": "001",
              "specialHandling": "NONE",
              "cardholderOrderInfo": {
                  "cardholderName": "JesseDoe",
                  "personalizedEmbossingText": "Red SOX"
              }
          }
      ]
  }
 ```
**Version 1**

**Debit**

### Cancel Debit Order with Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/order
```
{
      "cardNumber": "4000100020004000",
      "action": "CANCEL",
      "debitOnly": {
          "orderId": "436",
          "memberNumber": "0",
          "rushType": "NONE"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
### Search Debit Orders with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/order/search
```
{
      "cardNumber": "4000100020004000 "
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "orders": [
          {
              "cardNumber": "400020XXXXXX4000",
              "orderStatus": "ACTIVE",
              "orderType": "CARD",
              "rushType": "REGULAR",
              "processedDate": "2022-08-03",
              "orderId": "436",
              "orderDate": "2022-09-09",
              "orderReason": "NEW",
              "orderedBy": "JesseDoe",
              "memberNumber": "0",
              "logo": "APIP",
              "lastMaintenanceBy": "JesseDoe",
              "lastMaintainanceDate": "1990-08-24",
              "lastMaintainanceTime": "12:00",
              "cardholderOrderInfo": {
                  "nameSequenceNumber": "1",
                  "cardholderName": "JesseDoe",
                  "personalizedEmbossingText": "Red SOX",
                  "photoId": "EFGH",
                  "plasticId": "PM001",
                  "nameSuffix": "Mr"
              },
              "orderAddress": {
                  "addressLine1": "123AnyStreet",
                  "addressLine2": "Apt100",
                  "city": "Newark",
                  "country": "USA",
                  "state": "NewJersey",
                  "zipCode": "12345",
                  "addressType": "PRIMARY"
              },
              "cardMiscellaneous": {
                  "cardClass": "AAA00",
                  "emv": "CONTACT",
                  "pinVendor": "1234",
                  "vendor": "Home Supply"
              }
          }
      ]
  }
  ```
### Update Debit Order with Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/order
```
{
      "cardNumber": "4000100020004000",
      "action": "UPDATE",
      "debitOnly": {
          "orderId": "436",
          "memberNumber": "0",
          "rushType": "NONE"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

## PIN
**Credit**

### Reset PIN Attempts Using Credit Card Number
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinAttempts

```
{
      "cardNumber": "4000200030004001"
  }
  
```
#### Response
**HTTP Code:** 204 No Content

**Debit**

### Obtain PIN Select Token with Card Number
To select a PIN, you must supply the JWT returned by this operation. The JWT changes each time you make this request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/token
```
    {
        "cardNumber": "4000200030004000"
    }
```
#### Response
**HTTP Code:** 200 OK
```
    {
        "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg"
    }
```
### Obtain PIN Select Token with Card Number and NTT
To select a PIN, you must supply the JWT returned by this operation. The JWT changes each time you make this request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/token
```
{
     "cardNumber": "4000200030004000",
     "nonTransToken": "piUVBJKZGfks4000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
     "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg"
  }
```
### Obtain PIN Select Token with NTT
To select a PIN, you must supply the JWT returned by this operation. The JWT changes each time you make this request.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/token
```
{
     "nonTransToken": "piUVBJKZGfks4000"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
     "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.XU56gXVBUVLIH83fDZ_uUNj-C4f2UpGnTbP0kHLKPFEfOjn0vYP-TCcV0Cy8Q5t0bRNxE_eI6LIRT-p-dL-lQkv5Sx1GXVvsC9L_vFBzz4QU2DbkpwVjVin088uA23OV6EhylCgiwf8Yswu_1Pu8jFyvaFJUIiEvwZkFbHX73IE6fJanhMjgn_4Eo42CVdGgmzYJtfDQ9wkbAW3w3D2C2dkvzQiYeiTTCkRdzIxEeTDcN9NSM_vwElz_zO5ONExRa_2LTPlQPcen9meot8Dzlcqlz0i4Jo2xtLmkG6bA2uQzbAID4dRujhaOhCoW-GodyOvRCjOqFNYHX8tVLBio7w.oDrfGhbXOLDEWBNA.avKcJYf5i_zP2fov70cqzEW0B2znGvIF2zdEp4bkRtSDJrRBKfcbJeEaEakLZaItLDAlXz6ANJLUntsCpyrQ0Jm4nWfjRgtVmWFSUF3TvgLUH8_Pd5e8yZsI_TuJCPDMHSIt8XEkrpyRwsQT8BgUIU-iAuGe70KoFK5Cr5qvGNLgKJDIwSzlaZma-z9HFxTs6m8hKM3_5YMK5AUGsSpsy8Fb6QNhE6enfjc3GeZei1_dwhJC3Cfd8NkeNpH8AkYWGrY_ZvyZ1YAfFdgXeasCAA.yxrJMUH91uZWejU5N1VDRQ"
  }
  ```
### Reset PIN Attempts Using Card Number
Reset the number of PIN attempts to zero.

#### Request
**HTTP METHOD**: PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinAttempts
```
{
      "cardNumber": "4000200030004000",
      "memberNumber":"0"
  }
```  
#### Response
**HTTP Code:** 204 No Content

### Reset PIN Attempts Using Card Number and NTT
Reset the number of PIN attempts to zero.

#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinAttempts
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber":"0"
  }
```  
#### Response
**HTTP Code:** 204 No Content

### Reset PIN Attempts Using NTT
Reset the number of PIN attempts to zero.

#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinAttempts
```
{    
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber":"0"
  }
```  
#### Response
**HTTP Code:** 204 No Content 

### Select a PIN
You must first obtain a JWT with the token operation. Use the JWT returned from the token request.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pin
```
{
    "pin": "2938",
    "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg"
}
```
#### Response
**HTTP Code:** 204 No Content
### Set PIN Offset Using Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinOffset
```
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0",
   "pinOffset": "1234"
}
 ``` 
#### Response
**HTTP Code:** 204 No Content

### Set PIN Offset Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinOffset
```
{
   "cardNumber": "4000200030004000",
   "nonTransToken": "piUVBJKZGfks4000",
   "memberNumber": "0",
   "pinOffset": "1234"
}
```  
#### Response
**HTTP Code:** 204 No Content
### Set PIN Offset Using NTT
#### Request
**HTTP Method:** POST

**Target URL:** hhttps://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinOffset
```
{
   "nonTransToken": "piUVBJKZGfks4000",
   "memberNumber": "0",
   "pinOffset": "1234"
}
```  
#### Response
**HTTP Code:** 204 No Content

## Related Accounts
**Version 2**

**Debit**

**Add Account Association**
### Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "associations": [
    {
      "accountNumber": "123456789",
      "accountType": "CHECKING",
      "accountDescription": "Main",
      "accountStatus": "ACTIVE",
      "primaryAccount": true,
      "restrictedTransactions": "NO_RESTRICTIONS",
      "transactionsAllowed": {
        "balanceInquiries": true,
        "deposits": true,
        "paymentFrom": true,
        "paymentTo": true,
        "posPurchasesReturns": true,
        "transferFrom": true,
        "transferTo": true,
        "withdrawalsCashAdvance": true
      }
    }
  ]
}
```
### Using NTT Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "associations": [
    {
      "accountNumber": "123456789",
      "accountType": "CHECKING",
      "accountDescription": "Main",
      "accountStatus": "ACTIVE",
      "primaryAccount": true,
      "restrictedTransactions": "NO_RESTRICTIONS",
      "transactionsAllowed": {
        "balanceInquiries": true,
        "deposits": true,
        "paymentFrom": true,
        "paymentTo": true,
        "posPurchasesReturns": true,
        "transferFrom": true,
        "transferTo": true,
        "withdrawalsCashAdvance": true
      }
    }
  ]
}
```
### Using Card Number Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```{
  "cardNumber": "4000200030004000",
  "memberNumber": "0",
  "associations": [
    {
      "accountNumber": "123456789",
      "accountType": "CHECKING",
      "accountDescription": "Main",
      "accountStatus": "ACTIVE",
      "primaryAccount": true,
      "restrictedTransactions": "NO_RESTRICTIONS",
      "transactionsAllowed": {
        "balanceInquiries": true,
        "deposits": true,
        "paymentFrom": true,
        "paymentTo": true,
        "posPurchasesReturns": true,
        "transferFrom": true,
        "transferTo": true,
        "withdrawalsCashAdvance": true
      }
    }
  ]
}
```
### Not Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```
{
      "memberNumber": "0",
      "associations": [
          {
              "accountNumber": "123456789",
              "accountType": "CHECKING",
              "accountDescription": "Main",
              "accountStatus": "ACTIVE",
              "primaryAccount": "YES",
              "restrictedTransactions": "NO_RESTRICTIONS",
              "transactionsAllowed": {
                  "balanceInquiries": true,
                  "deposits": true,
                  "paymentFrom": true,
                  "paymentTo": true,
                  "posPurchasesReturns": true,
                  "transferFrom": true,
                  "transferTo": true,
                  "withdrawalsCashAdvance": true
              }
          }
      ]
  }
```
#### Response
**HTTP Code:** 400 Invalid #### Request
```
{
      "type": "Input Validation Exception",
      "title": "Bad #### Request",
      "message": "Please enter either cardNumber or nonTransToken.",
      "instance": "uri=/api/cards/v2/accounts/associations",s
      "timestamp": "2022-05-06T14:29:42.173912",
      "code": "400-121-108",
      "moreDetails": [
          {
              "code": "121-108",
              "detail": "Please enter either cardNumber or nonTransToken."
          }
      ]
  }
```

**Remove Account Association**
### Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations/unassociate
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "accountNumber": "123456789",
      "accountType": "SAVINGS"
  }
```
#### Response
**HTTP Code:** 204 No Content
### Using NTT Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations/unassociate
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "accountNumber": "123456789",
      "accountType": "SAVINGS"
  }
```
#### Response
**HTTP Code:** 204 No Content
### Using Card Number Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations/unassociate
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "accountNumber": "123456789",
      "accountType": "SAVINGS"
  }
```
#### Response
**HTTP Code:** 204 No Content
### Negative Use Case - with Card Number and NTT
Negative case with debit cardNumber and nonTransToken as empty value

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations/unassociate
```
{
      "cardNumber": "",
      "nonTransToken": "",
      "memberNumber": "0",
      "accountNumber": "123456789",
      "accountType": "SAVINGS"
  }
```
#### Response
**HTTP Code:** 400 Invalid #### Request
```
{
      "type": "Input Validation Exception",
      "title": "Bad #### Request",
      "message": "Please see sandbox documentation. Invalid sandbox testing use case.",
      "instance": "/api/cards/v1/card/status/search",
      "timestamp": "2021-09-30T15:42:40.751601",
      "code": "409-121-751",
      "traceId": "6f5fac8060745af5",
      "spanId": "c7cf0a4db13280a7",
      "moreDetails": [
          {
              "code": "1003-751",
              "detail": "Please see sandbox documentation. Invalid sandbox testing use case."
          }
      ]
  }
  ```
### Negative Use Case - without Card Number and NTT
Negative case with debit cardNumber and nonTransToken

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations/unassociate
```
{
      "memberNumber": "0",
      "accountNumber": "123456789",
      "accountType": "SAVINGS"
  }
```
#### Response
**HTTP Code:** 400 Invalid #### Request
```
{
      "type": "Input Validation Exception",
      "title": "Bad #### Request",
      "message": "Please enter either cardNumber or nonTransToken.",
      "instance": "uri=/api/cards/v1/card/status/search",
      "timestamp": "2022-05-06T14:29:42.173912",
      "code": "400-121-108",
      "moreDetails": [
          {
              "code": "121-108",
              "detail": "Please enter either cardNumber or nonTransToken."
          }
      ]
  }
  ```
**Retrieve Associated Accounts**
### Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/search
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
### Using NTT Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/search
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
### Using Card Number Only
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/search
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
### Not Using Card Number and with NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/search
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020xxxxxx4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "associations": [
          {
              "accountNumber": "123456789",
              "accountType": "CHECKING",
              "accountDescription": "Main",
              "accountStatus": "ACTIVE",
              "primaryAccount": "YES",
              "restrictedTransactions": "NO_RESTRICTIONS",
              "transactionsAllowed": {
                  "balanceInquiries": true,
                  "deposits": true,
                  "paymentFrom": true,
                  "paymentTo": true,
                  "posPurchasesReturns": true,
                  "transferFrom": true,
                  "transferTo": true,
                  "withdrawalsCashAdvance": true
              }
          }
      ]
  }
```
### Not Using Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/search
```
{
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 400 Invalid #### Request
```
{
      "type": "Input Validation Exception",
      "title": "Bad #### Request",
      "message": "Please enter either cardNumber or nonTransToken.",
      "instance": "uri=/api/cards/v2/cards/accounts/search",
      "timestamp": "2022-05-06T14:29:42.173912",
      "code": "400-121-108",
      "moreDetails": [
          {
              "code": "121-108",
              "detail": "Please enter either cardNumber or nonTransToken."
          }
      ]
  }
```
**Update Associated Accounts**
### Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "associations": [
    {
      "accountNumber": "123456789",
      "accountType": "CHECKING",
      "accountDescription": "Main",
      "accountStatus": "ACTIVE",
      "primaryAccount": true,
      "restrictedTransactions": "NO_RESTRICTIONS",
      "transactionsAllowed": {
        "balanceInquiries": true,
        "deposits": true,
        "paymentFrom": true,
        "paymentTo": true,
        "posPurchasesReturns": true,
        "transferFrom": true,
        "transferTo": true,
        "withdrawalsCashAdvance": true
      }
    }
  ]
}
```
#### Response
**HTTP Code:** 204 No Content
### Using NTT Only
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "associations": [
    {
      "accountNumber": "123456789",
      "accountType": "CHECKING",
      "accountDescription": "Main",
      "accountStatus": "ACTIVE",
      "primaryAccount": true,
      "restrictedTransactions": "NO_RESTRICTIONS",
      "transactionsAllowed": {
        "balanceInquiries": true,
        "deposits": true,
        "paymentFrom": true,
        "paymentTo": true,
        "posPurchasesReturns": true,
        "transferFrom": true,
        "transferTo": true,
        "withdrawalsCashAdvance": true
      }
    }
  ]
}
```
#### Response
**HTTP Code:** 204 No Content
### Using Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```
{
  "cardNumber": "4000200030004000",
  "memberNumber": "0",
  "associations": [
    {
      "accountNumber": "123456789",
      "accountType": "CHECKING",
      "accountDescription": "Main",
      "accountStatus": "ACTIVE",
      "primaryAccount": true,
      "restrictedTransactions": "NO_RESTRICTIONS",
      "transactionsAllowed": {
        "balanceInquiries": true,
        "deposits": true,
        "paymentFrom": true,
        "paymentTo": true,
        "posPurchasesReturns": true,
        "transferFrom": true,
        "transferTo": true,
        "withdrawalsCashAdvance": true
      }
    }
  ]
}
```
#### Response
**HTTP Code:** 204 No Content
```{
      "type": "Input Validation Exception",
      "title": "Bad #### Request",
      "message": "Please enter either cardNumber or nonTransToken.",
      "instance": "uri=/api/cards/v2/cards/accounts/associations",
      "timestamp": "2022-05-06T14:29:42.173912",
      "code": "400-121-108",
      "moreDetails": [
          {
              "code": "121-108",
              "detail": "Please enter either cardNumber or nonTransToken."
          }
      ]
  }
```
### Not Using Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```
{
      "memberNumber": "0",
      "associations": [
          {
              "accountNumber": "123456789",
              "accountType": "CHECKING",
              "accountDescription": "Main",
              "accountStatus": "ACTIVE",
              "primaryAccount": "YES",
              "restrictedTransactions": "NO_RESTRICTIONS",
              "transactionsAllowed": {
                  "balanceInquiries": true,
                  "deposits": true,
                  "paymentFrom": true,
                  "paymentTo": true,
                  "posPurchasesReturns": true,
                  "transferFrom": true,
                  "transferTo": true,
                  "withdrawalsCashAdvance": true
              }
          }
      ]
  }
```
#### Response
**HTTP Code:** 400 Invalid #### Request
```
{
      "type": "Input Validation Exception",
      "title": "Bad #### Request",
      "message": "Please enter either cardNumber or nonTransToken.",
      "instance": "uri=/api/cards/v2/cards/accounts/associations",
      "timestamp": "2022-05-06T14:29:42.173912",
      "code": "400-121-108",
      "moreDetails": [
          {
              "code": "121-108",
              "detail": "Please enter either cardNumber or nonTransToken."
          }
      ]
  }
```

**Version 1**

**Debit**

### Add Account Association for Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/accounts/associations/add
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "association": {
          "accountNumber": "123456789",
          "accountType": "CHECKING",
          "accountDescription": "Main",
          "accountStatus": "ACTIVE",
          "primaryAccount": "YES",
          "restrictedTransactions": "NO_RESTRICTIONS",
          "transactionsAllowed": {
              "balanceInquiries": true,
              "deposits": true,
              "paymentFrom": true,
              "paymentTo": true,
              "posPurchasesReturns": true,
              "transferFrom": true,
              "transferTo": true,
              "withdrawalsCashAdvance": true
          }
      }
  }
```
#### Response
**HTTP Code:** 201 Created
### Delete Related Account Details for Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/accounts/associations/delete

```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "accountNumber": "123456789",
      "accountType": "CHECKING"
  }
```
#### Response
**HTTP Code:** 204 No Content
### Retrieve Related Account Details for Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/accounts/search
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400010xxxxxx4000",
      "memberNumber": "0",
      "associations": [
          {
              "accountNumber": "123456789",
              "accountType": "CHECKING",
              "accountDescription": "Main",
              "accountStatus": "ACTIVE",
              "primaryAccount": "YES",
              "restrictedTransactions": "NO_RESTRICTIONS",
              "transactionsAllowed": {
                  "balanceInquiries": true,
                  "deposits": true,
                  "paymentFrom": true,
                  "paymentTo": true,
                  "posPurchasesReturns": true,
                  "transferFrom": true,
                  "transferTo": true,
                  "withdrawalsCashAdvance": true
              }
          }
      ]
  }
```
### Update Related Account Details for Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/accounts/associations/update
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "association": {
          "accountNumber": "123456789",
          "accountType": "CHECKING",
          "accountDescription": "Main",
          "accountStatus": "ACTIVE",
          "primaryAccount": "YES",
          "restrictedTransactions": "NO_RESTRICTIONS",
          "transactionsAllowed": {
              "balanceInquiries": true,
              "deposits": true,
              "paymentFrom": true,
              "paymentTo": true,
              "posPurchasesReturns": true,
              "transferFrom": true,
              "transferTo": true,
              "withdrawalsCashAdvance": true
          }
      }
  }
```
#### Response
**HTTP Code:** 204 No Content
## Replacement
**Version 3**

**Debit**

### Replacement with Card Number and NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/v3/cards/replacement
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "order": {
              "addressType": "PRIMARY",
              "orderType": "CARD",
              "rushType": "NONE"
          },
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "order": {
              "addressType": "PRIMARY",
              "rushType": "NONE",
              "orderType": "CARD"
          },
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
### Replacement with NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/v3/cards/replacement
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "order": {
              "addressType": "PRIMARY",
              "orderType": "CARD",
              "rushType": "NONE"
          },
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
#### Response
**HTTP Code**: 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "order": {
              "addressType": "PRIMARY",
              "rushType": "NONE",
              "orderType": "CARD"
          },
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
### Replacement with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/v3/cards/replacement
```
{
      "cardNumber": "4000200030004000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "order": {
              "addressType": "PRIMARY",
              "orderType": "CARD",
              "rushType": "NONE"
          },
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "order": {
              "addressType": "PRIMARY",
              "rushType": "NONE",
              "orderType": "CARD"
          },
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "photoId": "EFGH",
              "plasticId": "PM001",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
**Version 2**

**Credit**

### Replacement with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/v3/cards/replacement
```
{
      "cardNumber": "4000200030004001",
      "cardholderName": "Doe, John H",
      "creditOnly": {
          "cardStock": "00",
          "specialHandling": "NONE",
          "waiveReplacementFee": "Y",
          "cardholder": {
              "personalizedEmbossingText": "Home Team",
              "customerRoleTypeCode": "01"
          }
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4001",
      "cardholderName": "Doe, John H",
      "creditOnly": {
          "cardStock": "00",
          "specialHandling": "NONE",
          "waiveReplacementFee": "Y",
          "cardholder": {
              "personalizedEmbossingText": "Home Team",
              "customerRoleTypeCode": "01"
          }
      }
  }
```
**Version 2**

**Debit**

### Debit Card Replacement with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/replacement
```
{
      "cardNumber": "4000100020003000",
      "cardholderName": "Doe, Jessie H",
      "personalizedEmbossingText": "Home Team",
      "debitOnly": {
          "cardAddressIdentifier": "PRIMARY",
          "expirationDate": "08/24",
          "nameSuffix": "MD",
          "memberNumber": "0",
          "photoId": "Alex",
          "plasticId": "PM001",
          "rushType": "NONE",
          "orderType": "CARD_AND_PIN"
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "card": {
          "cardNumber": "400010XXXXXX3000"
      },
      "cardholderName": {
          "cardholderName": "Doe, Jessie H"
      }
  }
```
### Debit Card Replacement with NTT
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/replacement
```
{
      "nonTransToken": "WUPIL5DQTZGM3000",
      "cardholderName": "Doe, Jessie H",
      "personalizedEmbossingText": "Home Team",
      "debitOnly": {
          "cardAddressIdentifier": "PRIMARY",
          "expirationDate": "08/24",
          "nameSuffix": "MD",
          "memberNumber": "0",
          "photoId": "Alex",
          "plasticId": "PM001",
          "rushType": "NONE",
          "orderType": "CARD_AND_PIN"
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "card": {
          "nonTransToken": "WUPIL5DQTZGM3000"
      },
      "cardholderName": {
          "cardholderName": "Doe, Jessie H"
      }
  }
```

**Version 1**

**Credit**

### Credit Card Replacement with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/replacement
```
{
      "cardNumber": "4000100020003000",
      "cardholderName": "Jesse, Doe",
      "personalizedEmbossingText": "ABC",
      "creditOnly": {
          "cardStock": "00",
          "waiveReplacementFee": "Y",
          "specialHandling": "NONE",
          "customerRoleTypeCode": "01"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

**Version 1**

**Debit**

### Debit Card Replacement with Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/replacement
```
{
      "cardNumber": "4000200030004000",
      "cardholderName": "Alex, Smith",
      "personalizedEmbossingText": "ABC",
      "debitOnly": {
          "cardAddressIdentifier": "PRIMARY",
          "expirationDate": "08/24",
          "nameSuffix": "Mr",
          "memberNumber": "0",
          "photoId": "Alex",
          "plasticId": "PM001",
          "rushType": "NONE"
      }
  }
```
#### Response
**HTTP Code:** 204 No Content

### Debit Card Replacement Instant Issuance with Card Number
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/instantIssuance
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "MASKED_CARD_ONLY",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
#### Response
**HTTP Code**: 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
### Debit Card Replacement Insant Issuance with Card Number and NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/instantIssuance
```{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "responseFormat": "MASKED_CARD_AND_TOKEN",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
### Debit Card Replacement Instant Issuance with NTT
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/instantIssuance
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "cardholderName": "Doe, John H",
      "debitOnly": {
          "memberNumber": "0",
          "cardholder": {
              "expirationDate": "10/28",
              "nameSuffix": "MD",
              "additionalEmbossLine": "Home Team"
          }
      }
  }
```

## Transactions

**Version 3**

**Credit**


### Search Transactions Using Card Number, NTT, Detail Filter

#### Request

**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=detail
```
{
      "cardNumber": "4000200030004001",
      "nonTransToken": "pSAZIXCAXrAo4001",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-15"
          }
      ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "count": 1,
  "cardNumber": "400020XXXXXX4001",
  "nonTransToken": "pSAZIXCAXrAo4001",
  "transactions": [
    {
      "transactionSummary": {
        "authorizationCode": "000229",
        "responseCode": "912",
        "responseCodeDescription": "APPROVED - WITH BALANCES",
        "responseDetails": "51-B W/D purchase transfer",
        "status": "APPROVED",
        "tranCode": "012000",
        "tranId": "314003065381779",
        "transactionStatus": "APPROVED",
        "transactionType": "WITHDRAWAL",       
        "creditOnly": {
          "effectiveDate": "04-OCT-2021 05:01:05 AM",
          "merchantCode": "6011",
          "messageId": "9906",
          "networkId": "0004"
        }
      },
      "transactionDetails": {
        "acquiringId": "11100170",
        "applicationTranCounter": "00AF",
        "cardAcceptorId": "CARD ACCEPTOR",
        "cardEntryMode": "Swiped/Machine read",
        "cavvResult": "V",
        "cvResult": "Passed",
        "cvvResult": "Pass",
        "enfactNearTimeScore": "0479",
        "enfactRealTimeDecision": "Approve",
        "enfactRealTimeScore": "0243",
        "enfactRecommendation": "approve",
        "expirationDate": "12/30",
        "messageReasonCode": "2104",
        "networkScore": "10",
        "ruleManagerRecommendation": "Pass",
        "ruleManagerRuleName": "FastReplyGlobalRule",
        "settlementCurrencyCode": "840",
        "stateCode": "NJ",
        "systemAuditNumber": "106308",
        "terminalCountryCode": "USA",
        "transactionBlockerResult": "2 - Successful",       
        "creditOnly": {
          "acquiringCountryCode": "USA",
          "additionalData1": "D11101B99001",
          "additionalData2": "60905",
          "appInterchangeProfile": "11FF",
          "availableUsage": "72968.00",
          "avsOptionCode": "51",
          "avsPostalCode": "337131520",
          "cardAcceptorCity": "ROGERSVILLE",
          "cardAcceptorName": "Pax Technology I",
          "cardAcceptorTermId": "WD644000",
          "cardSequenceNumber": "",
          "cvcResultCode": false,
          "cvvCVVtwo": "110123",
          "fraudDecision": "decline",
          "original#### ResponseCode": "59",
          "pinVerified": true,
          "posCode": "006 - PRE-AUTHORIZED REQUEST",
          "posMode": "801",
          "referenceNumber": "109000254949",
          "reversalreason": "2523",
          "riskCodeOne": "15C2BT",
          "riskReasonCodeOne": "441LR",
          "riskScore": "878A1",
          "settlementAmount": "422.72",
          "settlementConversionRate": "808464432",
          "tagCode": "120W00203000",
          "tagData": "910",
          "tranAmtOriginal": "901.53",
          "tranFeeAmount": "20.00",
          "transmissionDateTime": "25-AUG-2023 11:41:21 AM",         
          "postedTransactionDetails": {
            "authorizationCode": "000000",
            "cardholderAccountNumber": "443011000000018",
            "detailTransactionIdentifier": "000000000000000",
            "merchantCategoryCode": "00000",
            "merchantNumber": "443011000000398",
            "originalAuthAdjustmentAmount": "20.00",
            "postingDate": "2021-10-14",
            "promotionId": "11100171",
            "referenceNumber": "109000254949",
            "transactionAccountNumber": "443011000000018",
            "transactionCode": "CD",
            "transactionDescription": "MERCHANT ACCOUNT"
          }
        }
      }
    }
  ]
}
```

### Search Transactions Using Card Number, NTT, Summary Filter

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
      "cardNumber": "4000200030004001",
      "nonTransToken": "pSAZIXCAXrAo4001",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-14"
          }
      ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "transactions": [
        {
         "transactionSummary": {
            "authorizationCode": "000229",
            "responseCode": "912",
            "responseCodeDescription": "APPROVED - WITH BALANCES",
            "responseDetails": "51-B W/D purchase transfer",
            "status": "APPROVED",
            "tranCode": "012000",
            "tranId": "314003065381779",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "creditOnly": {
              "effectiveDate": "04-OCT-2021 05:01:05 AM",
              "merchantCode": "6011",
              "messageId": "9906",
              "networkId": "0004"
            }
         }
        }
    ]
}
```

### Search Transactions Using Card Number, NTT, Transaction Code, Summary Filter

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "filterCriteria": [
        {
            "filterBy": "TRANSACTION_CODE",
            "filterValue": "012000"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "transactions": [
        {
         "transactionSummary": {
            "authorizationCode": "000229",
            "responseCode": "912",
            "responseCodeDescription": "APPROVED - WITH BALANCES",
            "responseDetails": "51-B W/D purchase transfer",
            "status": "APPROVED",
            "tranCode": "012000",
            "tranId": "314003065381779",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "creditOnly": {
              "effectiveDate": "04-OCT-2021 05:01:05 AM",
              "merchantCode": "6011",
              "messageId": "9906",
              "networkId": "0004"
            }
         }
        }
    ]
}
```

### Search Transactions Using NTT and Detail Filter

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=detail
```
{
      "nonTransToken": "pSAZIXCAXrAo4001",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-15"
          }
      ]
}
```
****#### Response
**HTTP Code:** 200 OK
```
{
  "count": 1,
  "cardNumber": "400020XXXXXX4001",
  "nonTransToken": "pSAZIXCAXrAo4001",
  "transactions": [
    {
      "transactionSummary": {
        "authorizationCode": "000229",
        "responseCode": "912",
        "responseCodeDescription": "APPROVED - WITH BALANCES",
        "responseDetails": "51-B W/D purchase transfer",
        "status": "APPROVED",
        "tranCode": "012000",
        "tranId": "314003065381779",
        "transactionStatus": "APPROVED",
        "transactionType": "WITHDRAWAL",       
        "creditOnly": {
          "effectiveDate": "04-OCT-2021 05:01:05 AM",
          "merchantCode": "6011",
          "messageId": "9906",
          "networkId": "0004"
        }
      },
      "transactionDetails": {
        "acquiringId": "11100170",
        "applicationTranCounter": "00AF",
        "cardAcceptorId": "CARD ACCEPTOR",
        "cardEntryMode": "Swiped/Machine read",
        "cavvResult": "V",
        "cvResult": "Passed",
        "cvvResult": "Pass",
        "enfactNearTimeScore": "0479",
        "enfactRealTimeDecision": "Approve",
        "enfactRealTimeScore": "0243",
        "enfactRecommendation": "approve",
        "expirationDate": "12/30",
        "messageReasonCode": "2104",
        "networkScore": "10",
        "ruleManagerRecommendation": "Pass",
        "ruleManagerRuleName": "FastReplyGlobalRule",
        "settlementCurrencyCode": "840",
        "stateCode": "NJ",
        "systemAuditNumber": "106308",
        "terminalCountryCode": "USA",
        "transactionBlockerResult": "2 - Successful",       
        "creditOnly": {
          "acquiringCountryCode": "USA",
          "additionalData1": "D11101B99001",
          "additionalData2": "60905",
          "appInterchangeProfile": "11FF",
          "availableUsage": "72968.00",
          "avsOptionCode": "51",
          "avsPostalCode": "337131520",
          "cardAcceptorCity": "ROGERSVILLE",
          "cardAcceptorName": "Pax Technology I",
          "cardAcceptorTermId": "WD644000",
          "cardSequenceNumber": "",
          "cvcResultCode": false,
          "cvvCVVtwo": "110123",
          "fraudDecision": "decline",
          "original#### ResponseCode": "59",
          "pinVerified": true,
          "posCode": "006 - PRE-AUTHORIZED REQUEST",
          "posMode": "801",
          "referenceNumber": "109000254949",
          "reversalreason": "2523",
          "riskCodeOne": "15C2BT",
          "riskReasonCodeOne": "441LR",
          "riskScore": "878A1",
          "settlementAmount": "422.72",
          "settlementConversionRate": "808464432",
          "tagCode": "120W00203000",
          "tagData": "910",
          "tranAmtOriginal": "901.53",
          "tranFeeAmount": "20.00",
          "transmissionDateTime": "25-AUG-2023 11:41:21 AM",         
          "postedTransactionDetails": {
            "authorizationCode": "000000",
            "cardholderAccountNumber": "443011000000018",
            "detailTransactionIdentifier": "000000000000000",
            "merchantCategoryCode": "00000",
            "merchantNumber": "443011000000398",
            "originalAuthAdjustmentAmount": "20.00",
            "postingDate": "2021-10-14",
            "promotionId": "11100171",
            "referenceNumber": "109000254949",
            "transactionAccountNumber": "443011000000018",
            "transactionCode": "CD",
            "transactionDescription": "MERCHANT ACCOUNT"
          }
        }
      }
    }
  ]
}
```

### Search Transaction Using NTT and Summary Filter

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
      "nonTransToken": "pSAZIXCAXrAo4001",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-14"
          }
      ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "transactions": [
        {
         "transactionSummary": {
            "authorizationCode": "000229",
            "responseCode": "912",
            "responseCodeDescription": "APPROVED - WITH BALANCES",
            "responseDetails": "51-B W/D purchase transfer",
            "status": "APPROVED",
            "tranCode": "012000",
            "tranId": "314003065381779",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "creditOnly": {
              "effectiveDate": "04-OCT-2021 05:01:05 AM",
              "merchantCode": "6011",
              "messageId": "9906",
              "networkId": "0004"
            }
         }
        }
    ]
}
```

**Version 3**

**Debit**

### Search Transactions Using Card Number Only and Detail Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=detail
```
{
    "cardNumber": "4000200030004000",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "count": 1,
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "transactions": [
    {
      "transactionSummary": {
        "authorizationCode": "000229",
        "responseCode": "912",
        "responseCodeDescription": "APPROVED - WITH BALANCES",
        "responseDetails": "51-B W/D purchase transfer",
        "status": "APPROVED",
        "tranCode": "012000",
        "tranId": "314003065381779",
        "transactionStatus": "APPROVED",
        "transactionType": "WITHDRAWAL",
        "debitOnly": {
          "acquirerRefNum": "0000000000",
          "amtCharged": "6471902.00",
          "eciMastercard": "910",
          "eciVisa": "7",
          "expirationDateMismatch": false,
          "journalDateTime": "2023-07-20T13:38:53Z",
          "memberNumber": "0",
          "merchantCategoryCode": "6011",
          "merchantCity": "SAINT LOUIS",
          "merchantName": "FLORIDA MEDICAL",
          "merchantStateCode": "DC",
          "messageType": "210- Auth/Completion",
          "network": "000000 - Managed Service On US",
          "pinTransaction": "1 - Signature Network with PIN",
          "posDataInputCapability": "7 - Contactless chip",
          "posDataInputMode": "2 - Swipe",
          "preAuthAmt": "55.00",
          "retrievalRefNumber": "222815000031",
          "sequenceNumber": "000031",
          "sub#### ResponseCode": "D",
          "terminalId": "CATERMID",
          "transactionAmount": "158.41",
          "transactionDateTime": "2021-10-15T17:13:14Z",
          "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
          "unmatchedCompletionFlag": false
        }
      },
      "transactionDetails": {
        "acquiringId": "11100170",
        "applicationTranCounter": "00AF",
        "cardAcceptorId": "CARD ACCEPTOR",
        "cardEntryMode": "Swiped/Machine read",
        "cavvResult": "V",
        "cvResult": "Passed",
        "cvvResult": "Pass",
        "enfactNearTimeScore": "0479",
        "enfactRealTimeDecision": "Approve",
        "enfactRealTimeScore": "0243",
        "enfactRecommendation": "approve",
        "expirationDate": "12/30",
        "messageReasonCode": "2104",
        "networkScore": "10",
        "ruleManagerRecommendation": "Pass",
        "ruleManagerRuleName": "FastReplyGlobalRule",
        "settlementCurrencyCode": "840",
        "stateCode": "NJ",
        "systemAuditNumber": "106308",
        "terminalCountryCode": "USA",
        "transactionBlockerResult": "2 - Successful",
        "debitOnly": {
          "acqPostDate": "16-DEC-2023 12:00:00 AM",
          "atcResult": "Pass",
          "avsResult": "A",
          "camResult": "Valid",
          "cardCountryCode": "USA",
          "cardCounty": "840",
          "cardholderAddress": "98104    706 5TH AVE S",
          "cardLogo": "FOS3",
          "cashbackAmount": "40.00",
          "cvrResult": "03A01000",
          "cvrResultStat": "Pass",
          "cvv2Cvc2Result": true,
          "depositType": "Cash",
          "eCommerce": true,
          "emvApplicationId": "A0000000046000",
          "emvCard": true,
          "emvCardSequence": "004",
          "emvFallback": true,
          "emvTerminal": true,
          "entryMode": "5 - Chip",
          "fromAccount": "123456789",
          "fromAccountType": "Checking",
          "international": false,
          "locAmt1": "6.55",
          "locAmt2": "89.50",
          "merchantAdviceCode": "01",
          "merchantCountry": "USA",
          "merchantId": "STARBUCKS STORE",
          "mobileDenial": "05",
          "offline": true,
          "pinPresent": "1 - Signature Network with PIN",
          "pointOfService": "014 - GENERIC",
          "posDataCode": "52010120300C",
          "posEntryMode": "620",
          "productType": "ATM",
          "recurringPaymentInd": "R",
          "reversalCode": "10 - HARDWARE MALFUNCTION",
          "secureEci": "02 - 3-D Secure authentication attempt no resp",
          "surchargeAmount": "3.95",
          "surchargeReservalAmount": "2.50",
          "terminalLogo": "DSH4",
          "terminalPinCapable": false,
          "terminalStateCode": "NJ",
          "terminalStreet": "11806 SHELBYVILLE RD",
          "toAccount": "123456789",
          "toAccountType": "Checking",
          "token#### RequestorId": "50148904210",
          "tokenTransaction": false,
          "tokenType": "03",
          "transactionNetAmount": "111.96",
          "transactionSource": "E-COMMERCE",
          "tvrResult": "0400040001",
          "tvrResultStat": "Fail"
        }
      }
    }
  ]
}
```

### Search Transactions Using Card Number, NTT, Amount, Summary Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "AMOUNT_FROM",
            "filterValue": "0.00"
        },
        {
            "filterBy": "AMOUNT_TO",
            "filterValue": "200.00"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "transactions": [
        {
          "transactionSummary": {
             "authorizationCode": "000229",
             "responseCode": "912",
             "responseCodeDescription": "APPROVED - WITH BALANCES",
             "responseDetails": "51-B W/D purchase transfer",
             "status": "APPROVED",
             "tranCode": "012000",
             "tranId": "314003065381779",
             "transactionStatus": "APPROVED",
             "transactionType": "WITHDRAWAL",
             "debitOnly": {
               "acquirerRefNum": "0000000000",
               "amtCharged": "6471902.00",
               "eciMastercard": "910",
               "eciVisa": "7",
               "expirationDateMismatch": false,
               "journalDateTime": "2023-07-20T13:38:53Z",
               "memberNumber": "0",
               "merchantCategoryCode": "6011",
               "merchantCity": "SAINT LOUIS",
               "merchantName": "FLORIDA MEDICAL",
               "merchantStateCode": "DC",
               "messageType": "210- Auth/Completion",
               "network": "000000 - Managed Service On US",
               "pinTransaction": "1 - Signature Network with PIN",
               "posDataInputCapability": "7 - Contactless chip",
               "posDataInputMode": "2 - Swipe",
               "preAuthAmt": "55.00",
               "retrievalRefNumber": "222815000031",
               "sequenceNumber": "000031",
               "sub#### ResponseCode": "D",
               "terminalId": "CATERMID",
               "transactionAmount": "158.41",
               "transactionDateTime": "2021-10-15T17:13:14Z",
               "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
               "unmatchedCompletionFlag": false
             }
           }
        }
    ]
}
```


### Search Transactions Using Card Number, NTT, Detail Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=detail
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "count": 1,
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "transactions": [
    {
      "transactionSummary": {
        "authorizationCode": "000229",
        "responseCode": "912",
        "responseCodeDescription": "APPROVED - WITH BALANCES",
        "responseDetails": "51-B W/D purchase transfer",
        "status": "APPROVED",
        "tranCode": "012000",
        "tranId": "314003065381779",
        "transactionStatus": "APPROVED",
        "transactionType": "WITHDRAWAL",
        "debitOnly": {
          "acquirerRefNum": "0000000000",
          "amtCharged": "6471902.00",
          "eciMastercard": "910",
          "eciVisa": "7",
          "expirationDateMismatch": false,
          "journalDateTime": "2023-07-20T13:38:53Z",
          "memberNumber": "0",
          "merchantCategoryCode": "6011",
          "merchantCity": "SAINT LOUIS",
          "merchantName": "FLORIDA MEDICAL",
          "merchantStateCode": "DC",
          "messageType": "210- Auth/Completion",
          "network": "000000 - Managed Service On US",
          "pinTransaction": "1 - Signature Network with PIN",
          "posDataInputCapability": "7 - Contactless chip",
          "posDataInputMode": "2 - Swipe",
          "preAuthAmt": "55.00",
          "retrievalRefNumber": "222815000031",
          "sequenceNumber": "000031",
          "sub#### ResponseCode": "D",
          "terminalId": "CATERMID",
          "transactionAmount": "158.41",
          "transactionDateTime": "2021-10-15T17:13:14Z",
          "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
          "unmatchedCompletionFlag": false
        }
      },
      "transactionDetails": {
        "acquiringId": "11100170",
        "applicationTranCounter": "00AF",
        "cardAcceptorId": "CARD ACCEPTOR",
        "cardEntryMode": "Swiped/Machine read",
        "cavvResult": "V",
        "cvResult": "Passed",
        "cvvResult": "Pass",
        "enfactNearTimeScore": "0479",
        "enfactRealTimeDecision": "Approve",
        "enfactRealTimeScore": "0243",
        "enfactRecommendation": "approve",
        "expirationDate": "12/30",
        "messageReasonCode": "2104",
        "networkScore": "10",
        "ruleManagerRecommendation": "Pass",
        "ruleManagerRuleName": "FastReplyGlobalRule",
        "settlementCurrencyCode": "840",
        "stateCode": "NJ",
        "systemAuditNumber": "106308",
        "terminalCountryCode": "USA",
        "transactionBlockerResult": "2 - Successful",
        "debitOnly": {
          "acqPostDate": "16-DEC-2023 12:00:00 AM",
          "atcResult": "Pass",
          "avsResult": "A",
          "camResult": "Valid",
          "cardCountryCode": "USA",
          "cardCounty": "840",
          "cardholderAddress": "98104    706 5TH AVE S",
          "cardLogo": "FOS3",
          "cashbackAmount": "40.00",
          "cvrResult": "03A01000",
          "cvrResultStat": "Pass",
          "cvv2Cvc2Result": true,
          "depositType": "Cash",
          "eCommerce": true,
          "emvApplicationId": "A0000000046000",
          "emvCard": true,
          "emvCardSequence": "004",
          "emvFallback": true,
          "emvTerminal": true,
          "entryMode": "5 - Chip",
          "fromAccount": "123456789",
          "fromAccountType": "Checking",
          "international": false,
          "locAmt1": "6.55",
          "locAmt2": "89.50",
          "merchantAdviceCode": "01",
          "merchantCountry": "USA",
          "merchantId": "STARBUCKS STORE",
          "mobileDenial": "05",
          "offline": true,
          "pinPresent": "1 - Signature Network with PIN",
          "pointOfService": "014 - GENERIC",
          "posDataCode": "52010120300C",
          "posEntryMode": "620",
          "productType": "ATM",
          "recurringPaymentInd": "R",
          "reversalCode": "10 - HARDWARE MALFUNCTION",
          "secureEci": "02 - 3-D Secure authentication attempt no resp",          
          "surchargeAmount": "3.95",
          "surchargeReservalAmount": "2.50",
          "terminalLogo": "DSH4",
          "terminalPinCapable": false,
          "terminalStateCode": "NJ",
          "terminalStreet": "11806 SHELBYVILLE RD",
          "toAccount": "123456789",
          "toAccountType": "Checking",
          "token#### RequestorId": "50148904210",
          "tokenTransaction": false,
          "tokenType": "03",
          "transactionNetAmount": "111.96",
          "transactionSource": "E-COMMERCE",
          "tvrResult": "0400040001",
          "tvrResultStat": "Fail"
        }
      }
    }
  ]
}
```


### Search Transactions Using Card Number, NTT, Merchant Name, Summary Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "MERCHANT_NAME",
            "filterValue": "FLORIDA MEDICAL"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "transactions": [
        {
          "transactionSummary": {
             "authorizationCode": "000229",
             "responseCode": "912",
             "responseCodeDescription": "APPROVED - WITH BALANCES",
             "responseDetails": "51-B W/D purchase transfer",
             "status": "APPROVED",
             "tranCode": "012000",
             "tranId": "314003065381779",
             "transactionStatus": "APPROVED",
             "transactionType": "WITHDRAWAL",
             "debitOnly": {
               "acquirerRefNum": "0000000000",
               "amtCharged": "6471902.00",
               "eciMastercard": "910",
               "eciVisa": "7",
               "expirationDateMismatch": false,
               "journalDateTime": "2023-07-20T13:38:53Z",
               "memberNumber": "0",
               "merchantCategoryCode": "6011",
               "merchantCity": "SAINT LOUIS",
               "merchantName": "FLORIDA MEDICAL",
               "merchantStateCode": "DC",
               "messageType": "210- Auth/Completion",
               "network": "000000 - Managed Service On US",
               "pinTransaction": "1 - Signature Network with PIN",
               "posDataInputCapability": "7 - Contactless chip",
               "posDataInputMode": "2 - Swipe",
               "preAuthAmt": "55.00",
               "retrievalRefNumber": "222815000031",
               "sequenceNumber": "000031",
               "sub#### ResponseCode": "D",
               "terminalId": "CATERMID",
               "transactionAmount": "158.41",
               "transactionDateTime": "2021-10-15T17:13:14Z",
               "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
               "unmatchedCompletionFlag": false
             }
           }
        }
    ]
}
```

### Search Transactions Using Card Number, NTT, Message Type, Summary Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "MESSAGE_TYPE",
            "filterValue": "210- Auth/Completion"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "transactions": [
        {
          "transactionSummary": {
             "authorizationCode": "000229",
             "responseCode": "912",
             "responseCodeDescription": "APPROVED - WITH BALANCES",
             "responseDetails": "51-B W/D purchase transfer",
             "status": "APPROVED",
             "tranCode": "012000",
             "tranId": "314003065381779",
             "transactionStatus": "APPROVED",
             "transactionType": "WITHDRAWAL",
             "debitOnly": {
               "acquirerRefNum": "0000000000",
               "amtCharged": "6471902.00",
               "eciMastercard": "910",
               "eciVisa": "7",
               "expirationDateMismatch": false,
               "journalDateTime": "2023-07-20T13:38:53Z",
               "memberNumber": "0",
               "merchantCategoryCode": "6011",
               "merchantCity": "SAINT LOUIS",
               "merchantName": "FLORIDA MEDICAL",
               "merchantStateCode": "DC",
               "messageType": "210- Auth/Completion",
               "network": "000000 - Managed Service On US",
               "pinTransaction": "1 - Signature Network with PIN",
               "posDataInputCapability": "7 - Contactless chip",
               "posDataInputMode": "2 - Swipe",
               "preAuthAmt": "55.00",
               "retrievalRefNumber": "222815000031",
               "sequenceNumber": "000031",
               "sub#### ResponseCode": "D",
               "terminalId": "CATERMID",
               "transactionAmount": "158.41",
               "transactionDateTime": "2021-10-15T17:13:14Z",
               "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
               "unmatchedCompletionFlag": false
             }
           }
        }
    ]
}
```

### Search Transactions Using Card Number, NTT, Summary Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "transactions": [
        {
          "transactionSummary": {
             "authorizationCode": "000229",
             "responseCode": "912",
             "responseCodeDescription": "APPROVED - WITH BALANCES",
             "responseDetails": "51-B W/D purchase transfer",
             "status": "APPROVED",
             "tranCode": "012000",
             "tranId": "314003065381779",
             "transactionStatus": "APPROVED",
             "transactionType": "WITHDRAWAL",
             "debitOnly": {
               "acquirerRefNum": "0000000000",
               "amtCharged": "6471902.00",
               "eciMastercard": "910",
               "eciVisa": "7",
               "expirationDateMismatch": false,
               "journalDateTime": "2023-07-20T13:38:53Z",
               "memberNumber": "0",
               "merchantCategoryCode": "6011",
               "merchantCity": "SAINT LOUIS",
               "merchantName": "FLORIDA MEDICAL",
               "merchantStateCode": "DC",
               "messageType": "210- Auth/Completion",
               "network": "000000 - Managed Service On US",
               "pinTransaction": "1 - Signature Network with PIN",
               "posDataInputCapability": "7 - Contactless chip",
               "posDataInputMode": "2 - Swipe",
               "preAuthAmt": "55.00",
               "retrievalRefNumber": "222815000031",
               "sequenceNumber": "000031",
               "sub#### ResponseCode": "D",
               "terminalId": "CATERMID",
               "transactionAmount": "158.41",
               "transactionDateTime": "2021-10-15T17:13:14Z",
               "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
               "unmatchedCompletionFlag": false
             }
           }
        }
    ]
}
```

### Search Transactions Using Card Number, NTT, Transaction Code, Summary Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "TRANSACTION_CODE",
            "filterValue": "012000"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "transactions": [
        {
          "transactionSummary": {
             "authorizationCode": "000229",
             "responseCode": "912",
             "responseCodeDescription": "APPROVED - WITH BALANCES",
             "responseDetails": "51-B W/D purchase transfer",
             "status": "APPROVED",
             "tranCode": "012000",
             "tranId": "314003065381779",
             "transactionStatus": "APPROVED",
             "transactionType": "WITHDRAWAL",
             "debitOnly": {
               "acquirerRefNum": "0000000000",
               "amtCharged": "6471902.00",
               "eciMastercard": "910",
               "eciVisa": "7",
               "expirationDateMismatch": false,
               "journalDateTime": "2023-07-20T13:38:53Z",
               "memberNumber": "0",
               "merchantCategoryCode": "6011",
               "merchantCity": "SAINT LOUIS",
               "merchantName": "FLORIDA MEDICAL",
               "merchantStateCode": "DC",
               "messageType": "210- Auth/Completion",
               "network": "000000 - Managed Service On US",
               "pinTransaction": "1 - Signature Network with PIN",
               "posDataInputCapability": "7 - Contactless chip",
               "posDataInputMode": "2 - Swipe",
               "preAuthAmt": "55.00",
               "retrievalRefNumber": "222815000031",
               "sequenceNumber": "000031",
               "sub#### ResponseCode": "D",
               "terminalId": "CATERMID",
               "transactionAmount": "158.41",
               "transactionDateTime": "2021-10-15T17:13:14Z",
               "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
               "unmatchedCompletionFlag": false
             }
           }
        }
    ]
}
```

### Search Transactions Using Detail Filter NSF

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=detail
```
{
    "cardNumber": "4000200030004000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2022-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 2,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "transactions": [
        {
            "transactionSummary": {
                "authorizationCode": "000229",
                "responseCode": "912",
                "responseCodeDescription": "APPROVED - WITH BALANCES",
                "responseDetails": "51-B W/D purchase transfer",
                "status": "APPROVED",
                "tranCode": "012000",
                "tranId": "314003065381779",
                "transactionStatus": "APPROVED",
                "transactionType": "WITHDRAWAL",
                "debitOnly": {
                    "acquirerRefNum": "0000000000",
                    "amtCharged": "6471902.00",
                    "eciMastercard": "910",
                    "eciVisa": "7",
                    "expirationDateMismatch": false,
                    "journalDateTime": "2023-07-20T13:38:53Z",
                    "memberNumber": "0",
                    "merchantCategoryCode": "6011",
                    "merchantCity": "SAINT LOUIS",
                    "merchantName": "FLORIDA MEDICAL",
                    "merchantStateCode": "DC",
                    "messageType": "210- Auth/Completion",
                    "network": "000000 - Managed Service On US",
                    "pinTransaction": "1 - Signature Network with PIN",
                    "posDataInputCapability": "7 - Contactless chip",
                    "posDataInputMode": "2 - Swipe",
                    "preAuthAmt": "55.00",
                    "retrievalRefNumber": "222815000031",
                    "sequenceNumber": "000031",
                    "sub#### ResponseCode": "D",
                    "terminalId": "CATERMID",
                    "transactionAmount": "158.41",
                    "transactionDateTime": "2022-10-15T17:13:14Z",
                    "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
                    "unmatchedCompletionFlag": false
                }
            },
            "transactionDetails": {
                "acquiringId": "11100170",
                "applicationTranCounter": "00AF",
                "cardAcceptorId": "CARD ACCEPTOR",
                "cardEntryMode": "Swiped/Machine read",
                "cavvResult": "V",
                "cvResult": "Passed",
                "cvvResult": "Pass",
                "enfactNearTimeScore": "0479",
                "enfactRealTimeDecision": "Approve",
                "enfactRealTimeScore": "0243",
                "enfactRecommendation": "approve",
                "expirationDate": "12/30",
                "messageReasonCode": "2104",
                "networkScore": "10",
                "ruleManagerRecommendation": "Pass",
                "ruleManagerRuleName": "FastReplyGlobalRule",
                "settlementCurrencyCode": "840",
                "stateCode": "NJ",
                "systemAuditNumber": "106308",
                "terminalCountryCode": "USA",
                "transactionBlockerResult": "2 - Successful",
                "debitOnly": {
                    "acqPostDate": "16-DEC-2023 12:00:00 AM",
                    "atcResult": "Pass",
                    "avsResult": "A",
                    "camResult": "Valid",
                    "cardCountryCode": "USA",
                    "cardCounty": "840",
                    "cardholderAddress": "98104    706 5TH AVE S",
                    "cardLogo": "FOS3",
                    "cashbackAmount": "40.00",
                    "cvrResult": "03A01000",
                    "cvrResultStat": "Pass",
                    "cvv2Cvc2Result": true,
                    "depositType": "Cash",
                    "eCommerce": true,
                    "emvApplicationId": "A0000000046000",
                    "emvCard": true,
                    "emvCardSequence": "004",
                    "emvFallback": true,
                    "emvTerminal": true,
                    "entryMode": "5 - Chip",
                    "fromAccount": "123456789",
                    "fromAccountType": "Checking",
                    "international": false,
                    "locAmt1": "6.55",
                    "locAmt2": "89.50",
                    "merchantAdviceCode": "01",
                    "merchantCountry": "USA",
                    "merchantId": "STARBUCKS STORE",
                    "mobileDenial": "05",
                    "offline": true,
                    "pinPresent": "1 - Signature Network with PIN",
                    "pointOfService": "014 - GENERIC",
                    "posDataCode": "52010120300C",
                    "posEntryMode": "620",
                    "productType": "ATM",
                    "recurringPaymentInd": "R",
                    "reversalCode": "10 - HARDWARE MALFUNCTION",
                    "secureEci": "02 - 3-D Secure authentication attempt no resp",
                    "surchargeAmount": "3.95",
                    "surchargeReservalAmount": "2.50",
                    "terminalLogo": "DSH4",
                    "terminalPinCapable": false,
                    "terminalStateCode": "NJ",
                    "terminalStreet": "11806 SHELBYVILLE RD",
                    "toAccount": "123456789",
                    "toAccountType": "Checking",
                    "token#### RequestorId": "50148904210",
                    "tokenTransaction": false,
                    "tokenType": "03",
                    "transactionNetAmount": "111.96",
                    "transactionSource": "E-COMMERCE",
                    "tvrResult": "0400040001",
                    "tvrResultStat": "Fail"
                }
            }
        },
        {
            "transactionSummary": {
                "authorizationCode": "000229",
                "responseCode": "912",
                "responseCodeDescription": "APPROVED - WITH BALANCES",
                "responseDetails": "51-B W/D purchase transfer",
                "status": "APPROVED",
                "tranCode": "012000",
                "tranId": "314003065381779",
                "transactionStatus": "APPROVED",
                "transactionType": "WITHDRAWAL",
                "debitOnly": {
                    "acquirerRefNum": "0000000000",
                    "amtCharged": "6471902.00",
                    "eciMastercard": "910",
                    "eciVisa": "7",
                    "expirationDateMismatch": false,
                    "journalDateTime": "2023-07-20T13:38:53Z",
                    "memberNumber": "0",
                    "merchantCategoryCode": "6011",
                    "merchantCity": "SAINT LOUIS",
                    "merchantName": "FLORIDA MEDICAL",
                    "merchantStateCode": "DC",
                    "messageType": "210- Auth/Completion",
                    "network": "000000 - Managed Service On US",
                    "pinTransaction": "1 - Signature Network with PIN",
                    "posDataInputCapability": "7 - Contactless chip",
                    "posDataInputMode": "2 - Swipe",
                    "preAuthAmt": "55.00",
                    "retrievalRefNumber": "222815000031",
                    "sequenceNumber": "000031",
                    "sub#### ResponseCode": "D",
                    "terminalId": "CATERMID",
                    "transactionAmount": "158.41",
                    "transactionDateTime": "2022-10-15T17:13:14Z",
                    "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
                    "unmatchedCompletionFlag": false
                }
            },
            "transactionDetails": {
                "acquiringId": "11100170",
                "applicationTranCounter": "00AF",
                "cardAcceptorId": "CARD ACCEPTOR",
                "cardEntryMode": "Swiped/Machine read",
                "cavvResult": "V",
                "cvResult": "Passed",
                "cvvResult": "Pass",
                "enfactNearTimeScore": "0479",
                "enfactRealTimeDecision": "Approve",
                "enfactRealTimeScore": "0243",
                "enfactRecommendation": "approve",
                "expirationDate": "12/30",
                "messageReasonCode": "2104",
                "networkScore": "10",
                "ruleManagerRecommendation": "Pass",
                "ruleManagerRuleName": "FastReplyGlobalRule",
                "settlementCurrencyCode": "840",
                "stateCode": "NJ",
                "systemAuditNumber": "106308",
                "terminalCountryCode": "USA",
                "transactionBlockerResult": "2 - Successful",
                "debitOnly": {
                    "acqPostDate": "16-DEC-2023 12:00:00 AM",
                    "atcResult": "Pass",
                    "avsResult": "A",
                    "camResult": "Valid",
                    "cardCountryCode": "USA",
                    "cardCounty": "840",
                    "cardholderAddress": "98104    706 5TH AVE S",
                    "cardLogo": "FOS3",
                    "cashbackAmount": "40.00",
                    "cvrResult": "03A01000",
                    "cvrResultStat": "Pass",
                    "cvv2Cvc2Result": true,
                    "depositType": "Cash",
                    "eCommerce": true,
                    "emvApplicationId": "A0000000046000",
                    "emvCard": true,
                    "emvCardSequence": "004",
                    "emvFallback": true,
                    "emvTerminal": true,
                    "entryMode": "5 - Chip",
                    "fromAccount": "123456789",
                    "fromAccountType": "Checking",
                    "international": false,
                    "locAmt1": "6.55",
                    "locAmt2": "89.50",
                    "merchantAdviceCode": "01",
                    "merchantCountry": "USA",
                    "merchantId": "STARBUCKS STORE",
                    "mobileDenial": "05",
                    "offline": true,
                    "pinPresent": "1 - Signature Network with PIN",
                    "pointOfService": "014 - GENERIC",
                    "posDataCode": "52010120300C",
                    "posEntryMode": "620",
                    "productType": "ATM",
                    "recurringPaymentInd": "R",
                    "reversalCode": "10 - HARDWARE MALFUNCTION",
                    "secureEci": "02 - 3-D Secure authentication attempt no resp",                 
                    "surchargeAmount": "3.95",
                    "surchargeReservalAmount": "2.50",
                    "terminalLogo": "DSH4",
                    "terminalPinCapable": false,
                    "terminalStateCode": "NJ",
                    "terminalStreet": "11806 SHELBYVILLE RD",
                    "toAccount": "123456789",
                    "toAccountType": "Checking",
                    "token#### RequestorId": "50148904210",
                    "tokenTransaction": false,
                    "tokenType": "03",
                    "transactionNetAmount": "111.96",
                    "transactionSource": "E-COMMERCE",
                    "tvrResult": "0400040001",
                    "tvrResultStat": "Fail"
                }
            }
        }
    ]
}
```

### Search Transactions Using NTT and Detail Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=detail
```
{
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "count": 1,
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "transactions": [
    {
      "transactionSummary": {
        "authorizationCode": "000229",
        "responseCode": "912",
        "responseCodeDescription": "APPROVED - WITH BALANCES",
        "responseDetails": "51-B W/D purchase transfer",
        "status": "APPROVED",
        "tranCode": "012000",
        "tranId": "314003065381779",
        "transactionStatus": "APPROVED",
        "transactionType": "WITHDRAWAL",
        "debitOnly": {
          "acquirerRefNum": "0000000000",
          "amtCharged": "6471902.00",
          "eciMastercard": "910",
          "eciVisa": "7",
          "expirationDateMismatch": false,
          "journalDateTime": "2023-07-20T13:38:53Z",
          "memberNumber": "0",
          "merchantCategoryCode": "6011",
          "merchantCity": "SAINT LOUIS",
          "merchantName": "FLORIDA MEDICAL",
          "merchantStateCode": "DC",
          "messageType": "210- Auth/Completion",
          "network": "000000 - Managed Service On US",
          "pinTransaction": "1 - Signature Network with PIN",
          "posDataInputCapability": "7 - Contactless chip",
          "posDataInputMode": "2 - Swipe",
          "preAuthAmt": "55.00",
          "retrievalRefNumber": "222815000031",
          "sequenceNumber": "000031",
          "sub#### ResponseCode": "D",
          "terminalId": "CATERMID",
          "transactionAmount": "158.41",
          "transactionDateTime": "2021-10-15T17:13:14Z",
          "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
          "unmatchedCompletionFlag": false
        }
      },
      "transactionDetails": {
        "acquiringId": "11100170",
        "applicationTranCounter": "00AF",
        "cardAcceptorId": "CARD ACCEPTOR",
        "cardEntryMode": "Swiped/Machine read",
        "cavvResult": "V",
        "cvResult": "Passed",
        "cvvResult": "Pass",
        "enfactNearTimeScore": "0479",
        "enfactRealTimeDecision": "Approve",
        "enfactRealTimeScore": "0243",
        "enfactRecommendation": "approve",
        "expirationDate": "12/30",
        "messageReasonCode": "2104",
        "networkScore": "10",
        "ruleManagerRecommendation": "Pass",
        "ruleManagerRuleName": "FastReplyGlobalRule",
        "settlementCurrencyCode": "840",
        "stateCode": "NJ",
        "systemAuditNumber": "106308",
        "terminalCountryCode": "USA",
        "transactionBlockerResult": "2 - Successful",
        "debitOnly": {
          "acqPostDate": "16-DEC-2023 12:00:00 AM",
          "atcResult": "Pass",
          "avsResult": "A",
          "camResult": "Valid",
          "cardCountryCode": "USA",
          "cardCounty": "840",
          "cardholderAddress": "98104    706 5TH AVE S",
          "cardLogo": "FOS3",
          "cashbackAmount": "40.00",
          "cvrResult": "03A01000",
          "cvrResultStat": "Pass",
          "cvv2Cvc2Result": true,
          "depositType": "Cash",
          "eCommerce": true,
          "emvApplicationId": "A0000000046000",
          "emvCard": true,
          "emvCardSequence": "004",
          "emvFallback": true,
          "emvTerminal": true,
          "entryMode": "5 - Chip",
          "fromAccount": "123456789",
          "fromAccountType": "Checking",
          "international": false,
          "locAmt1": "6.55",
          "locAmt2": "89.50",
          "merchantAdviceCode": "01",
          "merchantCountry": "USA",
          "merchantId": "STARBUCKS STORE",
          "mobileDenial": "05",
          "offline": true,
          "pinPresent": "1 - Signature Network with PIN",
          "pointOfService": "014 - GENERIC",
          "posDataCode": "52010120300C",
          "posEntryMode": "620",
          "productType": "ATM",
          "recurringPaymentInd": "R",
          "reversalCode": "10 - HARDWARE MALFUNCTION",
          "secureEci": "02 - 3-D Secure authentication attempt no resp",
          "surchargeAmount": "3.95",
          "surchargeReservalAmount": "2.50",
          "terminalLogo": "DSH4",
          "terminalPinCapable": false,
          "terminalStateCode": "NJ",
          "terminalStreet": "11806 SHELBYVILLE RD",
          "toAccount": "123456789",
          "toAccountType": "Checking",
          "token#### RequestorId": "50148904210",
          "tokenTransaction": false,
          "tokenType": "03",
          "transactionNetAmount": "111.96",
          "transactionSource": "E-COMMERCE",
          "tvrResult": "0400040001",
          "tvrResultStat": "Fail"
        }
      }
    }
  ]
}
```

### Search Transactions Using NTT and Summary Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "transactions": [
        {
          "transactionSummary": {
             "authorizationCode": "000229",
             "responseCode": "912",
             "responseCodeDescription": "APPROVED - WITH BALANCES",
             "responseDetails": "51-B W/D purchase transfer",
             "status": "APPROVED",
             "tranCode": "012000",
             "tranId": "314003065381779",
             "transactionStatus": "APPROVED",
             "transactionType": "WITHDRAWAL",
             "debitOnly": {
               "acquirerRefNum": "0000000000",
               "amtCharged": "6471902.00",
               "eciMastercard": "910",
               "eciVisa": "7",
               "expirationDateMismatch": false,
               "journalDateTime": "2023-07-20T13:38:53Z",
               "memberNumber": "0",
               "merchantCategoryCode": "6011",
               "merchantCity": "SAINT LOUIS",
               "merchantName": "FLORIDA MEDICAL",
               "merchantStateCode": "DC",
               "messageType": "210- Auth/Completion",
               "network": "000000 - Managed Service On US",
               "pinTransaction": "1 - Signature Network with PIN",
               "posDataInputCapability": "7 - Contactless chip",
               "posDataInputMode": "2 - Swipe",
               "preAuthAmt": "55.00",
               "retrievalRefNumber": "222815000031",
               "sequenceNumber": "000031",
               "sub#### ResponseCode": "D",
               "terminalId": "CATERMID",
               "transactionAmount": "158.41",
               "transactionDateTime": "2021-10-15T17:13:14Z",
               "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
               "unmatchedCompletionFlag": false
             }
           }
        }
    ]
}
```

### Search Transactions Using NTT Only and Detail Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=detail
```
{
    "nonTransToken": "piUVBJKZGfks4000",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "count": 1,
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "transactions": [
    {
      "transactionSummary": {
        "authorizationCode": "000229",
        "responseCode": "912",
        "responseCodeDescription": "APPROVED - WITH BALANCES",
        "responseDetails": "51-B W/D purchase transfer",
        "status": "APPROVED",
        "tranCode": "012000",
        "tranId": "314003065381779",
        "transactionStatus": "APPROVED",
        "transactionType": "WITHDRAWAL",
        "debitOnly": {
          "acquirerRefNum": "0000000000",
          "amtCharged": "6471902.00",
          "eciMastercard": "910",
          "eciVisa": "7",
          "expirationDateMismatch": false,
          "journalDateTime": "2023-07-20T13:38:53Z",
          "memberNumber": "0",
          "merchantCategoryCode": "6011",
          "merchantCity": "SAINT LOUIS",
          "merchantName": "FLORIDA MEDICAL",
          "merchantStateCode": "DC",
          "messageType": "210- Auth/Completion",
          "network": "000000 - Managed Service On US",
          "pinTransaction": "1 - Signature Network with PIN",
          "posDataInputCapability": "7 - Contactless chip",
          "posDataInputMode": "2 - Swipe",
          "preAuthAmt": "55.00",
          "retrievalRefNumber": "222815000031",
          "sequenceNumber": "000031",
          "sub#### ResponseCode": "D",
          "terminalId": "CATERMID",
          "transactionAmount": "158.41",
          "transactionDateTime": "2021-10-15T17:13:14Z",
          "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
          "unmatchedCompletionFlag": false
        }
      },
      "transactionDetails": {
        "acquiringId": "11100170",
        "applicationTranCounter": "00AF",
        "cardAcceptorId": "CARD ACCEPTOR",
        "cardEntryMode": "Swiped/Machine read",
        "cavvResult": "V",
        "cvResult": "Passed",
        "cvvResult": "Pass",
        "enfactNearTimeScore": "0479",
        "enfactRealTimeDecision": "Approve",
        "enfactRealTimeScore": "0243",
        "enfactRecommendation": "approve",
        "expirationDate": "12/30",
        "messageReasonCode": "2104",
        "networkScore": "10",
        "ruleManagerRecommendation": "Pass",
        "ruleManagerRuleName": "FastReplyGlobalRule",
        "settlementCurrencyCode": "840",
        "stateCode": "NJ",
        "systemAuditNumber": "106308",
        "terminalCountryCode": "USA",
        "transactionBlockerResult": "2 - Successful",
        "debitOnly": {
          "acqPostDate": "16-DEC-2023 12:00:00 AM",
          "atcResult": "Pass",
          "avsResult": "A",
          "camResult": "Valid",
          "cardCountryCode": "USA",
          "cardCounty": "840",
          "cardholderAddress": "98104    706 5TH AVE S",
          "cardLogo": "FOS3",
          "cashbackAmount": "40.00",
          "cvrResult": "03A01000",
          "cvrResultStat": "Pass",
          "cvv2Cvc2Result": true,
          "depositType": "Cash",
          "eCommerce": true,
          "emvApplicationId": "A0000000046000",
          "emvCard": true,
          "emvCardSequence": "004",
          "emvFallback": true,
          "emvTerminal": true,
          "entryMode": "5 - Chip",
          "fromAccount": "123456789",
          "fromAccountType": "Checking",
          "international": false,
          "locAmt1": "6.55",
          "locAmt2": "89.50",
          "merchantAdviceCode": "01",
          "merchantCountry": "USA",
          "merchantId": "STARBUCKS STORE",
          "mobileDenial": "05",
          "offline": true,
          "pinPresent": "1 - Signature Network with PIN",
          "pointOfService": "014 - GENERIC",
          "posDataCode": "52010120300C",
          "posEntryMode": "620",
          "productType": "ATM",
          "recurringPaymentInd": "R",
          "reversalCode": "10 - HARDWARE MALFUNCTION",
          "secureEci": "02 - 3-D Secure authentication attempt no resp",          
          "surchargeAmount": "3.95",
          "surchargeReservalAmount": "2.50",
          "terminalLogo": "DSH4",
          "terminalPinCapable": false,
          "terminalStateCode": "NJ",
          "terminalStreet": "11806 SHELBYVILLE RD",
          "toAccount": "123456789",
          "toAccountType": "Checking",
          "token#### RequestorId": "50148904210",
          "tokenTransaction": false,
          "tokenType": "03",
          "transactionNetAmount": "111.96",
          "transactionSource": "E-COMMERCE",
          "tvrResult": "0400040001",
          "tvrResultStat": "Fail"
        }
      }
    }
  ]
}
```

### Search Transactions Using Sequence Number, Retrieval Number, Detail Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=detail
```
{
    "cardNumber": "4000200030004000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "SEQUENCE_NUMBER",
            "filterValue": "000031"
        },
        {
            "filterBy": "RETRIEVAL_REF_NUMBER",
            "filterValue": "222815000031"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "count": 1,
  "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "transactions": [
    {
      "transactionSummary": {
        "authorizationCode": "000229",
        "responseCode": "912",
        "responseCodeDescription": "APPROVED - WITH BALANCES",
        "responseDetails": "51-B W/D purchase transfer",
        "status": "APPROVED",
        "tranCode": "012000",
        "tranId": "314003065381779",
        "transactionStatus": "APPROVED",
        "transactionType": "WITHDRAWAL",
        "debitOnly": {
          "acquirerRefNum": "0000000000",
          "amtCharged": "6471902.00",
          "eciMastercard": "910",
          "eciVisa": "7",
          "expirationDateMismatch": false,
          "journalDateTime": "2023-07-20T13:38:53Z",
          "memberNumber": "0",
          "merchantCategoryCode": "6011",
          "merchantCity": "SAINT LOUIS",
          "merchantName": "FLORIDA MEDICAL",
          "merchantStateCode": "DC",
          "messageType": "210- Auth/Completion",
          "network": "000000 - Managed Service On US",
          "pinTransaction": "1 - Signature Network with PIN",
          "posDataInputCapability": "7 - Contactless chip",
          "posDataInputMode": "2 - Swipe",
          "preAuthAmt": "55.00",
          "retrievalRefNumber": "222815000031",
          "sequenceNumber": "000031",
          "sub#### ResponseCode": "D",
          "terminalId": "CATERMID",
          "transactionAmount": "158.41",
          "transactionDateTime": "2021-10-15T17:13:14Z",
          "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
          "unmatchedCompletionFlag": false
        }
      },
      "transactionDetails": {
        "acquiringId": "11100170",
        "applicationTranCounter": "00AF",
        "cardAcceptorId": "CARD ACCEPTOR",
        "cardEntryMode": "Swiped/Machine read",
        "cavvResult": "V",
        "cvResult": "Passed",
        "cvvResult": "Pass",
        "enfactNearTimeScore": "0479",
        "enfactRealTimeDecision": "Approve",
        "enfactRealTimeScore": "0243",
        "enfactRecommendation": "approve",
        "expirationDate": "12/30",
        "messageReasonCode": "2104",
        "networkScore": "10",
        "ruleManagerRecommendation": "Pass",
        "ruleManagerRuleName": "FastReplyGlobalRule",
        "settlementCurrencyCode": "840",
        "stateCode": "NJ",
        "systemAuditNumber": "106308",
        "terminalCountryCode": "USA",
        "transactionBlockerResult": "2 - Successful",
        "debitOnly": {
          "acqPostDate": "16-DEC-2023 12:00:00 AM",
          "atcResult": "Pass",
          "avsResult": "A",
          "camResult": "Valid",
          "cardCountryCode": "USA",
          "cardCounty": "840",
          "cardholderAddress": "98104    706 5TH AVE S",
          "cardLogo": "FOS3",
          "cashbackAmount": "40.00",
          "cvrResult": "03A01000",
          "cvrResultStat": "Pass",
          "cvv2Cvc2Result": true,
          "depositType": "Cash",
          "eCommerce": true,
          "emvApplicationId": "A0000000046000",
          "emvCard": true,
          "emvCardSequence": "004",
          "emvFallback": true,
          "emvTerminal": true,
          "entryMode": "5 - Chip",
          "fromAccount": "123456789",
          "fromAccountType": "Checking",
          "international": false,
          "locAmt1": "6.55",
          "locAmt2": "89.50",
          "merchantAdviceCode": "01",
          "merchantCountry": "USA",
          "merchantId": "STARBUCKS STORE",
          "mobileDenial": "05",
          "offline": true,
          "pinPresent": "1 - Signature Network with PIN",
          "pointOfService": "014 - GENERIC",
          "posDataCode": "52010120300C",
          "posEntryMode": "620",
          "productType": "ATM",
          "recurringPaymentInd": "R",
          "reversalCode": "10 - HARDWARE MALFUNCTION",
          "secureEci": "02 - 3-D Secure authentication attempt no resp",
          "surchargeAmount": "3.95",
          "surchargeReservalAmount": "2.50",
          "terminalLogo": "DSH4",
          "terminalPinCapable": false,
          "terminalStateCode": "NJ",
          "terminalStreet": "11806 SHELBYVILLE RD",
          "toAccount": "123456789",
          "toAccountType": "Checking",
          "token#### RequestorId": "50148904210",
          "tokenTransaction": false,
          "tokenType": "03",
          "transactionNetAmount": "111.96",
          "transactionSource": "E-COMMERCE",
          "tvrResult": "0400040001",
          "tvrResultStat": "Fail"
        }
      }
    }
  ]
}
```

### Search Transactions Using Sequence Number, Retrieval Number, Summary Filter

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "SEQUENCE_NUMBER",
            "filterValue": "000031"
        },
        {
            "filterBy": "RETRIEVAL_REF_NUMBER",
            "filterValue": "222815000031"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "transactions": [
        {
          "transactionSummary": {
             "authorizationCode": "000229",
             "responseCode": "912",
             "responseCodeDescription": "APPROVED - WITH BALANCES",
             "responseDetails": "51-B W/D purchase transfer",
             "status": "APPROVED",
             "tranCode": "012000",
             "tranId": "314003065381779",
             "transactionStatus": "APPROVED",
             "transactionType": "WITHDRAWAL",
             "debitOnly": {
               "acquirerRefNum": "0000000000",
               "amtCharged": "6471902.00",
               "eciMastercard": "910",
               "eciVisa": "7",
               "expirationDateMismatch": false,
               "journalDateTime": "2023-07-20T13:38:53Z",
               "memberNumber": "0",
               "merchantCategoryCode": "6011",
               "merchantCity": "SAINT LOUIS",
               "merchantName": "FLORIDA MEDICAL",
               "merchantStateCode": "DC",
               "messageType": "210- Auth/Completion",
               "network": "000000 - Managed Service On US",
               "pinTransaction": "1 - Signature Network with PIN",
               "posDataInputCapability": "7 - Contactless chip",
               "posDataInputMode": "2 - Swipe",
               "preAuthAmt": "55.00",
               "retrievalRefNumber": "222815000031",
               "sequenceNumber": "000031",
               "sub#### ResponseCode": "D",
               "terminalId": "CATERMID",
               "transactionAmount": "158.41",
               "transactionDateTime": "2021-10-15T17:13:14Z",
               "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
               "unmatchedCompletionFlag": false
             }
           }
        }
    ]
}
```




**Version 2**

**Credit**

**Search Tansactions**
### Using Card Number, NTT, Detail Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=detail
```
{
      "cardNumber": "4000200030004001",
      "nonTransToken": "pSAZIXCAXrAo4001",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-15"
          }
      ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "CREDIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4001",
            "transactionAmount": "20.00",
            "transactionCode": "964",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N",
            "creditOnly": {
                "postedTransactionDetails": {
                    "authorizationCode": "000000",
                    "cardholderAccountNumber": "443011000000018",
                    "detailTransactionIdentifier": "000000000000000",
                    "merchantCategoryCode": "00000",
                    "merchantNumber": "443011000000398",
                    "originalAuthAdjustmentAmount": "",
                    "postingDate": "2021-10-14",
                    "transactionAccountNumber": ""
                }
            }
        }
    ]
}
```
### Using Card Number, NTT, Merchant Name, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "filterCriteria": [
        {
            "filterBy": "MERCHANT_NAME",
            "filterValue": "STORE1"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "CREDIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4001",
            "transactionAmount": "20.00",
            "transactionCode": "964",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
### Using Card Number, NTT, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
      "cardNumber": "4000200030004001",
      "nonTransToken": "pSAZIXCAXrAo4001",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-14"
          }
      ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "CREDIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4001",
            "transactionAmount": "20.00",
            "transactionCode": "964",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
### Using Card Number, NTT, Transaction Code, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "filterCriteria": [
        {
            "filterBy": "TRANSACTION_CODE",
            "filterValue": "964"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "CREDIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4001",
            "transactionAmount": "20.00",
            "transactionCode": "964",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
### Using NTT and Detail Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=detail
```
{
      "nonTransToken": "pSAZIXCAXrAo4001",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-15"
          }
      ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "CREDIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4001",
            "transactionAmount": "20.00",
            "transactionCode": "964",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N",
            "creditOnly": {
                "postedTransactionDetails": {
                    "authorizationCode": "000000",
                    "cardholderAccountNumber": "443011000000018",
                    "detailTransactionIdentifier": "000000000000000",
                    "merchantCategoryCode": "00000",
                    "merchantNumber": "443011000000398",
                    "originalAuthAdjustmentAmount": "",
                    "postingDate": "2021-10-14",
                    "transactionAccountNumber": ""
                }
            }
        }
    ]
}
```
### Using NTT and Summary Filter
#### Request

**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
      "nonTransToken": "pSAZIXCAXrAo4001",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-14"
          }
      ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "CREDIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4001",
            "transactionAmount": "20.00",
            "transactionCode": "964",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```



**Version 2**

**Debit**

## Search Transactions
### Using Card Number Only and Detail Filter

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=detail
```
{
    "cardNumber": "4000200030004000",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N",
            "debitOnly": {
                "transactionDetails": {
                    "enteredExpirationDate": "1122",
                    "entryMode": "2 - Swip",
                    "international": "No",
                    "pinTransaction": "1 - Yes",
                    "settlementAmount": "1100.00",
                    "terminalCountryCode": "string",
                    "terminalPinCapable": "No",
                    "transactionfeeAmount": "20.00",
                    "generalDetails": {
                        "fromAccount": "00000000000000000000",
                        "fromAccountType": "Checking",
                        "journalDateTime": "2021-10-22T19:50:40Z",
                        "productType": "MRG",
                        "reversalCode": "No",
                        "toAccount": "0000000000000000000",
                        "toAccountType": "Checking",
                        "transactionType": "TRANSFER"
                    },
                    "amountDetails": {
                        "cashbackAmount": "0.00",
                        "surchargeAmount": "0.00",
                        "surchargeReservalAmount": "0.00",
                        "transactionNetAmount": "20.00"
                    },
                    "networkInfo": {
                        "authorizationCode": "000227",
                        "network": "655100 - Mastercard Credit - Affiliate Member",
                        "sequenceNumber": "001668"
                    },
                    "tokenAndEmvInfo": {
                        "emvCard": "Yes",
                        "emvFallback": "N/A",
                        "emvTerminal": "Yes",
                        "tokenTransaction": "No"
                    },
                    "acquirerInfo": {
                        "merchantCategoryCode": "5541",
                        "merchantCountry": "USA",
                        "merchantId": "PARAGON APPLICAT",
                        "merchantName": "PARAGON APPLICATION",
                        "pointOfService": "002 - ON-PREMISE",
                        "terminalCityAndState": "NY",
                        "terminalId": "PREPINND",
                        "terminalStreet": "PARAGON APPLICAT"
                    }
                }
            }
        }
    ]
}
```
### Using Card Number, NTT, Amount, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "AMOUNT_FROM",
            "filterValue": "0.0"
        },
		{
            "filterBy": "AMOUNT_TO",
            "filterValue": "20.0"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
### Using Card Number, NTT, Detail Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=detail
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N",
            "debitOnly": {
                "transactionDetails": {
                    "enteredExpirationDate": "1122",
                    "entryMode": "2 - Swip",
                    "international": "No",
                    "pinTransaction": "1 - Yes",
                    "settlementAmount": "1100.00",
                    "terminalCountryCode": "string",
                    "terminalPinCapable": "No",
                    "transactionfeeAmount": "20.00",
                    "generalDetails": {
                        "fromAccount": "00000000000000000000",
                        "fromAccountType": "Checking",
                        "journalDateTime": "2021-10-22T19:50:40Z",
                        "productType": "MRG",
                        "reversalCode": "No",
                        "toAccount": "0000000000000000000",
                        "toAccountType": "Checking",
                        "transactionType": "TRANSFER"
                    },
                    "amountDetails": {
                        "cashbackAmount": "0.00",
                        "surchargeAmount": "0.00",
                        "surchargeReservalAmount": "0.00",
                        "transactionNetAmount": "20.00"
                    },
                    "networkInfo": {
                        "authorizationCode": "000227",
                        "network": "655100 - Mastercard Credit - Affiliate Member",
                        "sequenceNumber": "001668"
                    },
                    "tokenAndEmvInfo": {
                        "emvCard": "Yes",
                        "emvFallback": "N/A",
                        "emvTerminal": "Yes",
                        "tokenTransaction": "No"
                    },
                    "acquirerInfo": {
                        "merchantCategoryCode": "5541",
                        "merchantCountry": "USA",
                        "merchantId": "PARAGON APPLICAT",
                        "merchantName": "PARAGON APPLICATION",
                        "pointOfService": "002 - ON-PREMISE",
                        "terminalCityAndState": "NY",
                        "terminalId": "PREPINND",
                        "terminalStreet": "PARAGON APPLICAT"
                    }
                }
            }
        }
    ]
}
```
### Using Card Number, NTT, Merchant Name, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "MERCHANT_NAME",
            "filterValue": "STORE1"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
### Using Card Number, NTT, Message Type, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "MESSAGE_TYPE",
            "filterValue": "210- Auth/Completion"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
### Using Card Number, NTT, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-24"
          }
      ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
### Using Card Number, NTT, Transaction Code, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
	"memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "TRANSACTION_CODE",
            "filterValue": "961"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
### Using NTT and Detail Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=detail
```
{
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N",
            "debitOnly": {
                "transactionDetails": {
                    "enteredExpirationDate": "1122",
                    "entryMode": "2 - Swip",
                    "international": "No",
                    "pinTransaction": "1 - Yes",
                    "settlementAmount": "1100.00",
                    "terminalCountryCode": "string",
                    "terminalPinCapable": "No",
                    "transactionfeeAmount": "20.00",
                    "generalDetails": {
                        "fromAccount": "00000000000000000000",
                        "fromAccountType": "Checking",
                        "journalDateTime": "2021-10-22T19:50:40Z",
                        "productType": "MRG",
                        "reversalCode": "No",
                        "toAccount": "0000000000000000000",
                        "toAccountType": "Checking",
                        "transactionType": "TRANSFER"
                    },
                    "amountDetails": {
                        "cashbackAmount": "0.00",
                        "surchargeAmount": "0.00",
                        "surchargeReservalAmount": "0.00",
                        "transactionNetAmount": "20.00"
                    },
                    "networkInfo": {
                        "authorizationCode": "000227",
                        "network": "655100 - Mastercard Credit - Affiliate Member",
                        "sequenceNumber": "001668"
                    },
                    "tokenAndEmvInfo": {
                        "emvCard": "Yes",
                        "emvFallback": "N/A",
                        "emvTerminal": "Yes",
                        "tokenTransaction": "No"
                    },
                    "acquirerInfo": {
                        "merchantCategoryCode": "5541",
                        "merchantCountry": "USA",
                        "merchantId": "PARAGON APPLICAT",
                        "merchantName": "PARAGON APPLICATION",
                        "pointOfService": "002 - ON-PREMISE",
                        "terminalCityAndState": "NY",
                        "terminalId": "PREPINND",
                        "terminalStreet": "PARAGON APPLICAT"
                    }
                }
            }
        }
    ]
}
```
### Using NTT Only and Detail Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=detail
```
{
    "nonTransToken": "piUVBJKZGfks4000",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
H**TTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N",
            "debitOnly": {
                "transactionDetails": {
                    "enteredExpirationDate": "1122",
                    "entryMode": "2 - Swip",
                    "international": "No",
                    "pinTransaction": "1 - Yes",
                    "settlementAmount": "1100.00",
                    "terminalCountryCode": "string",
                    "terminalPinCapable": "No",
                    "transactionfeeAmount": "20.00",
                    "generalDetails": {
                        "fromAccount": "00000000000000000000",
                        "fromAccountType": "Checking",
                        "journalDateTime": "2021-10-22T19:50:40Z",
                        "productType": "MRG",
                        "reversalCode": "No",
                        "toAccount": "0000000000000000000",
                        "toAccountType": "Checking",
                        "transactionType": "TRANSFER"
                    },
                    "amountDetails": {
                        "cashbackAmount": "0.00",
                        "surchargeAmount": "0.00",
                        "surchargeReservalAmount": "0.00",
                        "transactionNetAmount": "20.00"
                    },
                    "networkInfo": {
                        "authorizationCode": "000227",
                        "network": "655100 - Mastercard Credit - Affiliate Member",
                        "sequenceNumber": "001668"
                    },
                    "tokenAndEmvInfo": {
                        "emvCard": "Yes",
                        "emvFallback": "N/A",
                        "emvTerminal": "Yes",
                        "tokenTransaction": "No"
                    },
                    "acquirerInfo": {
                        "merchantCategoryCode": "5541",
                        "merchantCountry": "USA",
                        "merchantId": "PARAGON APPLICAT",
                        "merchantName": "PARAGON APPLICATION",
                        "pointOfService": "002 - ON-PREMISE",
                        "terminalCityAndState": "NY",
                        "terminalId": "PREPINND",
                        "terminalStreet": "PARAGON APPLICAT"
                    }
                }
            }
        }
    ]
}
```
### Using NTT and Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2021-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
### Using Detail Filter NSF
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=detail
```
{
    "cardNumber": "4000200030004000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-09-10"
        },
        {
            "filterBy": "TO_DATE",
            "filterValue": "2022-10-24"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 2,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "ABC Fitness",
            "merchantState": "NJ",
            "messageType": "110 - Preauthorization",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "551",
            "responseCodeDescription": "INSUFFICIENT FUNDS (NO BALANCE AVAILABLE)",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2022-10-22T19:50:40Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "TRANSFER",
            "unmatchedCompletionFlag": "N",
            "debitOnly": {
                "transactionDetails": {
                    "enteredExpirationDate": "1122",
                    "entryMode": "2 - Swipe",
                    "pinTransaction": "4 - Yes",
                    "settlementAmount": "1100.00",
                    "settlementConversionRate": "",
                    "settlementCurrencyCode": "",
                    "terminalPinCapable": "No",
                    "transactionfeeAmount": "20.00",
                    "generalDetails": {
                        "fromAccount": "00000000000000000000",
                        "fromAccountType": "Checking",
                        "journalDateTime": "2021-10-22T19:50:40Z",
                        "productType": "MRG",
                        "reversalCode": "No",
                        "toAccount": "00000000000000000000",
                        "toAccountType": "Checking",
                        "transactionType": "Payment"
                    },
                    "amountDetails": {
                        "cashbackAmount": "0.00",
                        "surchargeAmount": "0.00",
                        "surchargeReservalAmount": "0.00",
                        "transactionNetAmount": "20.00"
                    },
                    "networkInfo": {
                        "authorizationCode": "000000",
                        "network": "487000 - null",
                        "sequenceNumber": "000031"
                    },
                    "tokenAndEmvInfo": {
                        "emvCard": "Yes",
                        "emvFallback": "N/A",
                        "emvTerminal": "Yes",
                        "tokenTransaction": "No"
                    },
                    "acquirerInfo": {
                        "merchantCategoryCode": "0000",
                        "merchantCountry": "USA",
                        "merchantId": "ABC Fitness",
                        "merchantName": "ABC Fitness",
                        "pointOfService": "002 - ON-PREMISE",
                        "terminalCityAndState": "5533 0472, NY ",
                        "terminalId": "25589705 - POS",
                        "terminalStreet": "24 W MAIN ST"
                    }
                }
            }
        },
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "QDH4",
            "merchantState": "NJ",
            "messageType": "210 - Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "092",
            "responseCodeDescription": "NETWORK NOT FOUND",
            "retrievalRefNumber": "222815000029",
            "sequenceNumber": "000029",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2021-10-22T18:11:41Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "TRANSFER",
            "unmatchedCompletionFlag": "N",
            "debitOnly": {
                "memberNumber": "0",
                "transactionDetails": {
                    "enteredExpirationDate": "1122",
                    "entryMode": "2 - Swipe",
                    "international": "Yes",
                    "pinTransaction": "4 - Yes",
                    "settlementAmount": "1100.00",
                    "terminalPinCapable": "No",
                    "transactionfeeAmount": "20.00",
                    "generalDetails": {
                        "fromAccount": "00000000000000000000",
                        "fromAccountType": "Checking",
                        "journalDateTime": "2021-10-22T18:11:41Z",
                        "productType": "MRG",
                        "reversalCode": "No",
                        "toAccount": "00000000000000000000",
                        "toAccountType": "Checking",
                        "transactionType": "TRANSFER"
                    },
                    "amountDetails": {
                        "cashbackAmount": "0.00",
                        "surchargeAmount": "0.00",
                        "surchargeReservalAmount": "0.00",
                        "transactionNetAmount": "20.00"
                    },
                    "networkInfo": {
                        "authorizationCode": "000000",
                        "network": "487000 - null",
                        "secureEci": "",
                        "sequenceNumber": "000029"
                    },
                    "tokenAndEmvInfo": {
                        "emvCard": "Yes",
                        "emvFallback": "N/A",
                        "emvTerminal": "Yes",
                        "tokenTransaction": "No"
                    },
                    "acquirerInfo": {
                        "merchantCategoryCode": "0000",
                        "merchantCountry": "USA",
                        "merchantId": "QDH4",
                        "merchantName": "QDH4",
                        "pointOfService": "002 - ON-PREMISE",
                        "terminalCityAndState": "5533 0472, NY ",
                        "terminalId": "MSDIEBVK",
                        "terminalStreet": "24 W MAIN ST"
                    }
                }
            }
        }
    ]
}
```
### Using Sequence Number, Retrieval Number, Detail Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=detail
```
{
    "cardNumber": "4000200030004000",
    "memberNumber": "0",
    "filterCriteria": [
        {
            "filterBy": "SEQUENCE_NUMBER",
            "filterValue": "000031"
        },
        {
            "filterBy": "RETRIEVAL_REF_NUMBER",
            "filterValue": "222815000031"
        }
    ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "STORE1",
            "merchantState": "NJ",
            "messageType": "210- Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "000",
            "responseCodeDescription": "APPROVED - NO BALANCES",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2023-05-23T07:30:02Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "WITHDRAWAL",
            "unmatchedCompletionFlag": "N",
            "debitOnly": {
                "transactionDetails": {
                    "enteredExpirationDate": "1122",
                    "entryMode": "2 - Swip",
                    "international": "No",
                    "pinTransaction": "1 - Yes",
                    "settlementAmount": "1100.00",
                    "terminalCountryCode": "string",
                    "terminalPinCapable": "No",
                    "transactionfeeAmount": "20.00",
                    "generalDetails": {
                        "fromAccount": "00000000000000000000",
                        "fromAccountType": "Checking",
                        "journalDateTime": "2021-10-22T19:50:40Z",
                        "productType": "MRG",
                        "reversalCode": "No",
                        "toAccount": "0000000000000000000",
                        "toAccountType": "Checking",
                        "transactionType": "TRANSFER"
                    },
                    "amountDetails": {
                        "cashbackAmount": "0.00",
                        "surchargeAmount": "0.00",
                        "surchargeReservalAmount": "0.00",
                        "transactionNetAmount": "20.00"
                    },
                    "networkInfo": {
                        "authorizationCode": "000227",
                        "network": "655100 - Mastercard Credit - Affiliate Member",
                        "sequenceNumber": "001668"
                    },
                    "tokenAndEmvInfo": {
                        "emvCard": "Yes",
                        "emvFallback": "N/A",
                        "emvTerminal": "Yes",
                        "tokenTransaction": "No"
                    },
                    "acquirerInfo": {
                        "merchantCategoryCode": "5541",
                        "merchantCountry": "USA",
                        "merchantId": "PARAGON APPLICAT",
                        "merchantName": "PARAGON APPLICATION",
                        "pointOfService": "002 - ON-PREMISE",
                        "terminalCityAndState": "NY",
                        "terminalId": "PREPINND",
                        "terminalStreet": "PARAGON APPLICAT"
                    }
                }
            }
        }
    ]
}
```

### Using Sequence Number, Retrieval Number, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/transactions/search?filter=summary
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "filterCriteria": [
          {
              "filterBy": "SEQUENCE_NUMBER",
              "filterValue": "000031"
          },
          {
              "filterBy": "RETRIEVAL_REF_NUMBER",
              "filterValue": "222815000031"
          }
      ]
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "count": 1,
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "transactions": [
        {
            "acquirerRefNum": "222815000031",
            "amtCharged": "0.00",
            "authorizationCode": "000000",
            "cardType": "DEBIT",
            "eciMastercard": "3",
            "eciVisa": "3",
            "effectiveDate": "2023-05-28",
            "expirationDateMismatch": "N",
            "merchantCategoryCode": "0000",
            "merchantCity": "MORRIS PLAINS",
            "merchantName": "Test123",
            "merchantState": "NJ",
            "messageType": "210 - Auth/Completion",
            "networkID": "773002 - Maestro",
            "pinTransaction": "1 - Yes",
            "posDataInputCapability": "2",
            "posDataInputMode": "2 - Swipe",
            "preAuthAmt": "1.00",
            "responseCode": "096",
            "responseCodeDescription": "SYSTEM MALFUNCTION",
            "retrievalRefNumber": "222815000031",
            "sequenceNumber": "000031",
            "statusDescription": "64-PI LOST",
            "sub#### ResponseCode": "M",
            "sub#### ResponseCodeDescription": "96-M Error processing PIN",
            "terminalId": "VMDHDB03",
            "transactedCardNumber": "400020XXXXXX4000",
            "transactionAmount": "20.00",
            "transactionCode": "961",
            "transactionDateTime": "2021-10-22T19:50:40Z",
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}",
            "transactionStatus": "APPROVED",
            "transactionType": "TRANSFER",
            "unmatchedCompletionFlag": "N"
        }
    ]
}
```
**Version 1**

**Credit**

## Search Transactions
### Using Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/transactions/search?filter=summary
```
{
      "cardNumber": "4000100020003000",
      "memberNumber": "1",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-07-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-14"
          }
      ]
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "count": 2,
      "transactions": [
          {
              "transactionDateTime": "2021-09-14T05:00:00Z",
              "merchantName": "LATE FEE",
              "transactionAmount": "29.00",
              "transactionType": "Late Charge",
              "transactionStatus": "POSTED"
          },
          {
              "transactionDateTime": "2021-07-14T05:00:00Z",
              "merchantName": "Interest Charge on Cash A",
              "transactionAmount": "6.73",
              "transactionType": "Cash Advance Finance Charge",
              "transactionStatus": "POSTED"
          }
      ]
  }
```
### Using Detail Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/transactions/search?filter=detail
```
{
      "cardNumber": "4000100020003000",
      "memberNumber": "1",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-15"
          }
      ]
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "count": 2,
      "transactions": [
          {
              "transactionDateTime": "2021-10-14T06:00:00Z",
              "merchantName": "LATE FEE",
              "transactionAmount": "29.00",
              "transactionType": "Late Charge",
              "transactionStatus": "POSTED",
              "postedTransactionDetails": {
                  "cardholderAccountNumber": "123456789",
                  "transactionDescription": "LATE FEE",
                  "postingDate": "2021-10-14",
                  "detailTransactionIdentifier": "000000000000000",
                  "merchantCategoryCode": "00000",
                  "transactionCode": "961"
              }
          },
          {
              "transactionDateTime": "2021-09-14T05:00:00Z",
              "merchantName": "FRSTNECN022 ALBIN",
              "transactionAmount": "0.00",
              "transactionType": "Finance Charge (item charge)",
              "transactionStatus": "POSTED",
              "postedTransactionDetails": {
                  "cardholderAccountNumber": "123456789",
                  "transactionDescription": "FRSTNECN022 ALBIN",
                  "postingDate": "2021-09-14",
                  "detailTransactionIdentifier": "000000000000000",
                  "merchantCategoryCode": "00000",
                  "transactionCode": "900"
              }
          }
      ]
  }
```
**Debit**

**Search Transactions**
### Using Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/transactions/search?filter=summary
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-24"
          }
      ]
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "count": 2,
      "transactions": [
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "retrievalRefNumber": "222815000031",
              "sequenceNumber": "000031",
              "sub#### ResponseCode": "M",
              "sub#### ResponseCodeDescription": "96-M Error processing PIN",
              "preAuthAmt": "2000",
              "amtCharged": "0",
              "authorizationCode": "000000",
              "terminalId": "VMDHDB03",
              "merchantCategoryCode": "0000",
              "eciVisa": " ",
              "pinTransaction": "4 - Yes",
              "networkID": "    ",
              "acquirerRefNum": "0000000000",
              "posDataInputCapability": "5",
              "posDataInputMode": "2 - Swipe",
              "unmatchedCompletionFlag": " ",
              "expirationDateMismatch": "N",
              "transactionDateTime": "2021-10-22T19:50:40Z",
              "merchantName": "Test123         ",
              "transactionAmount": "2000",
              "transactionType": "402020",
              "messageType": "210 - Auth/Completion",
              "transactionStatus": "96",
              "responseCode": "096",
              "responseCodeDescription": "SYSTEM MALFUNCTION"
          },
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "retrievalRefNumber": "222815000029",
              "sequenceNumber": "000029",
              "sub#### ResponseCode": "B",
              "preAuthAmt": "2000",
              "amtCharged": "0",
              "authorizationCode": "000000",
              "terminalId": "MSDIEBVK",
              "merchantCategoryCode": "0000",
              "eciVisa": " ",
              "pinTransaction": "4 - Yes",
              "networkID": "    ",
              "acquirerRefNum": "0000000000",
              "posDataInputCapability": "5",
              "posDataInputMode": "2 - Swipe",
              "unmatchedCompletionFlag": " ",
              "expirationDateMismatch": "N",
              "transactionDateTime": "2021-10-22T18:11:41Z",
              "merchantName": "QDH4            ",
              "transactionAmount": "2000",
              "transactionType": "402020",
              "messageType": "210 - Auth/Completion",
              "transactionStatus": "92",
              "responseCode": "092",
              "responseCodeDescription": "NETWORK NOT FOUND"
          }
      ]
  }
```
### Using Detail Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/transactions/search?filter=detail
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2021-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2021-10-24"
          }
      ]
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "count": 2,
      "transactions": [
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "sequenceNumber": "000031",
              "retrievalRefNumber": "222815000031",
              "transactionDateTime": "2021-10-22T19:50:40Z",
              "merchantName": "Test123",
              "transactionAmount": "20.00",
              "transactionType": "TRANSFER",
              "messageType": "210 - Auth/Completion",
              "responseCode": "096",
              "responseCodeDescription": "SYSTEM MALFUNCTION",
              "transactionDetails": {
                  "entryMode": "2 - Swipe",
                  "pinTransaction": "4 - Yes",
                  "terminalPinCapable": "No",
                  "international": "Yes",
                  "generalDetails": {
                      "journalDateTime": "2021-10-22T19:50:40Z",
                      "reversalCode": "No",
                      "toAccountType": "Checking",
                      "toAccount": "00000000000000000000",
                      "fromAccountType": "Checking",
                      "fromAccount": "00000000000000000000",
                      "transactionType": "TRANSFER"
                  },
                  "amountDetails": {
                      "transactionNetAmount": "20.00",
                      "cashbackAmount": "0.00",
                      "surchargeAmount": "0.00",
                      "surchargeReservalAmount": "0.00"
                  },
                  "networkInfo": {
                      "network": "487000 - null",
                      "authorizationCode": "000000",
                      "sequenceNumber": "000031"
                  },
                  "tokenAndEmvInfo": {
                      "tokenTransaction": "No",
                      "emvCard": "Yes",
                      "emvTerminal": "Yes",
                      "emvFallback": "N/A"
                  },
                  "acquirerInfo": {
                      "merchantName": "Test123",
                      "merchantId": "Test123",
                      "terminalId": "VMDHDB03",
                      "terminalStreet": "24 W MAIN ST",
                      "terminalCityAndState": "5533 0472, NY ",
                      "merchantCountry": "USA",
                      "merchantCategoryCode": "0000",
                      "pointOfService": "002 - ON-PREMISE"
                  }
              }
          },
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "sequenceNumber": "000029",
              "retrievalRefNumber": "222815000029",
              "transactionDateTime": "2021-10-22T18:11:41Z",
              "merchantName": "QDH4",
              "transactionAmount": "20.00",
              "transactionType": "TRANSFER",
              "messageType": "210 - Auth/Completion",
              "responseCode": "092",
              "responseCodeDescription": "NETWORK NOT FOUND",
              "transactionDetails": {
                  "entryMode": "2 - Swipe",
                  "pinTransaction": "4 - Yes",
                  "terminalPinCapable": "No",
                  "international": "Yes",
                  "generalDetails": {
                      "journalDateTime": "2021-10-22T18:11:41Z",
                      "reversalCode": "No",
                      "toAccountType": "Checking",
                      "toAccount": "00000000000000000000",
                      "fromAccountType": "Checking",
                      "fromAccount": "00000000000000000000",
                      "transactionType": "TRANSFER"
                  },
                  "amountDetails": {
                      "transactionNetAmount": "20.00",
                      "cashbackAmount": "0.00",
                      "surchargeAmount": "0.00",
                      "surchargeReservalAmount": "0.00"
                  },
                  "networkInfo": {
                      "network": "487000 - null",
                      "authorizationCode": "000000",
                      "sequenceNumber": "000029"
                  },
                  "tokenAndEmvInfo": {
                      "tokenTransaction": "No",
                      "emvCard": "Yes",
                      "emvTerminal": "Yes",
                      "emvFallback": "N/A"
                  },
                  "acquirerInfo": {
                      "merchantName": "QDH4",
                      "merchantId": "QDH4",
                      "terminalId": "MSDIEBVK",
                      "terminalStreet": "24 W MAIN ST",
                      "terminalCityAndState": "5533 0472, NY ",
                      "merchantCountry": "USA",
                      "merchantCategoryCode": "0000",
                      "pointOfService": "002 - ON-PREMISE"
                  }
              }
          }
      ]
  }
```
### Using Detail Filter NSF
Not Sufficient Funds

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/transactions/search?filter=detail
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "filterCriteria": [
          {
              "filterBy": "FROM_DATE",
              "filterValue": "2022-09-10"
          },
          {
              "filterBy": "TO_DATE",
              "filterValue": "2022-10-24"
          }
      ]
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "count": 2,
      "transactions": [
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "sequenceNumber": "000031",
              "retrievalRefNumber": "222815000031",
              "transactionDateTime": "2022-10-22T19:50:40Z",
              "merchantName": "ABC Fitness",
              "transactionAmount": "20.00",
              "transactionType": "Payment",
              "messageType": "110 - Preauthorization",
              "responseCode": "551",
              "responseCodeDescription": "INSUFFICIENT FUNDS (NO BALANCE AVAILABLE)",
              "transactionDetails": {
                  "entryMode": "2 - Swipe",
                  "pinTransaction": "4 - Yes",
                  "terminalPinCapable": "No",
                  "international": "Yes",
                  "generalDetails": {
                      "journalDateTime": "2022-10-22T19:50:40Z",
                      "reversalCode": "No",
                      "toAccountType": "Checking",
                      "toAccount": "00000000000000000000",
                      "fromAccountType": "Checking",
                      "fromAccount": "00000000000000000000",
                      "transactionType": "Payment"
                  },
                  "amountDetails": {
                      "transactionNetAmount": "20.00",
                      "cashbackAmount": "0.00",
                      "surchargeAmount": "0.00",
                      "surchargeReservalAmount": "0.00"
                  },
                  "networkInfo": {
                      "network": "487000 - null",
                      "authorizationCode": "000000",
                      "sequenceNumber": "000031"
                  },
                  "tokenAndEmvInfo": {
                      "tokenTransaction": "No",
                      "emvCard": "Yes",
                      "emvTerminal": "Yes",
                      "emvFallback": "N/A"
                  },
                  "acquirerInfo": {
                      "merchantName": "ABC Fitness",
                      "merchantId": "ABC Fitness",
                      "terminalId": "25589705 - POS",
                      "terminalStreet": "24 W MAIN ST",
                      "terminalCityAndState": "5533 0472, NY ",
                      "merchantCountry": "USA",
                      "merchantCategoryCode": "0000",
                      "pointOfService": "002 - ON-PREMISE"
                  }
              }
          },
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "sequenceNumber": "000029",
              "retrievalRefNumber": "222815000029",
              "transactionDateTime": "2022-10-22T18:11:41Z",
              "merchantName": "QDH4",
              "transactionAmount": "20.00",
              "transactionType": "TRANSFER",
              "messageType": "210 - Auth/Completion",
              "responseCode": "092",
              "responseCodeDescription": "NETWORK NOT FOUND",
              "transactionDetails": {
                  "entryMode": "2 - Swipe",
                  "pinTransaction": "4 - Yes",
                  "terminalPinCapable": "No",
                  "international": "Yes",
                  "generalDetails": {
                      "journalDateTime": "2022-10-22T18:11:41Z",
                      "reversalCode": "No",
                      "toAccountType": "Checking",
                      "toAccount": "00000000000000000000",
                      "fromAccountType": "Checking",
                      "fromAccount": "00000000000000000000",
                      "transactionType": "TRANSFER"
                  },
                  "amountDetails": {
                      "transactionNetAmount": "20.00",
                      "cashbackAmount": "0.00",
                      "surchargeAmount": "0.00",
                      "surchargeReservalAmount": "0.00"
                  },
                  "networkInfo": {
                      "network": "487000 - null",
                      "authorizationCode": "000000",
                      "sequenceNumber": "000029"
                  },
                  "tokenAndEmvInfo": {
                      "tokenTransaction": "No",
                      "emvCard": "Yes",
                      "emvTerminal": "Yes",
                      "emvFallback": "N/A"
                  },
                  "acquirerInfo": {
                      "merchantName": "QDH4",
                      "merchantId": "QDH4",
                      "terminalId": "MSDIEBVK",
                      "terminalStreet": "24 W MAIN ST",
                      "terminalCityAndState": "5533 0472, NY ",
                      "merchantCountry": "USA",
                      "merchantCategoryCode": "0000",
                      "pointOfService": "002 - ON-PREMISE"
                  }
              }
          }
      ]
  }
```
### Using Sequence Number, Retrieval Number, Summary Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/transactions/search?filter=summary
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "filterCriteria": [
          {
              "filterBy": "SEQUENCE_NUMBER",
              "filterValue": "000031"
          },
          {
              "filterBy": "RETRIEVAL_REF_NUMBER",
              "filterValue": "222815000031"
          }
      ]
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "count": 1,
      "transactions": [
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "retrievalRefNumber": "222815000031",
              "sequenceNumber": "000031",
              "sub#### ResponseCode": "M",
              "sub#### ResponseCodeDescription": "96-M Error processing PIN",
              "preAuthAmt": "2000",
              "amtCharged": "0",
              "authorizationCode": "000000",
              "terminalId": "VMDHDB03",
              "merchantCategoryCode": "0000",
              "eciVisa": " ",
              "pinTransaction": "4 - Yes",
              "networkID": "    ",
              "acquirerRefNum": "0000000000",
              "posDataInputCapability": "5",
              "posDataInputMode": "2 - Swipe",
              "unmatchedCompletionFlag": " ",
              "expirationDateMismatch": "N",
              "transactionDateTime": "2021-10-22T19:50:40Z",
              "merchantName": "Test123         ",
              "transactionAmount": "2000",
              "transactionType": "402020",
              "messageType": "210 - Auth/Completion",
              "transactionStatus": "96",
              "responseCode": "096",
              "responseCodeDescription": "SYSTEM MALFUNCTION"
          }
      ]
  }
```
### Using Sequence Number, Retrieval Number, Detail Filter
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/transactions/search?filter=detail
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "filterCriteria": [
          {
              "filterBy": "SEQUENCE_NUMBER",
              "filterValue": "000031"
          },
          {
              "filterBy": "RETRIEVAL_REF_NUMBER",
              "filterValue": "222815000031"
          }
      ]
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "count": 1,
      "transactions": [
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "sequenceNumber": "000031",
              "retrievalRefNumber": "222815000031",
              "transactionDateTime": "2021-10-22T19:50:40Z",
              "merchantName": "Test123",
              "transactionAmount": "20.00",
              "transactionType": "TRANSFER",
              "messageType": "210 - Auth/Completion",
              "responseCode": "096",
              "responseCodeDescription": "SYSTEM MALFUNCTION",
              "transactionDetails": {
                  "entryMode": "2 - Swipe",
                  "pinTransaction": "4 - Yes",
                  "terminalPinCapable": "No",
                  "international": "Yes",
                  "generalDetails": {
                      "journalDateTime": "2021-10-22T19:50:40Z",
                      "reversalCode": "No",
                      "toAccountType": "Checking",
                      "toAccount": "00000000000000000000",
                      "fromAccountType": "Checking",
                      "fromAccount": "00000000000000000000",
                      "transactionType": "TRANSFER"
                  },
                  "amountDetails": {
                      "transactionNetAmount": "20.00",
                      "cashbackAmount": "0.00",
                      "surchargeAmount": "0.00",
                      "surchargeReservalAmount": "0.00"
                  },
                  "networkInfo": {
                      "network": "487000 - null",
                      "authorizationCode": "000000",
                      "sequenceNumber": "000031"
                  },
                  "tokenAndEmvInfo": {
                      "tokenTransaction": "No",
                      "emvCard": "Yes",
                      "emvTerminal": "Yes",
                      "emvFallback": "N/A"
                  },
                  "acquirerInfo": {
                      "merchantName": "Test123",
                      "merchantId": "Test123",
                      "terminalId": "VMDHDB03",
                      "terminalStreet": "24 W MAIN ST",
                      "terminalCityAndState": "5533 0472, NY ",
                      "merchantCountry": "USA",
                      "merchantCategoryCode": "0000",
                      "pointOfService": "002 - ON-PREMISE"
                  }
              }
          }
      ]
  }
```
## Search for Terminal Transactions
### By Status
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/terminalTransactions/search
```
{
      "terminalId": "CATERMID",
      "filterCriteria": [
          {
              "filterBy": "STATUS",
              "filterValue": "Approved"
          }
      ]
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "count": 2,
      "transactions": [
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "1",
              "sequenceNumber": "003503",
              "sub#### ResponseCode": "K",
              "sub#### ResponseCodeDescription": "57-k Blocked for country code",
              "preAuthAmt": "1.00",
              "amtCharged": "0.00",
              "authorizationCode": "600636",
              "terminalId": "CATERMID",
              "merchantCategoryCode": "4112",
              "merchantCity": "Morris Plains",
              "merchantState": "NJ",
              "eciMastercard": "3",
              "eciVisa": "3",
              "pinTransaction": "1 - Yes",
              "networkID": "773002 - Maestro",
              "acquirerRefNum": "1055556060",
              "posDataInputCapability": "2",
              "posDataInputMode": "2 - Swipe",
              "unmatchedCompletionFlag": "N",
              "expirationDateMismatch": "N",
              "transactionDateTime": "2021-12-29T16:37:51Z",
              "merchantName": "HT02",
              "transactionAmount": "1.00",
              "transactionType": "PAYMENT TO MERCHANT",
              "messageType": "210 - Auth/Completion",
              "transactionStatus": "APPROVED",
              "responseCode": "00",
              "responseCodeDescription": "APPROVED - NO BALANCES",
              "terminalFILogo": "RM22",
              "cardFILogo": "V924",
              "terminalPinCapable": "No",
              "merchantCountry": "USA"
          },
          {
              "systemRecordId": "011103LMFI4F4321377761184|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "1",
              "sequenceNumber": "003487",
              "sub#### ResponseCode": "K",
              "sub#### ResponseCodeDescription": "57-k Blocked for country code",
              "preAuthAmt": "1.00",
              "amtCharged": "0.00",
              "authorizationCode": "600636",
              "terminalId": "CATERMID",
              "merchantCategoryCode": "4112",
              "merchantCity": "Morris Plains",
              "merchantState": "NJ",
              "eciMastercard": "3",
              "eciVisa": "3",
              "pinTransaction": "1 - Yes",
              "networkID": "773002 - Maestro",
              "acquirerRefNum": "1055556060",
              "posDataInputCapability": "2",
              "posDataInputMode": "2 - Swipe",
              "unmatchedCompletionFlag": "N",
              "expirationDateMismatch": "N",
              "transactionDateTime": "2021-12-29T14:06:04Z",
              "merchantName": "HT02",
              "transactionAmount": "1.00",
              "transactionType": "PAYMENT TO MERCHANT",
              "messageType": "210 - Auth/Completion",
              "transactionStatus": "APPROVED",
              "responseCode": "00",
              "responseCodeDescription": "APPROVED - NO BALANCES",
              "terminalFILogo": "RM22",
              "cardFILogo": "V924",
              "terminalPinCapable": "No",
              "merchantCountry": "USA"
          }
      ]
  }
```
### By Terminal FI Logo
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/terminalTransactions/search
```
{
      "terminalId": "CATERMID",
      "filterCriteria": [
          {
              "filterBy": "TERMINALFILOGO",
              "filterValue": "RM22"
          }
      ]
  }
```
##### Response
**HTTP Code:** 200 OK
```
{
      "count": 1,
      "transactions": [
          {
              "systemRecordId": "40002075TCXT0001611881614|12080251120230113|0120",
              "cardNumber": "400020XXXXXX4000",
              "memberNumber": "0",
              "sequenceNumber": "007336",
              "sub#### ResponseCode": "0",
              "sub#### ResponseCodeDescription": "03-0 Approved with Balances",
              "preAuthAmt": "73.00",
              "amtCharged": "73",
              "authorizationCode": "010184",
              "terminalId": "CATERMID",
              "merchantCategoryCode": "6011",
              "merchantCity": "BERKELEY HEIGHTS",
              "merchantState": "NJ",
              "eciMastercard": "210",
              "eciVisa": "6",
              "pinTransaction": "4 - Yes",
              "networkID": "734004 - Plus VisaNet",
              "acquirerRefNum": "0000000000",
              "posDataInputCapability": "5",
              "posDataInputMode": "5 - Chip",
              "unmatchedCompletionFlag": "N",
              "expirationDateMismatch": "N",
              "transactionDateTime": "2021-12-29T16:37:51Z",
              "merchantName": "TEST BANK",
              "transactionAmount": "73.00",
              "transactionType": "WITHDRAWAL FROM CHECKING",
              "messageType": "210 - Auth/Completion",
              "transactionStatus": "APPROVED",
              "responseCode": "03",
              "responseCodeDescription": "APPROVED - BOTH BALANCES PROVIDED",
              "terminalFILogo": "RM22",
              "cardFILogo": "V924",
              "terminalPinCapable": "5",
              "merchantCountry": "USA"
          }
      ]
  }
```
## Update Status
**Version 2**

**Debit**

### Update Debit Card Status with Card Number, Full Card Only Format
#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/status
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "FULL_CARD_ONLY",
      "memberNumber": "0",
      "cardStatus": "CAPTURE",
      "statusReasonCode": "LOST"
  }
```
#### Response
**HTTP Code:** 204 No Content

**Credit**

### Retrieve Status Credit
Responses for credit card status always use MASKED_CARD_ONLY regardless of the requested responseFormat, as shown here.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/status/search
```
{
      "cardNumber": "4000200030004001",
      "responseFormat": "FULL_CARD_ONLY",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020xxxxxx4001",
      "cardStatus": "LOST_OR_STOLEN",
      "statusReasonCode": "LOST"
  }
```
**Version 1**

**Debit**

### Retrieve Status Debit with Card Number, Full Card Only Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/status/search
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "FULL_CARD_ONLY",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "4000200030004000",
      "cardStatus": "CAPTURE",
      "statusReasonCode": "LOST"
  }
```
### Retrieve Status Debit Card Number, Token Only Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/status/search
```
{
      "cardNumber": "4000200030004000",
      "responseFormat": "TOKEN_ONLY",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "cardStatus": "CAPTURE",
      "statusReasonCode": "LOST"
  }
  ```
### Retrieve Status Debit with NTT, Masked Card Only Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/status/search
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "responseFormat": "MASKED_CARD_ONLY",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "cardNumber": "400020xxxxxx4000",
      "cardStatus": "CAPTURE",
      "statusReasonCode": "LOST"
  }
  ```
### Retrieve Status Debit with Card Number and NTT Full Card Only Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/status/search
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "responseFormat": "FULL_CARD_ONLY",
      "memberNumber": "0"
  }
```
#### Response
****HTTP Code:** **200 OK
```
{
      "cardNumber": "4000200030004000",
      "cardStatus": "CAPTURE",
      "statusReasonCode": "LOST"
  }
```
### Retrieve Status Debit with Card Number and NTT, Token Only Format
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/status/search
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "responseFormat": "TOKEN_ONLY",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "cardStatus": "CAPTURE",
      "statusReasonCode": "LOST"
  }
```
### Update Debit Card Status
Allow clients to update the Status and Reason codes for a debit card. 

#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/status
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "cardStatus": "ACTIVE",
      "statusReasonCode": "NONE",
      "fraudActivity": "NONE_SUSPECTED",
      "securityMemo": "memo"
  }
```
#### Response
**HTTP Code:** 204 No Content
