# Test Cases

See Using the Sandbox before executing test cases. Tests must use only requests given here.


## Activations
**Credit**
### Activate Inactive Credit Card
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

### Search for Details Inactive Credit Card
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

### Search for Details Active Credit Card
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

### Activate Inactive Debit Card with Card Number
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
### Activate Inactive Debit Card with NTT
#### Request
**HTTP Method:** PUT
**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations
```
{
      "nonTransToken": "hggLkjgJGSwh3000"
  }
```  
#### Response
B 200 OK
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
### Search for Details Inactive Debit Card
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
HTTP Code: 200 OK
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

### Search for Details Inactive Debit Card with NTT
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

### Search for Details Activate Debit Card
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

### Search for Details Activate Debit Card with NTT
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
Version 2

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
Templates

### Retrieve Credit Template with accountNumber
#### Request
**HTTP METHOD:** POST

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

##  Version 1
Credit

### Add Credit Card
Card Number Provided
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
Templates

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
Templates

### Retrieve Debit Template with cardNumber
#### Request
**HTTP METHOD:** POST

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
**HTTP METHOD:** POST

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
**HTTP METHOD:** POST

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
**HTTP METHOD:**POST

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

### Using Card Number Provided Masked Card Only Default Response
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
No card number in request, nonTransTokenFlag true, responseFormat TOKEN_ONLY

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
Templates

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
**HTTP Code: 201** Created
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
### Using Card Number Full Card and Token Format
**Request**
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
**HTTP Code: 201** Created
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
{
      "cardNumber": "4000200030004000",
      "responseFormat": "FULL_CARD_ONLY",
      "memberNumber": "0"
  }
#### Response
**HTTP Code: 201** Created
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
**HTTP Code: 201** Created
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
HTTP Code: 201 Created
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

T**arget URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
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
## Demographics

**Version 3**

**Credit**

**Demographics Search**

### Using Credit Card Number
#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v4/cards/cardholders/demographics/search
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
                      "countryCode": "USA",
                      "categoryCode": "PERMANENT",
                      "beginDate": "2021-08-03",
                      "endDate": "2021-08-03"
                  }
              ]
          }
      ]
  }
```
**Version 4**

**Debit**

**Demographics Search**
###Using Card Number and NTT
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

**Demographics Search**
### Search
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
**HTTP Code:** 206 Partial Success Response
```
{
      "traceId": null,
      "spanId": null,
      "instance": "/api/cardholders/v4/demographics/search",
      "code": null,
      "moreDetails": null,
      "type": "Partial Content For Credit",
      "title": "PartialSuccess",
      "message": "Response is partially success for Credit Card.",
      "timestamp": "2022-11-24T20:06:24.553771"
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
**HTTP Code:** 206 Partial Success Response
```
{
      "traceId": null,
      "spanId": null,
      "instance": "/api/cardholders/v4/demographics/search",
      "code": null,
      "moreDetails": null,
      "type": "Partial Content For Credit",
      "title": "PartialSuccess",
      "message": "Response is partially success for Credit Card.",
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
