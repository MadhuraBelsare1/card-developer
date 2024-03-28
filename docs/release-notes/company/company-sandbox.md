# Test Cases

## $${\color{orage}Company API Endpoints }$$
$${\color{purple} \boxed{ \frak{ \color{orange}Rise \space \color{cyan}and \space \color{magenta}Rise \space \color{lime}again \space \color{violet}until \space \color{lightgray}Lambs \space \color{teal}become \space \color{red}Lions !} } }$$
## Details
Tests must use only requests given here.

## Company ID Search
This case activates a card.

#### Request

**HTTP METHOD:** POST

**Target URL:**  https://card-sandbox.api.fiservapps.com/cs/companies/v1/id/search

``` 
{
   "companyIdentifier": "TEST0002",
   "systemIdentifier": "3771",
   "principalIdentifier": "0050",
   "agentIdentifier": "0000"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "address": [
      {
         "addressLine1": "123 ANY STREET",
         "addressLine2": "APT 100",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "PARSIPPANY"
      }
   ],
   "summary": [
      {
         "companyIdentifier": "TEST0002",
         "companyName": "FISERV",
         "systemIdentifier": "3771",
         "principalIdentifier": "0050",
         "agentIdentifier": "0000",
         "institutionName": "360 FEDERAL CREDIT UNION",
         "productName": "360 FCU VISA BUSINESS",
         "companyCreditLine": "100000",
         "companyAvailableCreditAmount": "86489",
         "companyContactTelephoneNumber": "9898989898",
         "openDate": "2020-07-15",
         "lastChangeDate": "2021-09-17",
         "billingCycleCode": "03",
         "annualFeeAmount": "0.0",
         "statementOptionCode": "SEND_STATEMENTS_TO_ISSUER",
         "paperStatementSuppressCode": "DO_NOT_SUPPRESS",
         "companyLastBillingDate": "2021-09-17",
         "companyNextBillingDate": "2021-10-17",
         "companyContactName": "DAVID",
         "principalOfficerName": "CLARA",
         "businessType": "ASSOCIATIONS",
         "goodAccountOutstandingBalanceAmount": "13511",
         "externallyStatusedAccountsOutstandingBalance": "0",
         "companyCreditLineExceptionPercentage": "100",
         "cardholderCreditLineExceptionPercentageRate": "100",
         "federalTaxFormTaxTypeCode": "TAX_ID",
         "federalTaxIdentifier": "981231256",
         "averageCardholderBalanceAmount": "3466",
         "goodAccountMaximumCreditLineAmount": "597600",
         "externallyStatusedAccountsMaximumCredit": "11250",
         "contractExpirationDate": "2099-12",
         "goodAccountsCount": "33",
         "externallyStatusedAccountsCount": "0",
         "fiscalYearEndCode": "JAN",
         "generalLedgerCostCenterIdentifier": "A32424RTRTREQW2311413241",
         "cdfIndicator": "CDF_REPORTING_ACTIVE",
         "vcfIndicator": "VCF_REPORORTING_ACTIVE",
         "reportLanguageCode": "ENGLISH",
         "miscellaneousField1Text": "OP1",
         "miscellaneousField2Text": "OP2",
         "miscellaneousField3Text": "OP3",
         "miscellaneousField4Text": "OP4",
         "creditScoreCode": "800",
         "numberOfEmployees": "10",
         "clientDefinedOneText": "1",
         "clientDefinedTwoText": "12",
         "clientDefinedThreeText": "123",
         "clientDefinedFourText": "123",
         "clientDefinedFiveText": "123",
         "clientDefinedSixText": "123",
         "clientDefinedSevenText": "1"
      }
    ]
  }
}
```

## Company Name Search
This method is to get list of companies by using company name. This will act as wild card search.

#### Request

**HTTP METHOD:** POST

**Target URL:**  https://card-sandbox.api.fiservapps.com/cs/companies/v1/id/search

``` 

{
   "companyName": "FISERV",
   "systemIdentifier": "3771"
 }
 
``` 
#### Response
**HTTP Code:** 200

``` 
 {
   "summary": [
      {
         "agentIdentifier": "0000",
         "companyCreditLine": "100000",
         "companyIdentifier": "TEST0002",
         "companyName": "FISERV",
         "goodAccountsCount": "36",
         "principalIdentifier": "0050",
         "systemIdentifier": "3771",
         "address": [
            {
               "addressLine1": "123 ANY STREET",
               "addressLine2": "APT 100",
               "country": "USA",
               "state": "NJ",
               "zipCode": "07054",
               "city": "PARSIPPANY"
            }
         ]
      }
   ]
}
```
## Account Details

Tests must use only requests given here.

### Not Using Card Number

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/accounts/search

``` 
{
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "startSequence": "1",
    "endSequence": "3"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "count": "3",
    "summary": [
	      {
            "accountNumber": "4907570050500063",
            "cardholderName": "JESSE, DOE",
            "accountType": "CONTROL",
            "creditLimitAmount": "59200.00",
            "currentBalanceAmount": "2501.74",
            "minimumPaymentDueAmount": "0.00",
            "statementEndingBalanceAmount": "2501.74",
            "lastStatementDate": "2024-01-01",
            "nextPaymentDueDate": "2024-01-26",
            "externalStatusCode": "NORMAL"
        },
	      {
            "accountNumber": "4907570050500071",
            "cardholderName": "JOHN, DOE",
            "accountType": "SUB",
            "creditLimitAmount": "200001.00",
            "currentBalanceAmount": "0.00",
            "controlAccountNumber": "4907570050500063",
            "minimumPaymentDueAmount": "0.00",
            "statementEndingBalanceAmount": "0.00",
            "lastStatementDate": "000000",
            "nextPaymentDueDate": "2024-01-26",
            "externalStatusCode": "NORMAL"
        },
	      {
            "accountNumber": "4907570050500089",
            "cardholderName": "COMPANY, TEST",
            "accountType": "INDIVIDUAL",
            "creditLimitAmount": "200001.00",
            "currentBalanceAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "statementEndingBalanceAmount": "0.00",
            "lastStatementDate": "000000",
            "nextPaymentDueDate": "2024-01-26",
            "externalStatusCode": "NORMAL"
        }
    ]
}
```

### Company Account Control
This API is used to add company control account.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/accounts/controls

``` 
{
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "customerName": "JESSE, DOE",
    "creditLimitAmount": "99999",
    "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
    "federalTaxIdentifier": "981231256",
    "personalizedEmbossing": "Test",
    "pricingStrategy": "AA01",
    "cardStock": "00",
    "workPhoneNumber": "2223334444",
    "workEmail": "zyz@test.com",
    "address": {
        "addressLine1": "123 Any Street",
        "addressLine2": "Apt 100",
        "country": "USA",
        "state": "NJ",
        "zipCode": "07054",
        "city": "Pasrippany",
        "isFormattedAddress": true
    }
}
``` 
#### Response
**HTTP Code:** 201 Created

``` 
{
  "companyIdentifier": "TEST0002",
  "systemIdentifier": "3771",
  "principalIdentifier": "0050",
  "agentIdentifier": "0000",
  "accountNumber": "4907570054342454",
  "cardNumber": "4907570054342389",
  "externalCustomerId": "B24029052933423554035550"
}
```


### Company Account Individuals
This API is used to add individual account.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/accounts/individuals

``` 
{
     "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "customerName": "COMPANY, TEST",
    "mothersMaidenName": "Nancy",
    "dateOfBirth": "1990-08-24",
    "creditLimitAmount": "3000",
    "specialAccountHandeling": "NONE",
    "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
    "federalTaxIdentifier": "981231256",
    "personalizedEmbossing": "John Doe",
    "pricingStrategy": "AA01",
    "cardStock": "00",
    "homePhoneNumber": "7406520178",
    "workPhoneNumber": "7406520178",
    "mobilePhoneNumber": "7406520178",
    "homeEmail": "testemail@email.com",
    "workEmail": "testemail@company.com",
    "address": {
        "addressLine1": "123 Any Street",
        "addressLine2": "Apt 100",
        "country": "USA",
        "state": "NJ",
        "zipCode": "07054",
        "city": "Parsippany",
        "isFormattedAddress": true
    }
}
``` 
#### Response
**HTTP Code:** 201 Created

``` 
{
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "accountNumber": "4907570050500089",
    "cardNumber": "4907570054342215",
}
```

### Company Account Sub
This API is used to add sub account.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/accounts/subs

``` 
{
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "controlAccount": "4907570050500063",
    "customerName": "JOHN, DOE",
    "mothersMaidenName": "NANCY",
    "dateOfBirth": "1990-08-24",
    "creditLimitAmount": "3000",
    "specialAccountHandeling": "NONE",
    "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
    "federalTaxIdentifier": "981231256",
    "personalizedEmbossing": "DOE, JOHN",
    "pricingStrategy": "AA01",
    "cardStock": "00",
    "homePhoneNumber": "7406520178",
    "workPhoneNumber": "7406520178",
    "mobilePhoneNumber": "7406520178",
    "homeEmail": "testemail@mail.com",
    "workEmail": "testemail@company.com",
    "address": {
        "addressLine1": "123 ANY STREET",
        "addressLine2": "APT 100",
        "country": "USA",
        "state": "NJ",
        "zipCode": "07054",
        "city": "PARSIPPANY",
        "isFormattedAddress": true
    }
}
``` 
#### Response
**HTTP Code:** 201 Created

``` 
{
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "accountNumber": "4907570050500089",
    "cardNumber": "4907570054342215",
    "externalCustomerId": "B24029052933423554035550"
}
```

### Company Account
This API is used to add individual account.

#### Request

**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/accounts/sub

``` 
{
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "controlAccount": "4907570050500063",
    "customerName": "JOHN, DOE",
    "mothersMaidenName": "NANCY",
    "dateOfBirth": "1990-08-24",
    "creditLimitAmount": "3000",
    "specialAccountHandeling": "NONE",
    "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
    "federalTaxIdentifier": "981231256",
    "personalizedEmbossing": "DOE, JOHN",
    "pricingStrategy": "AA01",
    "cardStock": "00",
    "homePhoneNumber": "7406520178",
    "workPhoneNumber": "7406520178",
    "mobilePhoneNumber": "7406520178",
    "homeEmail": "testemail@mail.com",
    "workEmail": "testemail@company.com",
    "address": {
        "addressLine1": "123 ANY STREET",
        "addressLine2": "APT 100",
        "country": "USA",
        "state": "NJ",
        "zipCode": "07054",
        "city": "PARSIPPANY",
        "isFormattedAddress": true
    }
}
``` 
#### Response
**HTTP Code:**  201 Created

``` 
{
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "accountNumber": "4907570050500089",
    "cardNumber": "4907570054342215",
    "externalCustomerId": "B24029052933423554035550"
}
```


## Demographics

Tests must use only requests given here.

### Companies Demographics Search
#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/demographics/search

``` 
{
   "companyIdentifier": "TEST0002",
   "systemIdentifier": "3771",
   "principalIdentifier": "0050",
   "agentIdentifier": "0000"
}
``` 
#### Response
**HTTP Code:** 200 OK

``` 
 {
   "primaryAddresses": {
      "sequenceNumber": "00001",
      "name": "JESSE DOE",
      "workPhone": "9871625141",
      "address": {
         "addressLine1": "123 ANY STREET",
         "addressLine2": "APT 100",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "PARSIPPANY"
      }
   },
   "previousAddresses": {
      "sequenceNumber": "00002",
      "address": {
         "addressLine1": "23 ANY STREET",
         "addressLine2": "APT 101",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "PARSIPPANY"
      }
   },
   "secondaryAddresses": {
      "sequenceNumber": "00003",
      "workPhone": "9877665542",
      "address": {
         "addressLine1": "12 ANY STREET",
         "addressLine2": "APT 10",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "PARSIPPANY"
      }
   },
   "individualGuarantors": [
      {
         "sequenceNumber": "00004",
         "firstName": "JESSE",
         "lastName": "DOE",
         "middleInitial": "M",
         "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
         "federalTaxIdentifier": "123456789",
         "workPhone": "7406520178",
         "alternativePhone": "9789120123",
         "emailAddress": "JESSEDOE@EXAMPLE.COM",
         "address": {
            "addressLine1": "201 ANY STREET",
            "addressLine2": "APT 20",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "PARSIPPANY"
         }
      }
   ],
   "companyGuarantors": [
      {
         "sequenceNumber": "00005",
         "name": "JESSE",
         "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
         "federalTaxIdentifier": "129956789",
         "workPhone": "7406520178",
         "alternativePhone": "9789120123",
         "address": {
            "addressLine1": "13 ANY STREET",
            "addressLine2": "APT 19",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "PARSIPPANY"
         }
      }
   ],
   "individualOwners": [
      {
         "sequenceNumber": "00006",
         "firstName": "JOHN",
         "lastName": "DOE",
         "middleInitial": "M",
         "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
         "federalTaxIdentifier": "223456789",
         "workPhone": "7406520178",
         "emailAddress": "JESSEDOE@EXAMPLE.COM",
         "address": {
            "addressLine1": "12 ANY STREET",
            "addressLine2": "APT 10",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "PARSIPPANY"
         }
      }
   ],
   "companyOwners": [
      {
         "sequenceNumber": "00007",
         "name": "DAVID",
         "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
         "federalTaxIdentifier": "323456789",
         "workPhone": "7406520178",
         "address": {
            "addressLine1": "123 ANY STREET",
            "addressLine2": "APT 100",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "PARSIPPANY"
         }
      }
   ]
 }
```

### Retrieve Audit Records for a Card

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/demographics

``` 
{
   "companyIdentifier": "TEST0002",
   "systemIdentifier": "3771",
   "principalIdentifier": "0050",
   "agentIdentifier": "0000",
   "primaryAddress": {
      "name": "Jesse Doe",
      "workPhone": "7406520178",
      "address": {
         "addressLine1": "123 Any Street",
         "addressLine2": "Apt 100",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "Parsippany"
      }
   },
   "previousAddress": {
      "address": {
         "addressLine1": "23 Any Street",
         "addressLine2": "Apt 101",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "Parsippany"
      }
   },
   "secondaryAddress": {
      "workPhone": "6789120123",
      "address": {
         "addressLine1": "12 Any Street",
         "addressLine2": "Apt 10",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "Parsippany"
      }
   },
   "individualGuarantor": {
      "firstName": "Jesse",
      "lastName": "Doe",
      "middleInitial": "M",
      "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
      "federalTaxIdentifier": "123456789",
      "workPhone": "7406520178",
      "alternativePhone": "9789120123",
      "emailAddress": "jessedoe@example.com",
      "address": {
         "addressLine1": "201 Any Street",
         "addressLine2": "Apt 20",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "Parsippany"
      }
   },
   "companyGuarantor": {
      "name": "Jesse",
      "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
      "federalTaxIdentifier": "129956789",
      "workPhone": "7406520178",
      "alternativePhone": "9789120123",
      "address": {
         "addressLine1": "13 Any Street",
         "addressLine2": "Apt 19",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "Parsippany"
      }
   },
   "individualOwner": {
      "firstName": "John",
      "lastName": "Doe",
      "middleInitial": "M",
      "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
      "federalTaxIdentifier": "223456789",
      "workPhone": "7406520178",
      "emailAddress": "jessedoe@example.com",
      "address": {
         "addressLine1": "12 Any Street",
         "addressLine2": "Apt 10",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "Parsippany"
      }
   },
   "companyOwner": {
      "name": "David",
      "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
      "federalTaxIdentifier": "323456789",
      "workPhone": "7406520178",
      "address": {
         "addressLine1": "123 Any Street",
         "addressLine2": "Apt 100",
         "country": "USA",
         "state": "NJ",
         "zipCode": "07054",
         "city": "Parsippany"
      }
   }
}

``` 
#### Response
**HTTP Code:** 201 Created

``` 
{
{
   "companyIdentifier": "TEST0002",
   "systemIdentifier": "3771",
   "principalIdentifier": "0050",
   "agentIdentifier": "0000",
   "primaryAddress": {
      "sequenceNumber": "00001"
   },
   "previousAddress": {
      "sequenceNumber": "00002"
   },
   "secondaryAddress": {
      "sequenceNumber": "00003"
   },
   "individualGuaranter": {
      "sequenceNumber": "00004"
   },
   "companyGuaranter": {
      "sequenceNumber": "00005"
   },
   "individualOwner": {
      "sequenceNumber": "00006"
   },
   "companyOwner": {
      "sequenceNumber": "00007"
   }
}
}
```

### Company Update Demographics
This API adds demographic details for the parties associated with the company.

#### Request

**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/demographics

``` 
{
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
	 "demographics": {
        "companyName": "FISERV",
        "companyContactName": "DAVID",
        "creditScoreCode": "800",
        "numberOfEmployees": "101",
        "businessType": "PARTNERSHIP",
        "companyContactTelephoneNumber": "9898989898",
        "federalTaxFormTaxTypeCode": "TAX_ID",
        "federalTaxIdentifier": "9812312560",
        "reportLanguageCode": "ENGLISH",
        "miscellaneousField1Text": "A",
        "miscellaneousField2Text": "B",
        "miscellaneousField3Text": "C",
        "miscellaneousField4Text": "D",
        "address": {
            "addressLine1": "123 Any Street",
            "addressLine2": "Apt 100",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "Parsippany"
        }
    },
    "primaryAddress": {
	    "sequenceNumber": "00001"
        "name": "Jesse, Doe",
        "workPhone": "9871625141",
        "address": {
            "addressLine1": "123 Any Street",
            "addressLine2": "Apt 100",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "Parsippany"
        }
    },
    "previousAddress": {
       "sequenceNumber": "00002",
        "address": {
            "addressLine1": "23 Any Street",
            "addressLine2": "Apt 101",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "Parsippany"
        }
    },
    "secondaryAddress": {
       "sequenceNumber": "00003",
        "workPhone": "9877665542",
        "address": {
            "addressLine1": "12 Any Street",
            "addressLine2": "Apt 10",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "Parsippany"
        }
    },
    "individualGuarantor": {
        "sequenceNumber": "00004",
        "firstName": "Jesse",
        "lastName": "Doe",
        "middleInitial": "M",
        "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
        "federalTaxIdentifier": "123456789",
        "workPhone": "7406520178",
        "alternativePhone": "9789120123",
        "emailAddress": "jessedoe@example.com",
        "address": {
            "addressLine1": "201 Any Street",
            "addressLine2": "Apt 20",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "Parsippany"
        }
    },
    "companyGuarantor": {
        "sequenceNumber": "00005",
        "name": "Jesse",
        "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
        "federalTaxIdentifier": "129956789",
        "workPhone": "7406520178",
        "alternativePhone": "9789120123",
        "address": {
            "addressLine1": "13 Any Street",
            "addressLine2": "Apt 19",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "Parsippany"
        }
    },
    "individualOwner": {
        "sequenceNumber": "00006",
        "firstName": "John",
        "lastName": "Doe",
        "middleInitial": "M",
        "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
        "federalTaxIdentifier": "223456789",
        "workPhone": "7406520178",
        "emailAddress": "jessedoe@example.com",
        "address": {
            "addressLine1": "12 Any Street",
            "addressLine2": "Apt 10",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "Parsippany"
        }
    },
    "companyOwner": {
       "sequenceNumber": "00007",
        "name": "David",
        "federalTaxFormTaxTypeCode": "SOCIAL_SECURITY",
        "federalTaxIdentifier": "323456789",
        "workPhone": "7406520178",
        "address": {
            "addressLine1": "123 Any Street",
            "addressLine2": "Apt 100",
            "country": "USA",
            "state": "NJ",
            "zipCode": "07054",
            "city": "Parsippany"
        }
    }
 }
``` 
#### Response
**HTTP Code:** 201 Created


###Update Cardholder Address Using nonTransToken
This API is used to delete demographic details associated to the company.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/demographics

``` 
 {
    "op": "DELETE_ASSOCIATION",
    "sequenceNumber": "00001",
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "addressType": "INDIVIDUAL_GUARANTOR"
 }
``` 
#### Response
**HTTP Code:** 204 No Content

## Notes/Memo

Tests must use only requests given here.

### Companies Note Search
This API returns a list with one or multiple company notes with summary information.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/notes/search

``` 
{
   "companyIdentifier": "TEST0002",
   "systemIdentifier": "3771",
   "principalIdentifier": "0050",
   "agentIdentifier": "0000",
   "startDate": "2024-01-31",
   "endDate": "2024-02-07"
}
``` 
#### Response
**HTTP Code:** 200 OK

``` 
{
   "notes": [
      {
         "noteId": "01",
         "operatorIdentifier": "VSA",
         "date": "2024-02-02",
         "text": "CREDIT LIMIT INCREASED"
      }
   ]
}
```

### Company Memos Search
This API returns a list with one or multiple company memos with summary information.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/memos/search

``` 
{
   "companyIdentifier": "TEST0002",
   "systemIdentifier": "3771",
   "principalIdentifier": "0050",
   "agentIdentifier": "0000",
   "startDate": "2024-01-31",
   "endDate": "2024-02-07"
}
``` 
#### Response
**HTTP Code:** 200 OK

``` 
{
   "memos": [
      {
         "memoId": "01",
         "operatorIdentifier": "VSA",
         "date": "2024-02-01",
         "text": "CREDIT LIMIT INCREASED"
      }
   ]
}
```

### Company Notes
This API is used for updating company notes and memos.
#### Request

**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/companies/v1/notes

``` 
{
    "identifier": "001",
    "companyIdentifier": "TEST0002",
    "systemIdentifier": "3771",
    "principalIdentifier": "0050",
    "agentIdentifier": "0000",
    "noteType": "NOTE",
    "text": "This is company note"
}
``` 
#### Response
**HTTP Code:** 204 No Content
