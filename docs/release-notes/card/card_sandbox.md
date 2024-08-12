# Test Cases

<span style="color:#ff6600;">**Card API Endpoints**</span>

When testing these endpoints, please use the test cases and test data from the Sandbox.

## Activations

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
This case activates a card using NTT.

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
This case demonstrates when the debit card is inactive.

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
This case demonstrates when the debit card is activated.

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

### Credit Add v2: Not using card number 
This case adds a new credit card without using a card number.

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

### Debit Add v2: Using card number
This case adds a new debit card using a card number.

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

### Debit Add v2: Not using card number
This case adds a new debit card without using a card number.

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

### Debit Add v2: Not using card number, using full card and token response format
This case adds a new debit card without using a card number.

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

### Debit Add v2: Not using card number, using masked card and token response format
This case adds a new debit card without using a card number.

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

### Debit Add v2: Not using card number, using token only response format
This case adds a new debit card without using a card number.

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

### Credit Template v2: Retrieve template using account number
This case retrieves a template to add a card using an account number.
<i>This case retrieves an add card template using an account number.</i>

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

### Debit Template v2: Retrieve template using card number
This case retrieves template using a card number.

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
### Debit Template v2: Retrieve template using card class
This case retrieves template using a card class.

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
### Debit Template v2: Retrieve template using NTT
This case retrieves template using NTT.

#### Request
**HTTP Method:** POST

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

### Debit Template v2: Retrieve template using NTT
This case retrieves template using NTT.

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

### Debit NTT v1: Generate using card number, without response format 
This case generates an NTT using a card number.

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
**HTTP Code:** 201 Created
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000
}
```

###  Debit NTT v1: Generate using card number, full card and token format 
This case generates an NTT using a card number.

#### Request
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
**HTTP Code:** 201 Created
```
{
       "cardNumber": "4000200030004000",
       "nonTransToken": "piUVBJKZGfks4000"
}
```

### Debit NTT v1: Generate using card number, masked card and token format
This case generates an NTT using a card number.

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
**HTTP Code:** 201 Created
```
{
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000"
}
```

### Debit NTT v1: Generate using card number, token only format 
This case generates an NTT using a card number.

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

### Debit NTT v1: Search using card number
This case retrieves an NTT using a card number.

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


### Debit NTT v1: Search using card number, full card and token format 
This case retrieves an NTT using a card number.

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

### Debit NTT v1: Search using card number, masked card and token format
This case retrieves an NTT using a card number.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/ntt/search
```
{
    "cardNumber": "4000200030004001",
    "responseFormat" : "MASKED_CARD_AND_TOKEN"
}
```

### Debit NTT v1: Search using NTT
This case retrieves a card number using NTT.

#### Request
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4001",
    "nonTransToken": "pSAZIXCAXrAo4001"
}
```

###  Debit NTT v1: Search using NTT 
This case retrieves a card number using NTT.

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
### Debit NTT v1: Search using card number, token only format
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



## Audit
### Debit Audit v1: Retrieve details of audit records for card
Retrieves the details of audit log records for card.

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
### Debit Audit v1: Retrieve audit records for a card for date range
Retrieves the audit details of a given debit card for date range.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/audit/search
```
{
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "fromDateTime": "2021-07-20T07:00:00Z",
      "toDateTime": "2021-08-20T07:00:00Z"
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
 "cardNumber": "400020XXXXXX4000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "auditLogSearch": [
    {
      "auditLogDateTime": "2021-07-20T08:00:00Z",
      "auditLogSource": "ATM",
      "auditLogAction": "UPDATE",
      "recordType": "Card Details (DAF).",
      "auditLogId": "Alex"
    }
 ]
}
```



## Compromised Card

### Compromised Card v1: Get compromised cards list
This API returns a list of compromised cards for both debit and credit. The request has one of the following required parameters; cardnumber, networkalert or fromdate and todate.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/compromised/search
```
{
  "cardNumber": "400020003000400",
  "memberNumber": "0",
  "fromDateTime": "2021-07-20T07:00:00Z",
  "toDateTime": "2021-08-20T07:00:00Z"
}
```
##### Response
**HTTP Code:** 200 OK
```
{
  "compromisedCards": [
    {
      "cardNumber": "400020XXXXXX4000",
      "clientId": "12345678",
      "networkAlert": "CompCard1234",
      "networkAlertDate": "2021-12-30",
      "severityLevel": "A",
      "compromiseSource": "FALCOMPCARD TEST 1",
      "sourceAlertDescription": "NO ACTION TAKEN"
    }
  ]
  }
```

### Credit Compromised Card v1: Get details of compromised card
Returns details of compromised cards of type credit for the provided card number.

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


### Debit Compromised Card v1: Get details of compromised card
Returns details of compromised cards of type debit for the provided card number.

#### Request
**HTTP Method:** POST
**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/compromised/details/search
```
{
  "cardNumber": "4000200030004001",
  "networkAlert": "CompCard123456"
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

### Credit Demographics v4: Search using card number
This case retrieves the demographics of a cardholder using a card number.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards/v4/cards/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004001"
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
## Credit Demographics v3: Update cardholder contact information using card number
This case updates the contact information using a card number.

#### Request
**HTTP Method**: PATCH

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
            }
  }
```
#### Response
**HTTP Code:** 204 No Content

### Credit Demographics v3: Update cardholder address using card number
This case updates the address information using a card number.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/cards//v3/cardholders/address
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


### Debit Demographics v4: Search using card number 
This case retrieves the demographics of a cardholder using a card number.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v4/cards/cardholders/demographics/search
```
{
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
  }
```
#### Response
**HTTP Code:** 200 OK

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


### Debit Demographics v4: Search using NTT
This case retrieves the demographics of a cardholder using NTT.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v4/cards/cardholders/demographics/search
```
{
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
#### Response
**HTTP Code:**  200 OK
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

### Debit Demographics v3: Update cardholder contact information using NTT
This case updates the contact information using NTT.

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

### Debit Demographics v3: Update cardholder contact information using card number
This case updates the contact information using a card number.

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

### Debit Demographics v3: Update cardholder address using card number
This case updates the address information using a card number.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/address
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

## Details
### Credit Details v3: Update additional information using card number
This case updates the additional information using card number.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/additionalInfo<
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

### Credit Details v1: Search additional information using card number </a></h3></div>
This case retrieves the additional information using card number.

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
### Debit Details v3: Update additional information using card number
This case updated the additional information using card number.

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
**HTTP Code:** 204 No Content

### Debit Details v3: Update additional information using NTT
This case updated the additional information using NTT.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cardholders/additionalInfo<
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
**HTTP Code**: 204 No Content

### Debit Details v1: Search additional information using card number
This case retrieves the additional information using card number.

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

### Debit Details v1: Search additional information using NTT
This case retrieves the additional information using NTT.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/additionalInfo/search
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
```

### Debit Details v3: Update ATM preferences using NTT
This case updates the ATM Preferences using a NTT.

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


### Debit Details v3: Update ATM preferences using NTT
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

### Debit Details v1: Search ATM preferences using card number
This case retrieves the ATM Preferences using a card number.

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
**HTTP Code:**  200 OK
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

### Debit Details v1: Search ATM preferences using NTT
This case retrieves the ATM preferences using NTT.

#### Request
H**TTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/atmPreferences/search
```
{
      "nonTransToken": "piUVBJKZGfks4000",
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

### Debit Details v2: Cardholder search using full card record
This case retrieves the cardholder information using other commonly known information.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search<
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



### Debit Details v2: Cardholder search using card number
This case retrieves the cardholder information using a card number.

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

```

### Debit Details v2: Cardholder search using NTT
This case retrieves the cardholder information using NTT.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "nonTransToken": "piUVBJKZGfks4000"
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

### Debit Details v2: Cardholder search using SSN or tax ID and last name
This case retrieves the cardholder information using SSN or tax id and last name.

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
**HTTP Code:**  200 OK
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



### Debit Details v2: Cardholder search using email
This case retrieves the cardholder information using and email address.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cardholders/search
```
{
      "emailAddress": "jdoe@example.com"
  }
```
#### Response
**HTTP Code:**  200 OK
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

### Debit Details v2: Cardholder search using account and phone numbers
This case retrieves the cardholder information using account number and phone number.

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
**HTTP Code**: 200 OK
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

### Debit Details v2: Cardholder search using card number, full card and token format
This case retrieves the cardholder information using card number.

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

### Debit Details v2: Cardholder search using card number, token only format
This case retrieves the cardholder information using card number.

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

### Debit Details v2: Cardholder search using NTT, masked card only format
This case retrieves the cardholder information using card number.

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



## Limits

### Debit Limits v2: Search limits using card number
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

### Debit Limits v2: Search limits using NTT
Retrieves the limits for the selected cardholder record.

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
### Debit Limits v2: Search limits using card number, token only response format
Retrieves the limits for the selected cardholder record.

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
### Debit Limits v2: Search limits using card number, full card only response format
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
### Debit Limits v2: Search limits using card number, full card  and  token only response format.
Retrieves the limits for the selected cardholder record

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
### Debit Limits v2: Search limits using card number, masked card only response format
Retrieves the limits for the selected cardholder record

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
### Debit Limits v2: Search limits using card number, masked card and token response format
Retrieves the limits for the selected cardholder record.

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
####  Response
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

### Debit Limits v2: Update daily limits using card number
Override the daily limits for the selected cardholder record.

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

### Debit Limits v2: Update daily limits using NTT
Override the daily limits for the selected cardholder record.

#### Request
**HTTP Method:** PATCH

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
### Debit Limits v2: Update daily limits using card number, full card only response format
Override the daily limits for the selected cardholder record.

#### Request
**HTTP Method:** PATCH

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
### Debit Limits v2: Update daily limits using card number, full card and token response format
Override the daily limits for the selected cardholder record.

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
### Debit Limits v2: Update daily limits using card number, masked card only response format
Override the daily limits for the selected cardholder record.

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
### Debit Limits v2: Update daily limits using card number, masked card and token response format
Override the daily limits for the selected cardholder record.

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
### Debit Limits v2: Update daily limits using card number, token only response format
Override the daily limits for the selected cardholder record.

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
### Debit Limits v2: Update open to buy limits using card number
Update the open to buy limits for the selected cardholder record.

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

### Debit Limits v2: Update open to buy limits using NTT
Update the open to buy limits for the selected cardholder record

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
### Debit Limits v2: Update open to buy limits using card number, token only response format
Update the open to buy limits for the selected cardholder record.

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
### Debit Limits v2: Update open to buy limits using card number, full card only response format
Update the open to buy limits for the selected cardholder record.

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
### Debit Limits v2: Update open to buy limits using card number, full card and token response format
Update the open to buy limits for the selected cardholder record

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
### Debit Limits v2: Update open to buy limits using card number, masked card only response format
Update the open to buy limits for the selected cardholder record

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
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
### Debit Limits v2: Update open to buy limits using card number, masked card and token response format
Update the open to buy limits for the selected cardholder record.

#### Request
**HTTP Method**: PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/openToBuy
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_AND_TOKEN",
  "memberNumber": "0",
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

### Debit Limits v2: Update velocity limits using NTT
Updates the velocity limits for the selected cardholder record.

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
### Debit Limits v2: Update velocity limits using card number, token only response format
Updates the velocity limits for the selected cardholder record.

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
### Debit Limits v2: Update velocity limits using card number, full card only response format
Updates the velocity limits for the selected cardholder record.

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
### Debit Limits v2: Update velocity limits using card number, full card and token response format
Updates the velocity limits for the selected cardholder record.

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
### Debit Limits v2: Update velocity limits using card number, masked card only response format
#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
```
{
  "cardNumber": "4000200030004000",
  "responseFormat": "MASKED_CARD_ONLY",
  "memberNumber": "0",
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
### Debit Limits v2: Update velocity limits using card number, masked card and token response format
Updates the velocity limits for the selected cardholder record.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/limits/velocity
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

### Debit Limits v2: Set to default limits using card number 
Sets the cardholder limits to default values per card class.

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

### Debit Limits v2: Set to default limits using NTT
Sets the cardholder limits to default values per card class.

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
### Debit Limits v2: Set to default limits using card number, token only response format
Sets the cardholder limits to default values per card class.

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
### Debit Limits v2: Set to default limits card number, full card only response format
Sets the cardholder limits to default values per card class.

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
### Debit Limits v2: Set to default limits using card number, full card and token response format
Sets the cardholder limits to default values per card class.

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
### Debit Limits v2: Set to default limits using card number, masked card only response format
Sets the cardholder limits to default values per card class.

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
### Debit Limits v2: Set to default limits using card number, masked card and token response format
Sets the cardholder limits to default values per card class.

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

### Credit Order v3: Search using card number
Retrieves the orders for the selected cardholder record.

#### Request
****HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/order/search
```
{
    "cardNumber": "4000200030004001"
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
                "cardholderName": "Doe, John H",
                "personalizedEmbossingText": "Home Team"
            }
        }
    ]
}
```

### Credit Order v3: Cancel using card number
Retrieves the orders for the selected cardholder record.

#### Request
****HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/order/search
```
{
    "cardNumber": "4000200030004001",
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
                "cardholderName": "Doe, John H",
                "personalizedEmbossingText": "Home Team"
            }
        }
    ]
}
```


### Credit Order v2: Cancel using card number
Cancel the selected order.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/order
```
{
      "cardNumber": "4000100020004001",
      "action": "CANCEL"
  }
```
#### Response
**HTTP Code:** 200
```
{
    "card": {
        "cardNumber": "400020XXXXXX4001",
        "nonTransToken": "pSAZIXCAXrAo4001",
        "action": "CANCEL"
    }
}
```

### Debit Order v2: Cancel using card number
Cancel the selected order.

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
          "action": "CANCEL",
          "orderId": "436"
      }
  }
```

### Debit Order v2: Cancel using NTT
Cancel the selected order.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/order
```
{
      "nonTransToken": "WUPIL5DQTZGM3000",
      "orderId": "436",
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
          "action": "CANCEL",
          "orderId": "436"
      }
  }
```

### Debit Order v3: Search using card number 
Retrieves the orders for the selected cardholder record.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/order/search
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
       "orders": [
           {
               "cardNumber": "400010XXXXXX4000",
               "orderStatus": "PROCESSED",
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
               },
               "cardMailStatusDetails": {
                   "producttype": "3",
                   "embossingFacilityShipDate": "2023-10-02",
                   "trackingNumber": "9400100020003000400050",
                   "carrier": "Fedex",
                   "shipmentStatus": "Out for Delivery",
                   "shipmentMethod": "Next DAY AIR LETTER",
                   "expectedDeliveryDate": "2023-10-08"
               }
           }
       ]
   }
```

### Debit Order v3: Search using NTT
Retrieves the orders for the selected cardholder record.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/order/search
```
{
      "nonTransToken": "WUPIL5DQTZGM3000",
  }
```
#### Response
**HTTP Code:** 200 OK
```
{
      "orders": [
          {
               "nonTransToken": "piUVBJKZGfks4000",
               "orderStatus": "PROCESSED",
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
               },
               "cardMailStatusDetails": {
                   "producttype": "3",
                   "embossingFacilityShipDate": "2023-10-02",
                   "trackingNumber": "9400100020003000400050",
                   "carrier": "Fedex",
                   "shipmentStatus": "Out for Delivery",
                   "shipmentMethod": "Next DAY AIR LETTER",
                   "expectedDeliveryDate": "2023-10-08"
               }
           }
      ]
  }
```

### Debit Order v2: Update using card number
Update rush type of the selected order.

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
          "action": "UPDATE",
          "orderId": "436"
      }
  }
```

## PIN

### Debit Pin v1: Obtain JWT token using card number
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


### Debit Pin v1: Obtain JWT token using NTT
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
### Debit Pin v1: Reset PIN attempts using card number
Reset the number of PIN attempts to zero for the selected cardholder record.

#### Request
**HTTP METHOD**: POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinAttempts
```
{
      "cardNumber": "4000200030004000",
      "memberNumber":"0"
  }
```  
#### Response
**HTTP Code:** 204 No Content

### Debit Pin v1: Reset PIN attempts using NTT 
Reset the number of PIN attempts to zero for the selected cardholder record.

#### Request
**HTTP Method:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinAttempts
```
{
      "nonTransToken": "piUVBJKZGfks4000"
  }
```  
#### Response
**HTTP Code:** 204 No Content


### Debit Pin v1: Select a PIN
Provide the selected PIN and include the JWT card token.The JWT token must be used within 15 minutes.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pin
```
{
    "pin": "3578",
    "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.XU56gXVBUVLIH83fDZ_uUNj-C4f2UpGnTbP0kHLKPFEfOjn0vYP-TCcV0Cy8Q5t0bRNxE_eI6LIRT-p-dL-lQkv5Sx1GXVvsC9L_vFBzz4QU2DbkpwVjVin088uA23OV6EhylCgiwf8Yswu_1Pu8jFyvaFJUIiEvwZkFbHX73IE6fJanhMjgn_4Eo42CVdGgmzYJtfDQ9wkbAW3w3D2C2dkvzQiYeiTTCkRdzIxEeTDcN9NSM_vwElz_zO5ONExRa_2LTPlQPcen9meot8Dzlcqlz0i4Jo2xtLmkG6bA2uQzbAID4dRujhaOhCoW-GodyOvRCjOqFNYHX8tVLBio7w.oDrfGhbXOLDEWBNA.avKcJYf5i_zP2fov70cqzEW0B2znGvIF2zdEp4bkRtSDJrRBKfcbJeEaEakLZaItLDAlXz6ANJLUntsCpyrQ0Jm4nWfjRgtVmWFSUF3TvgLUH8_Pd5e8yZsI_TuJCPDMHSIt8XEkrpyRwsQT8BgUIU-iAuGe70KoFK5Cr5qvGNLgKJDIwSzlaZma-z9HFxTs6m8hKM3_5YMK5AUGsSpsy8Fb6QNhE6enfjc3GeZei1_dwhJC3Cfd8NkeNpH8AkYWGrY_ZvyZ1YAfFdgXeasCAA.yxrJMUH91uZWejU5N1VDRQ"
}
```
#### Response
**HTTP Code:** 204 No Content

### Debit Pin v1:Set PIN offset using card number
Update the PIN Offset for the selected cardholder record.

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

### Debit Pin v1: Set PIN offset using NTT
Update the PIN Offset for the selected cardholder record.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinOffset
```
>{
   "nonTransToken": "piUVBJKZGfks4000",
   "pinOffset": "1234"
}
```  
#### Response
**HTTP Code:** 204 No Content


## Related Accounts
**Version 2**

### Debit Related Account v2: Add account using NTT
Add accounts to the selected cardholder record.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```
{
    "nonTransToken": "piUVBJKZGfks4000"
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
**HTTP Code:** 201 Created

### Debit Related Account v2: Add account using card number
Add accounts to the selected cardholder record.

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

### Debit Related Account v2: Remove account using NTT
Delete accounts associated with the selected cardholder record.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations/unassociate
```
{
      "nonTransToken": "piUVBJKZGfks4000",
      "accountNumber": "123456789",
      "accountType": "SAVINGS"
  }
```
#### Response
**HTTP Code:** 204 No Content

### Debit Related Account v2: Remove account using card number
Delete accounts associated with the selected cardholder record,

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

### Debit Related Account v2: Search account using NTT
Retrieves the details of all accounts associated with the selected cardholder record.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/search
```
{
      "nonTransToken": "piUVBJKZGfks4000"
  }
```
#### Response
**HTTP Code:** 200 OK


### Debit Related Account v2: Search account using card number
Retrieves the details of all accounts associated with the selected cardholder record.

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
```
{
    "cardNumber": "400020XXXXXX4000",
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


**Update Associated Accounts**
### Debit Related Account v2: Update account using NTT
Update the details of accounts associated with the selected cardholder record.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/accounts/associations
```

  "nonTransToken": "piUVBJKZGfks4000"
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
**HTTP Code:** 204 No Content


### Debit Related Account v2: Update account using card number
Update the details of accounts associated with the selected cardholder record.

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


### Debit Related Account v2: Remove account using NTT
Delete accounts associated with the selected cardholder record

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/accounts/unassociate

```
{
    "nonTransToken": "piUVBJKZGfks4000",
    "accountNumber": "123456789",
    "accountType": "SAVINGS"
}
```
#### Response
**HTTP Code:** 204 No Content

## Replacement

### Debit Replacement v3: Replace card using card number
Change the expiration date and create a replacement order for an existing cardholder record.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/v3/cards/replacement
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
      "cardNumber": "400020XXX      "cardNumber": "400020XXX
  }
```

### Credit Replacement v3: Replace card using card number
Change the expiration date and create a replacement order for an existing cardholder record.

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
   "nonTransToken": "pSAZIXCAXrAo4001",
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

### Debit Replacement v3: Replace card using NTT
Change the expiration date and create a replacement order for an existing cardholder record.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/v3/cards/replacement
```
{
   "nonTransToken": "piUVBJKZGfks4000",
   "cardholderName": "Doe, John H",
   "debitOnly": {
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

### Credit Replacement v1: Instant Issuance using card number, full card only format
Change the expiration date on the selected cardholder record for an instant issue plastic.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/instantIssuance
```
{
   "cardNumber": "4000200030004001",
   "nonTransToken": "pSAZIXCAXrAo4001",
   "responseFormat": "FULL_CARD_ONLY",
   "cardholderName": "Doe, John H",
   "creditOnly": {
      "cardholder": {
         "personalizedEmbossingText": "Home Team",
         "customerRoleTypeCode": "01"
      }
   }
 }
```
#### Response
**HTTP Code**: 200 OK
```
{
  "cardNumber": "4000200030004001",
   "cardholderName": "Doe, John H",
   "creditOnly": {
      "cardholder": {
         "personalizedEmbossingText": "Home Team",
         "customerRoleTypeCode": "01"
      }
   }
 }
```
### Debit Replacement v1: Instant Issuance using NTT, no response format
Change the expiration date on the selected cardholder record for an instant issue plastic.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/instantIssuance
```{
  "nonTransToken": "piUVBJKZGfks4000",
   "cardholderName": "Doe, John H",
   "debitOnly": {
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
### Debit Replacement v1: Instant Issuance using card number, full card only format
Change the expiration date on the selected cardholder record for an instant issue plastic.

#### Request
**HTTP Method:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/instantIssuance
```
{
  "cardNumber": "4000200030004000",
   "responseFormat": "FULL_CARD_ONLY",
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
   "cardNumber": "4000200030004000",
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

### Credit Transaction v3: Search using card number, date and detail filter
Retrieve transaction details of a given card based on the filter criteria passed.

#### Request

**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=detail
```
{
     "cardNumber": "4000200030004001",
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
          "originalResponseCode": "59",
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

### Credit Transaction v3: Search using card number, date and summary filter
Retrieve transaction summary of a given card based on the filter criteria passed.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
     "cardNumber": "4000200030004001",
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

### Credit Transaction v3: Search using card number, transaction code, summary filter
Retrieve transaction summary of a given card based on the filter criteria passed.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
   "cardNumber": "4000200030004001",
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
      ]
}
```

### Debit Transaction v3: Search using card number only, date and detail filter
Retrieve transaction details of a given card based on the filter criteria passed.

#### Request
**HTTP Method:** POST

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
****#### Response
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
          "tokenRequestorId": "50148904210",
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

### Debit Transaction v3: Search using card number, amount, summary filter
Retrieve transaction summary of a given card based on the filter criteria passed.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
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
               "subResponseCode": "D",
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


### Debit Transaction v3: Search using card number, date and detail filter
Retrieve transaction details of a given card based on the filter criteria passed.

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
          "subResponseCode": "D",
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
          "tokenRequestorId": "50148904210",
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

### Debit Transaction v3: Search using NTT, merchant name, summary filter
Retrieve transaction summary of a given card based on the filter criteria passed.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
     "nonTransToken": "piUVBJKZGfks4000",
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
               "subResponseCode": "D",
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


### Debit Transaction v3: Search using card number, NTT, date and summary filter
Retrieve transaction summary of a given card based on the filter criteria passed. Note: If both card number and NTT present in the request then priority is given to card number.

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
               "subResponseCode": "D",
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


### Debit Transaction v3: Search using card number, transaction code, summary filter
Retrieve transaction summary of a given card based on the filter criteria passed.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
```
{
    "cardNumber": "4000200030004000",
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
               "subResponseCode": "D",
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

### Debit Transaction v3: Search using NTT, date and detail filter
Retrieve transaction details of a given card based on the filter criteria passed.

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
          "subResponseCode": "D",
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
          "tokenRequestorId": "50148904210",
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

### Debit Transaction v3: Search using NTT, date and summary filter
Retrieve transaction summary of a given card based on the filter criteria passed.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v3/cards/transactions/search?filter=summary
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
               "subResponseCode": "D",
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

### Debit Transaction v3: Search using card number, sequence number, retrieval number and detail filter
Retrieve transaction detail of a given card based on the filter criteria passed.

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
          "subResponseCode": "D",
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
          "tokenRequestorId": "50148904210",
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

### Debit Transaction v3: Search using card number, sequence number, retrieval number and summary filter
Retrieve transaction detail of a given card based on the filter criteria passed.

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
               "subResponseCode": "D",
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


## Update Status 

### Credit card Status v1: Search card status, full card only format
Retrieve status of Credit Card,

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/status/search
```
{
      "cardNumber": "4000200030004001",
      "responseFormat": "FULL_CARD_ONLY"
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


### Debit Card Status v1: Search using card number, token only format
Retrieve the status of debit card.

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
### Debit Card Status v1: Search using card number, full card only format
Retrieve the status of debit card.

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
### Debit Card Status v1: Search using NTT, masked card only format

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

### Credit Card Status v2: Update card status 
Update the status of a card, including deactivation.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/status
```
{
  "cardNumber": "4000200030004001",
  "cardStatus": "CAPTURE",
  "statusReasonCode": "LOST",
  "fraudActivity": "POSSIBLE_FRAUD",
  "securityMemo": "memo"
  }
```
#### Response
**HTTP Code:** 204 No Content

### Debit Card Status v2: Update card status
Update the status of a card, including deactivation.

#### Request
**HTTP Method:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v2/cards/status
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

### Debit Card Status v2: Update using card number, full card only format
Update the status of a card, including deactivation.

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
