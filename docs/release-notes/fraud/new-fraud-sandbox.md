# Test Cases

<span style="color:#ff6600;">**Fraud API Endpoints**</span>

## Case

### Retrieve Fraud Case Details
Returns all the case details including the status.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/case

``` 
{
   "caseNumber": "999999999"
}
``` 
#### Response
**HTTP Code:** 200

 ```
{
    "logo": "APIP",
    "cardNumber": "400020XXXXXX4000",
    "caseNumber": "999999999",
    "caseTenant": "60",
    "caseCreatedDateTime": "2021-07-20T07:00:00Z",
    "name": "Alex Smith",
    "otherName": "Smith",
    "fraudApproach": "Custom",
    "languagePreference": "English",
    "newReactivatedIndication": "New",
    "currentCardStatus": "Active",
    "currentCaseStatus": "OPEN",
    "actionStrategy": "A1",
    "currentContactChannel": [
        "Email CH",
        "SMS CH"
    ],
    "homePhone": "1005550001",
    "workPhone": "1005550001",
    "cellPhone": "1005550001",
    "emailAddress": "alexsmith@example.com",
    "textAddress": "1005550001",
    "enrollmentStatus": "Sent",
    "enrollmentDate": "2021-07-20T07:00:00Z",
    "createScore": "0",
    "highScore": "430",
    "usedForEnfact": {
        "homePhone": true,
        "cellPhone": true,
        "workPhone": true,
        "emailAddress": true,
        "textAddress": true
    }
}
``` 
### Retrieve Fraud Case Details including caseTenant
Returns all the case details including the status and caseTenant.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/case

``` 
{
  "caseNumber": "999999999",
  "caseTenant": "60",
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
  "logo": "APIP",
  "cardNumber": "400020XXXXXX4000",
  "caseNumber": "999999999",
  "caseTenant": "60",
  "caseCreatedDateTime": "2021-07-20T07:00:00Z",
  "name": "Alex Smith",
  "otherName": "Smith",
  "fraudApproach": "Custom",
  "languagePreference": "English",
  "newReactivatedIndication": "New",
  "currentCardStatus": "Active",
  "currentCaseStatus": "OPEN",
  "actionStrategy": "A1",
  "currentContactChannel": [
    "Email CH",
    "SMS CH"
  ],
  "homePhone": "1005550001",
  "workPhone": "1005550001",
  "cellPhone": "1005550001",
  "emailAddress": "alexsmith@example.com",
  "textAddress": "1005550001",
  "enrollmentStatus": "Sent",
  "enrollmentDate": "2021-07-20T07:00:00Z",
  "createScore": "0",
  "highScore": "430",
  "usedForEnfact": {
    "homePhone": true,
    "cellPhone": true,
    "workPhone": true,
    "emailAddress": true,
    "textAddress": true
  }
}
``` 
### Retrieve Fraud Case History
Returns the case history details for a given case.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/history

```
{
   "caseNumber": "999999999",
   "caseTenant": "60",
   "pagelimit": 50,
   "pageoffset": 1
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "caseHistory": [
      {
         "createdDateTime": "2021-07-20T07:00:00Z",
         "DateTime": "2021-07-20T07:00:00Z",
         "requestedUser": "Smith",
         "description": "No Contact Found due to INVALID data."
      }
   ]
}
``` 
### Search Fraud Cases with Required Fields Only
Search for fraud cases based on request criteria(fromDateTime and toDateTime).

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/search

``` 
{
   "fromDateTime": "2021-07-20T07:00:00Z",
   "toDateTime": "2021-07-20T07:00:00Z"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "caseSearchResults": [
      {
         "logo": "APIP",
         "cardNumber": "400020XXXXXX4000",
         "caseNumber": "999999999",
         "caseTenant": "60",
         "caseCreatedDateTime": "2021-07-20T07:00:00Z",
         "caseStatus": "OPEN",
         "name": "Alex Smith",
         "caseClosedDateTime": "2021-07-21T07:00:00Z",
         "archived": "No",
         "baseCreateScore": "0",
         "baseHighScore": "430",
         "taxId1": "1234",
         "taxId2": "1234",
         "homePhone": "1005550001",
         "secondaryPhone": "1005550001",
         "workPhone": "1005550001",
         "cellPhone": "1005550001",
         "addressLine1": "123 Any Street",
         "addressLine2": "123 Any Lane",
         "city": "New Jersey",
         "state": "NJ",
         "postalCode": "12345",
         "actionStrategy": "A1",
         "adaptiveCreateScore": "0",
         "adaptiveHighScore": "430",
         "primaryBirthDate": "1990-08-24",
         "otherBirthDate": "1990-08-24",
         "cardStatusAtCaseCreate": "Active",
         "cardTrackerSeverity": "5",
         "fraudApproach": "Minimum",
         "memberNumber": "0",
         "highTransactionDateTime": "2021-07-20T07:00:00Z",
         "lastAnalyst": "Analyst",
         "lastFraudCode": "CASE_FRAUD_TYPE_APP_FRD",
         "lastName": "Smith",
         "lastScore": "0",
         "lastTransactionDateTime": "2021-07-20T07:00:00Z",
         "OriginalAnalyst": "Analyst",
         "scoreToUse": "Base",
         "rules": "RuleManager Case Create"
      },
      {
         "logo": "APIP",
         "cardNumber": "400020XXXXXX4000",
         "caseNumber": "888888888",
         "caseCreatedDateTime": "2021-07-20T07:00:00Z",
         "caseStatus": "OPEN",
         "name": "Alex Smith",
         "caseClosedDateTime": "2021-07-21T07:00:00Z",
         "archived": "No",
         "baseCreateScore": "0",
         "baseHighScore": "430",
         "taxId1": "1234",
         "taxId2": "1234",
         "homePhone": "1005550001",
         "secondaryPhone": "1005550001",
         "workPhone": "1005550001",
         "cellPhone": "1005550001",
         "addressLine1": "123 Any Street",
         "addressLine2": "123 Any Lane",
         "city": "New Jersey",
         "state": "NJ",
         "postalCode": "12345",
         "actionStrategy": "A1",
         "adaptiveCreateScore": "0",
         "adaptiveHighScore": "430",
         "primaryBirthDate": "1990-08-24",
         "otherBirthDate": "1990-08-24",
         "cardStatusAtCaseCreate": "Active",
         "cardTrackerSeverity": "5",
         "fraudApproach": "Minimum",
         "memberNumber": "0",
         "highTransactionDateTime": "2021-07-20T07:00:00Z",
         "lastAnalyst": "Analyst",
         "lastFraudCode": "CASE_FRAUD_TYPE_APP_FRD",
         "lastName": "Smith",
         "lastScore": "0",
         "lastTransactionDateTime": "2021-07-20T07:00:00Z",
         "OriginalAnalyst": "Analyst",
         "scoreToUse": "Base",
         "rules": "RuleManager Case Create"
      }
   ]
}
``` 
### Search Fraud Cases with Required Fields and Optional Field cardNumber
Search for fraud cases based on required fields fromDateTime and toDateTime plus optional field cardNumber.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/search

``` 
{
   "fromDateTime": "2021-07-20T07:00:00Z",
   "toDateTime": "2021-07-20T07:00:00Z",
   "cardNumber": "4000200030004000"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "caseSearchResults": [
      {
         "logo": "APIP",
         "cardNumber": "400020XXXXXX4000",
         "caseNumber": "999999999",
         "caseTenant": "60",
         "caseCreatedDateTime": "2021-07-20T07:00:00Z",
         "caseStatus": "OPEN",
         "name": "Alex Smith",
         "caseClosedDateTime": "2021-07-21T07:00:00Z",
         "archived": "No",
         "baseCreateScore": "0",
         "baseHighScore": "430",
         "taxId1": "1234",
         "taxId2": "1234",
         "homePhone": "1005550001",
         "secondaryPhone": "1005550001",
         "workPhone": "1005550001",
         "cellPhone": "1005550001",
         "addressLine1": "123 Any Street",
         "addressLine2": "123 Any Lane",
         "city": "New Jersey",
         "state": "NJ",
         "postalCode": "12345",
         "actionStrategy": "A1",
         "adaptiveCreateScore": "0",
         "adaptiveHighScore": "430",
         "primaryBirthDate": "1990-08-24",
         "otherBirthDate": "1990-08-24",
         "cardStatusAtCaseCreate": "Active",
         "cardTrackerSeverity": "5",
         "fraudApproach": "Minimum",
         "memberNumber": "0",
         "highTransactionDateTime": "2021-07-20T07:00:00Z",
         "lastAnalyst": "Analyst",
         "lastFraudCode": "CASE_FRAUD_TYPE_APP_FRD",
         "lastName": "Smith",
         "lastScore": "0",
         "lastTransactionDateTime": "2021-07-20T07:00:00Z",
         "OriginalAnalyst": "Analyst",
         "scoreToUse": "Base",
         "rules": "RuleManager Case Create"
      },
      {
         "logo": "APIP",
         "cardNumber": "400020XXXXXX4000",
         "caseNumber": "888888888",
         "caseCreatedDateTime": "2021-07-20T07:00:00Z",
         "caseStatus": "OPEN",
         "name": "Alex Smith",
         "caseClosedDateTime": "2021-07-21T07:00:00Z",
         "archived": "No",
         "baseCreateScore": "0",
         "baseHighScore": "430",
         "taxId1": "1234",
         "taxId2": "1234",
         "homePhone": "1005550001",
         "secondaryPhone": "1005550001",
         "workPhone": "1005550001",
         "cellPhone": "1005550001",
         "addressLine1": "123 Any Street",
         "addressLine2": "123 Any Lane",
         "city": "New Jersey",
         "state": "NJ",
         "postalCode": "12345",
         "actionStrategy": "A1",
         "adaptiveCreateScore": "0",
         "adaptiveHighScore": "430",
         "primaryBirthDate": "1990-08-24",
         "otherBirthDate": "1990-08-24",
         "cardStatusAtCaseCreate": "Active",
         "cardTrackerSeverity": "5",
         "fraudApproach": "Minimum",
         "memberNumber": "0",
         "highTransactionDateTime": "2021-07-20T07:00:00Z",
         "lastAnalyst": "Analyst",
         "lastFraudCode": "CASE_FRAUD_TYPE_APP_FRD",
         "lastName": "Smith",
         "lastScore": "0",
         "lastTransactionDateTime": "2021-07-20T07:00:00Z",
         "OriginalAnalyst": "Analyst",
         "scoreToUse": "Base",
         "rules": "RuleManager Case Create"
      }
   ]
}
``` 
### Search Fraud Cases with Required Fields and Optional Field caseNumber
Search for fraud cases based on request criteria fromDateTime, toDateTime and caseNumber.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/search

``` 
{
   "fromDateTime": "2021-07-20T07:00:00Z",
   "toDateTime": "2021-07-20T07:00:00Z",
   "caseNumber": "999999999"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "caseSearchResults": [
      {
         "logo": "APIP",
         "cardNumber": "400020XXXXXX4000",
         "caseNumber": "999999999",
         "caseTenant": "60",
         "caseCreatedDateTime": "2021-07-20T07:00:00Z",
         "caseStatus": "OPEN",
         "name": "Alex Smith",
         "caseClosedDateTime": "2021-07-21T07:00:00Z",
         "archived": "No",
         "baseCreateScore": "0",
         "baseHighScore": "430",
         "taxId1": "1234",
         "taxId2": "1234",
         "homePhone": "1005550001",
         "secondaryPhone": "1005550001",
         "workPhone": "1005550001",
         "cellPhone": "1005550001",
         "addressLine1": "123 Any Street",
         "addressLine2": "123 Any Lane",
         "city": "New Jersey",
         "state": "NJ",
         "postalCode": "12345",
         "actionStrategy": "A1",
         "adaptiveCreateScore": "0",
         "adaptiveHighScore": "430",
         "primaryBirthDate": "1990-08-24",
         "otherBirthDate": "1990-08-24",
         "cardStatusAtCaseCreate": "Active",
         "cardTrackerSeverity": "5",
         "fraudApproach": "Minimum",
         "memberNumber": "0",
         "highTransactionDateTime": "2021-07-20T07:00:00Z",
         "lastAnalyst": "Analyst",
         "lastFraudCode": "CASE_FRAUD_TYPE_APP_FRD",
         "lastName": "Smith",
         "lastScore": "0",
         "lastTransactionDateTime": "2021-07-20T07:00:00Z",
         "OriginalAnalyst": "Analyst",
         "scoreToUse": "Base",
         "rules": "RuleManager Case Create"
      }
   ]
}
``` 
### Search Fraud Cases with Required Fields and Optional Fields lastName, phone and postalCode
Search for fraud cases based on fromDateTime and todateTime plus lastName, phone and postalCode fields.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/search

``` 
{
   "fromDateTime": "2021-07-20T07:00:00Z",
   "toDateTime": "2021-07-20T07:00:00Z",
   "lastName": "Smith",
   "phoneNumber": "1005550001",
   "postalCode": "12345"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "caseSearchResults": [
      {
         "logo": "APIP",
         "cardNumber": "400020XXXXXX4000",
         "caseNumber": "999999999",
         "caseTenant": "60",
         "caseCreatedDateTime": "2021-07-20T07:00:00Z",
         "caseStatus": "OPEN",
         "name": "Alex Smith",
         "caseClosedDateTime": "2021-07-21T07:00:00Z",
         "archived": "No",
         "baseCreateScore": "0",
         "baseHighScore": "430",
         "taxId1": "1234",
         "taxId2": "1234",
         "homePhone": "1005550001",
         "secondaryPhone": "1005550001",
         "workPhone": "1005550001",
         "cellPhone": "1005550001",
         "addressLine1": "123 Any Street",
         "addressLine2": "123 Any Lane",
         "city": "New Jersey",
         "state": "NJ",
         "postalCode": "12345",
         "actionStrategy": "A1",
         "adaptiveCreateScore": "0",
         "adaptiveHighScore": "430",
         "primaryBirthDate": "1990-08-24",
         "otherBirthDate": "1990-08-24",
         "cardStatusAtCaseCreate": "Active",
         "cardTrackerSeverity": "5",
         "fraudApproach": "Minimum",
         "memberNumber": "0",
         "highTransactionDateTime": "2021-07-20T07:00:00Z",
         "lastAnalyst": "Analyst",
         "lastFraudCode": "CASE_FRAUD_TYPE_APP_FRD",
         "lastName": "Smith",
         "lastScore": "0",
         "lastTransactionDateTime": "2021-07-20T07:00:00Z",
         "OriginalAnalyst": "Analyst",
         "scoreToUse": "Base",
         "rules": "RuleManager Case Create"
      },
      {
         "logo": "APIP",
         "cardNumber": "400020XXXXXX4000",
         "caseNumber": "888888888",
         "caseCreatedDateTime": "2021-07-20T07:00:00Z",
         "caseStatus": "OPEN",
         "name": "Alex Smith",
         "caseClosedDateTime": "2021-07-21T07:00:00Z",
         "archived": "No",
         "baseCreateScore": "0",
         "baseHighScore": "430",
         "taxId1": "1234",
         "taxId2": "1234",
         "homePhone": "1005550001",
         "secondaryPhone": "1005550001",
         "workPhone": "1005550001",
         "cellPhone": "1005550001",
         "addressLine1": "123 Any Street",
         "addressLine2": "123 Any Lane",
         "city": "New Jersey",
         "state": "NJ",
         "postalCode": "12345",
         "actionStrategy": "A1",
         "adaptiveCreateScore": "0",
         "adaptiveHighScore": "430",
         "primaryBirthDate": "1990-08-24",
         "otherBirthDate": "1990-08-24",
         "cardStatusAtCaseCreate": "Active",
         "cardTrackerSeverity": "5",
         "fraudApproach": "Minimum",
         "memberNumber": "0",
         "highTransactionDateTime": "2021-07-20T07:00:00Z",
         "lastAnalyst": "Analyst",
         "lastFraudCode": "CASE_FRAUD_TYPE_APP_FRD",
         "lastName": "Smith",
         "lastScore": "0",
         "lastTransactionDateTime": "2021-07-20T07:00:00Z",
         "OriginalAnalyst": "Analyst",
         "scoreToUse": "Base",
         "rules": "RuleManager Case Create"
      }
   ]
}
``` 
### Search Fraud Cases with Required Fields and Optional Field caseTenant
Search for fraud cases based on fromDateTime and todateTime and optional caseTenant field.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/search

``` 
{
   "fromDateTime": "2021-07-20T07:00:00Z",
   "toDateTime": "2021-07-20T07:00:00Z",
   "caseTenant": "60"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "caseSearchResults": [
      {
         "logo": "APIP",
         "cardNumber": "400020XXXXXX4000",
         "caseNumber": "999999999",
         "caseTenant": "60",
         "caseCreatedDateTime": "2021-07-20T07:00:00Z",
         "caseStatus": "OPEN",
         "name": "Alex Smith",
         "caseClosedDateTime": "2021-07-21T07:00:00Z",
         "archived": "No",
         "baseCreateScore": "0",
         "baseHighScore": "430",
         "taxId1": "1234",
         "taxId2": "1234",
         "homePhone": "1005550001",
         "secondaryPhone": "1005550001",
         "workPhone": "1005550001",
         "cellPhone": "1005550001",
         "addressLine1": "123 Any Street",
         "addressLine2": "123 Any Lane",
         "city": "New Jersey",
         "state": "NJ",
         "postalCode": "12345",
         "actionStrategy": "A1",
         "adaptiveCreateScore": "0",
         "adaptiveHighScore": "430",
         "primaryBirthDate": "1990-08-24",
         "otherBirthDate": "1990-08-24",
         "cardStatusAtCaseCreate": "Active",
         "cardTrackerSeverity": "5",
         "fraudApproach": "Minimum",
         "memberNumber": "0",
         "highTransactionDateTime": "2021-07-20T07:00:00Z",
         "lastAnalyst": "Analyst",
         "lastFraudCode": "CASE_FRAUD_TYPE_APP_FRD",
         "lastName": "Smith",
         "lastScore": "0",
         "lastTransactionDateTime": "2021-07-20T07:00:00Z",
         "OriginalAnalyst": "Analyst",
         "scoreToUse": "Base",
         "rules": "RuleManager Case Create"
      },
      {
         "logo": "APIP",
         "cardNumber": "400020XXXXXX4000",
         "caseNumber": "888888888",
         "caseCreatedDateTime": "2021-07-20T07:00:00Z",
         "caseStatus": "OPEN",
         "name": "Alex Smith",
         "caseClosedDateTime": "2021-07-21T07:00:00Z",
         "archived": "No",
         "baseCreateScore": "0",
         "baseHighScore": "430",
         "taxId1": "1234",
         "taxId2": "1234",
         "homePhone": "1005550001",
         "secondaryPhone": "1005550001",
         "workPhone": "1005550001",
         "cellPhone": "1005550001",
         "addressLine1": "123 Any Street",
         "addressLine2": "123 Any Lane",
         "city": "New Jersey",
         "state": "NJ",
         "postalCode": "12345",
         "actionStrategy": "A1",
         "adaptiveCreateScore": "0",
         "adaptiveHighScore": "430",
         "primaryBirthDate": "1990-08-24",
         "otherBirthDate": "1990-08-24",
         "cardStatusAtCaseCreate": "Active",
         "cardTrackerSeverity": "5",
         "fraudApproach": "Minimum",
         "memberNumber": "0",
         "highTransactionDateTime": "2021-07-20T07:00:00Z",
         "lastAnalyst": "Analyst",
         "lastFraudCode": "CASE_FRAUD_TYPE_APP_FRD",
         "lastName": "Smith",
         "lastScore": "0",
         "lastTransactionDateTime": "2021-07-20T07:00:00Z",
         "OriginalAnalyst": "Analyst",
         "scoreToUse": "Base",
         "rules": "RuleManager Case Create"
      }
   ]
}
``` 
### Search Fraud Case Transactions with filter=AUTHORIZATIONS
Returns specified transactions associated with a case based on filter value "AUTHORIZATIONS"

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/transactions?filter=AUTHORIZATIONS

``` 
{
  "caseNumber" : "999999999"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
  "authTransactions": [
    {
      "transactionId": "0000001234",
      "disposition": "Not Fraud",
      "cardNumber": "400020XXXXXX4000",
      "transactionDateTime": "2021-07-20T07:00:00Z",
      "amount": "25.05",
      "authDecision": "D",
      "cardPresent": true,
      "baseScore": "0",
      "adaptiveScore": "0",
      "scoreUsed": "Base & Adaptive",
      "mcc": "1111",
      "merchantName": "Home Supply",
      "countryCode": "840",
      "countryAlpha": "US",
      "actionStrategy": "A1",
      "authReason": "O",
      "authResponse": "090",
      "authSubResponse": "G",
      "cv": "I",  "authResponse": "090",
      "authSubResponse": "G",
      "cardCapacity": "1",
      "eci": "0",
      "entryMode": "U",
      "mcEMSReasonCode": "45",
      "mcEMSScore": "0",
      "memberNumber": "0",
      "merchantCity": "New Jersey",
      "merchantIdentifier": "Home Supply",
      "merchantPostalCode": "12345",
      "merchantState": "NJ",
      "messageType": "136",
      "pin": "X",
      "realTimeResponse": "4250",
      "starScore": "0",
      "tokenAssuranceLevel": "23",
      "tokenId": "5046490000000004",
      "tokenRequestorId": "12345678901",
      "tokenizationIndicator": "S",
      "transType": "I",
      "transactionPOS": "2",
      "vaaRCC1": "12",
      "vaaRCC2": "34",
      "vaaRCC3": "56",
      "vaaRRC": "34",
      "vaaRTD": "",
      "vaaScore": "12"
    }
  ]
}
``` 
### Search Fraud Case Transactions with Optional Field caseTenant and filter=AUTHORIZATIONS
Search for fraud cases transactions based on request criteria caseNumber and caseTenant with filter value "AUTHORIZATIONS".

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/transactions?filter=AUTHORIZATIONS

``` 
{
    "caseNumber": "999999999",
    "caseTenant": "60"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "authTransactions": [
        {
		  "transactionId": "0000001234",
		  "disposition": "Not Fraud",
		  "cardNumber": "400020XXXXXX4000",
		  "transactionDateTime": "2021-07-20T07:00:00Z",
		  "amount": "25.05",
		  "authDecision": "D",
		  "cardPresent": true,
		  "baseScore": "0",
		  "adaptiveScore": "0",
		  "scoreUsed": "Base & Adaptive",
		  "mcc": "1111",
		  "merchantName": "Home Supply",
		  "countryCode": "840",
		  "countryAlpha": "US",
		  "actionStrategy": "A1",
		  "authReason": "O",
		  "authResponse": "090",
		  "authSubResponse": "G",
		  "cv": "I",
		  "cardCapacity": "1",
		  "eci": "0",
		  "entryMode": "U",
		  "mcEMSReasonCode": "45",
		  "mcEMSScore": "0",
		  "memberNumber": "0",
		  "merchantCity": "New Jersey",
		  "merchantIdentifier": "Home Supply",
		  "merchantPostalCode": "12345",
		  "merchantState": "NJ",
		  "messageType": "136",
		  "pin": "X",
		  "realTimeResponse": "4250",
		  "starScore": "0",
		  "tokenAssuranceLevel": "23",
		  "tokenId": "5046490000000004",
		  "tokenRequestorId": "12345678901",
		  "tokenizationIndicator": "S",
		  "transType": "I",
		  "transactionPOS": "2",
		  "vaaRCC1": "12",
		  "vaaRCC2": "34",
		  "vaaRCC3": "56",
		  "vaaRRC": "34",
		  "vaaRTD": "",
		  "vaaScore": "12"
		}
    ]
}
``` 
### Search Fraud Case Transactions with filter=DEPOSIT_AND_PAYMENTS
Returns specified transactions associated to a case based on filter value "DEPOSIT_AND_PAYMENTS"

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/transactions?filter=DEPOSIT_AND_PAYMENTS

``` 
{
  "caseNumber" : "999999999"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "depositAndPaymentTransactions": [
        {
            "transactionId": "1111115678",
            "disposition": "Not Fraud",
            "cardNumber": "400020XXXXXX4000",
            "transactionDateTime": "2021-07-20T07:00:00Z",
            "amount": "25.05",
            "authDecision": "D",
            "merchantName": "Home Supply",
            "countryCode": "840",
            "countryAlpha": "US",
            "actionStrategy": "A1",
            "authReason": "O",
            "authResponse": "090",
            "authSubResponse": "G",
            "memberNumber": "0",
            "transactionCity": "New Jersey",
            "merchantIdentifier": "Home Supply",
            "transactionPostalCode": "12345",
            "transactionState": "NJ",
            "messageType": "136",
            "realTimeResponse": "",
            "transType": "I",
            "transactionPOS": "2",
            "vaaRCC1": "42",
            "vaaRCC2": "23",
            "vaaRCC3": "11",
            "vaaRRC": "51",
            "vaaRTD": "2"
        }
    ]
}
``` 
### Search Fraud Case Transactions with Optional Field caseTenant and filter=DEPOSIT_AND_PAYMENTS
Search for fraud cases transactions based on request criteria caseNumber and optional fields with filter value "DEPOSIT_AND_PAYMENTS".

#### Request
**HTTP METHOD:**POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/transactions?filter=DEPOSIT_AND_PAYMENTS

``` 
{
    "caseNumber": "999999999",
    "caseTenant": "60",
    "pageLimit": 50,
    "pageOffset": 1
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "depositAndPaymentTransactions": [
        {
            "transactionId": "1111115678",
            "disposition": "Not Fraud",
            "cardNumber": "400020XXXXXX4000",
            "transactionDateTime": "2021-07-20T07:00:00Z",
            "amount": "25.05",
            "authDecision": "D",
            "merchantName": "Home Supply",
            "countryCode": "840",
            "countryAlpha": "US",
            "actionStrategy": "A1",
            "authReason": "O",
            "authResponse": "090",
            "authSubResponse": "G",
            "memberNumber": "0",
            "transactionCity": "New Jersey",
            "merchantIdentifier": "Home Supply",
            "transactionPostalCode": "12345",
            "transactionState": "NJ",
            "messageType": "136",
            "realTimeResponse": "",
            "transType": "I",
            "transactionPOS": "2",
            "vaaRCC1": "42",
            "vaaRCC2": "23",
            "vaaRCC3": "11",
            "vaaRRC": "51",
            "vaaRTD": "2"
        }
    ]
}
``` 
### Update Fraud Case Details
Update the fraud case details

#### Request
**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases

``` 
{
    "caseNumber": "999999999",
    "caseStatus": "CLOSED_UNCONFIRMED_FRAUD",
    "cardStatus": "ACTIVE",
    "leftMessage": true,
    "contactedCardholder": true,
    "homePhoneValid": true,
    "workPhoneValid": true,
    "cellPhoneValid": true,
    "caseComments": "No Contact Found due to INVALID data",
    "transactionDetails": [
        {
            "transactionId": "1111115678",
            "transactionDisposition": "NOT_FRAUD"
        }
    ]
}
``` 
#### Response
**HTTP Code:** 204
```
Successful.
```
 

 
### Update Fraud Case Details with caseTenant
Update the fraud case details with caseTenant

#### Request
**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases

``` 
{
  "caseNumber": "999999999",
  "caseTenant": "60",
  "caseStatus": "CLOSED_UNCONFIRMED_FRAUD",
  "fraudCode": "APPLICATION_FRAUD",
  "cardStatus": "ACTIVE",
  "leftMessage": true,
  "contactedCardholder": true,
  "homePhoneValid": true,
  "workPhoneValid": true,
  "cellPhoneValid": true,
  "caseComments": "No Contact Found due to INVALID data",
  "transactionDetails": [
    {
      "transactionId": "1111115678",
      "transactionDisposition": "NOT_FRAUD"
    }
  ]
}
``` 
#### Response
**HTTP Code:** 204
```
Successful.
```
## Exemptions
### Retrieve Fraud Travel Exemptions Countries List.
Retrieve Countries list for Fraud Travel Exemptions. locationFilter value will be COUNTRY for fetching the Countries list.

#### Request
**HTTP METHOD:** GET

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/exemptions/travel/locations?locationFilter=COUNTRY

#### Response
**HTTP Code:** 200
```
{
    "locations": [
        {
            "code": "AFG",
            "name": "AFGHANISTAN"
        },
        {
            "code": "ALA",
            "name": "ALAND ISLANDS"
        },
        {
            "code": "ALB",
            "name": "ALBANIA"
        },
        {
            "code": "DZA",
            "name": "ALGERIA"
        }
    ]
}
```
### Retrieve Fraud Travel Exemptions States List.
Retrieve States list for Fraud Travel Exemptions. locationFilter value will be STATE for fetching the States list.

#### Request
**HTTP METHOD:** GET

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/exemptions/travel/locations?locationFilter=STATE

#### Response
**HTTP Code:** 200
```
{
    "locations": [
        {
            "code": "AL",
            "name": "ALABAMA"
        },
        {
            "code": "AK",
            "name": "ALASKA"
        },
        {
            "code": "AZ",
            "name": "ARIZONA"
        },
        {
            "code": "AR",
            "name": "ARKANSAS"
        }
    ]
}
```
### Retrieve Countries/States list without location filter 
BAD Request Response for locations for Fraud Travel Exemptions without locationFilter parameter.

#### Request
**HTTP METHOD:** GET

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/exemptions/travel/locations

#### Response
**HTTP Code:** 400
```
{
    "status": "400",
    "path": "/api/fraud/v1/exemptions/locations",
   "instance": "/cs/fraud/v1/exemptions/travel/locations",
    "type": "https://card.developer.fiserv.com/fraud/error#invalid-request",
    "title": "Invalid Request"

}
```
## Rules
### Search Fraud Cases Rules with Required Fields Only
Search for fraud cases rules based on required field caseNumber.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/rules

``` 
{
  "caseNumber": "999999999"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
  "associatedRulesAndTransactions": [
    {
      "transactionId": "0000001234",
      "createdCase": true,
      "reactivatedCase": false,
      "rules": [
        {
          "ruleFiredDateTime": "2021-07-20T07:00:00Z",
          "ruleSet": "decision_DBTRAN25",
          "ruleName": "RuleManager Case Create"
        }
      ]
    }
  ]
}
```
### Search Fraud Cases Rules with Required Fields and Optional Field
Search for fraud cases rules based on required field caseNumber and optional field caseTenant.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cases/rules

``` 
{
  "caseNumber": "999999999",
  "caseTenant": "60"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
  "associatedRulesAndTransactions": [
    {
      "transactionId": "0000001234",
      "createdCase": true,
      "reactivatedCase": false,
      "rules": [
        {
          "ruleFiredDateTime": "2021-07-20T07:00:00Z",
          "ruleSet": "decision_DBTRAN25",
          "ruleName": "RuleManager Case Create"
        }
      ]
    }
  ]
}
```
## Verification

### Verification CardAuthInfo Using CardNumber, Member Number, OTP and JWT
Retrieves CV2 and expirationDate for given card by validating OTP and JWT.
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/verification/cardAuthInfo
```
{
  "cardNumber": "4000200030004000",
  "memberNumber": "0",
  "otp": "123456",
  "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "CV2": "282",
  "expirationDate": "10/28"
}
```

### Verification CardAuthInfo Using CardNumber, OTP and JWT
Retrieves CV2 and expirationDate for given card by validating OTP and JWT.
#### Request
**HTTP METHOD:** POST

**Target URL: **https://card-sandbox.api.fiservapps.com/cs/fraud/v1/verification/cardAuthInfo
```
{
  "cardNumber": "4000200030004000",
  "otp": "123456",
  "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "CV2": "282",
  "expirationDate": "10/28"
}
```

### Verification CardAuthInfo Using NTT, Member Number, OTP and JWT
Retrieves CV2 and expirationDate for given card by validating OTP and JWT..
#### Request
**HTTP METHOD:** POST

**Target URL: **https://card-sandbox.api.fiservapps.com/cs/fraud/v1/verification/cardAuthInfo
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0",
  "otp": "123456",
  "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "CV2": "282",
  "expirationDate": "10/28"
}
```

### Verification CardAuthInfo Using NTT, OTP and JWT
Retrieves CV2 and expirationDate for given card by validating OTP and JWT.
#### Request
**HTTP METHOD:** POST

**Target URL: **https://card-sandbox.api.fiservapps.com/cs/fraud/v1/verification/cardAuthInfo
```
{
  "nonTransToken": "piUVBJKZGfks4000",
  "otp": "123456",
  "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "CV2": "282",
  "expirationDate": "10/28"
}
```

### Verification CardAuthInfo Using OTP and JWT
Retrieves CV2 and expirationDate for given card by validating OTP and JWT.
#### Request
**HTTP METHOD:** POST

**Target URL: **https://card-sandbox.api.fiservapps.com/cs/fraud/v1/verification/cardAuthInfo
```
{
  "otp": "123456",
  "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
  "cardNumber": "4000200030004000",
  "CV2": "282",
  "expirationDate": "10/28"
}
```


### Retrieve Verification Options Using cardNumber and nonTransToken
Retrieves allowed and available media addresses for cardholder's Verification. Possible media address types are Voice, Text, and Email. Media addresses are semi-masked for cardholder's confidentiality.
#### Request
**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/search
```
{
  "cardNumber": "4000200030004000",
  "nonTransToken": "piUVBJKZGfks4000",
  "memberNumber": "0"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "contact": {
        "emailAddress": "ale******@example.com",
        "homePhone": "******0001",
        "workPhone": "******0001",
        "cellPhone": "******0001",
        "textAddress": "******0001"
    }
}
```

### Retrieve Verification Options Using cardNumber Only
Retrieves allowed and available media addresses for cardholder's Verification. Possible media address types are Voice, Text, and Email. Media addresses are semi-masked for cardholder's confidentiality.
#### Request
**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/search
```
{
  "cardNumber": "4000200030004000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "contact": {
        "emailAddress": "ale******@example.com",
        "homePhone": "******0001",
        "workPhone": "******0001",
        "cellPhone": "******0001",
        "textAddress": "******0001"
    }
}
```

### Retrieve Verification Options Using cardNumber without nonTransToken
Retrieves allowed and available media addresses for cardholder's Verification. Possible media address types are Voice, Text, and Email. Media addresses are semi-masked for cardholder's confidentiality.
#### Request
**HTTP METHOD:** POST

**Target URL:**  https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/search
```
{
  "cardNumber": "4000100020003000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400010XXXXXX3000",
    "memberNumber": "0",
    "contact": {
        "emailAddress": "ale******@example.com",
        "homePhone": "******0001",
        "workPhone": "******0001",
        "cellPhone": "******0001",
        "textAddress": "******0001"
    }
}
```

### Retrieve Verification Options Using nonTransToken Only
Retrieves allowed and available media addresses for cardholder's Verification. Possible media address types are Voice, Text, and Email. Media addresses are semi-masked for cardholder's confidentiality.
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/search
```
{
  "nonTransToken": "piUVBJKZGfks4000"
}
```
#### Response
**HTTP Code:** 200 OK
```
{
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "contact": {
        "emailAddress": "ale******@example.com",
        "homePhone": "******0001",
        "workPhone: "******0001",
        "cellPhone": "******0001",
        "textAddress": "******0001"
    }
}
```


### Retrieve Verification Options v2 (Active)
Retrieves allowed and available media addresses for cardholder's Verification. Possible media address types are Voice, Text, and Email. Media addresses are semi-masked for cardholder's confidentiality.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v2/verification/search

``` 
{
   "cardNumber": "4000200030004000"
}
```
#### Response
**HTTP Code:** 200

``` 
{
    "cardNumber": "400020XXXXXX4000",
    "memberNumber": "0",
    "contact": {
        "voice": {
            "homePhone": "******2222",
            "workPhone": "******1112",
            "cellPhone": "******3222"
        },
        "email": {
            "emailAddress": "ale******@example.com"
        },
        "text": {
            "homePhone": "******2222",
            "workPhone": "******1112",
            "cellPhone": "******3222",
            "textAddress": "******3222"
        }
    }
}
``` 
### Retrieve Verification Options v1 (Deprecated)
Deprecated. Use v2 endpoint.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/verification/search

``` 
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "cardholderDemographics": [
      {
         "cardNumber": "400020XXXXXX4000",
         "cardholderName": "Doe, Alex",
         "dateOfBirth": "1998-01-01",
         "motherMaidenName": "Chris Doe",
         "ssn": "SRM6Z1234",
         "verificationText": "FISERV",
         "contact": {
            "voice": {
               "homePhoneNumber1": "*********0001",
               "workPhoneNumber1": "*********0001",
               "mobilePhoneNumber": "*********0001",
               "textAddress": "******0001"
            },
            "email": {
               "homeEmail": "ale****@email.com"
            },
            "enfact": {
               "enfactLanguagePreference": "ENGLISH"
            },
            "enfactVoice": {
               "homePhone": true,
               "workPhone": true,
               "mobilePhone": true,
               "homeEmail": true,
               "textAddress": true
            },
            "enfactText": {
               "homePhone": true,
               "workPhone": true,
               "mobilePhone": true,
               "homeEmail": true,
               "mobileText": true
            },
            "stepUpText": {
               "homePhone": true,
               "workPhone": true,
               "mobilePhone": true,
               "homeEmail": true,
               "mobileText": true
            },
            "stepUpVoice": {
               "homePhone": true,
               "workPhone": true,
               "mobilePhone": true,
               "homeEmail": true,
               "mobileText": true
            }
         }
      }
   ]
}
```
### Retrieve Generated Passcode Email Using cardNumber with nonTransToken
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "jwtTokenFlag": false,
      "mediaType": "EMAIL",
      "mediaAddress": "alexsmith@example.com"
  }
```
#### Response
**HTTP Code:** 201 Created
```
  {
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "otpId": "1234567",
      "status": "SUCCESS",
      "statusDescription": "SUCCESS",
      "mediaType": "EMAIL",
      "mediaAddress": "alexsmith@example.com"
  }
```

### Retrieve Generated Passcode Email Using Masked Media Address
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "jwtTokenFlag": true,
    "mediaType": "EMAIL",
    "mediaAddress": "ale******@example.com"
  }
```
#### Response
**HTTP Code:** 201 Created
```
  {
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "otpId": "1234567",
    "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg",
    "status": "SUCCESS",
    "statusDescription": "SUCCESS",
    "mediaType": "EMAIL",
    "mediaAddress": "ale******@example.com"
  }
```
### Retrieve Generated Passcode Email Using nonTransToken Only
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "jwtTokenFlag": false,
      "mediaType": "EMAIL",
      "mediaAddress": "alexsmith@example.com"
  }
```
#### Response
**HTTP Code:** 201 Created
```
  {
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "otpId": "1234567",
      "status": "SUCCESS",
      "statusDescription": "SUCCESS",
      "mediaType": "EMAIL",
      "mediaAddress": "alexsmith@example.com"
  }
```

### Retrieve Generated Passcode Text Using cardNumber with nonTransToken
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
      "cardNumber": "4000200030004000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "jwtTokenFlag": false,
      "mediaType": "TEXT",
      "mediaAddress": "1005550001"
  } 
```
#### Response
**HTTP Code:** 200 OK
```
  {
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "otpId": "1234567",
      "status": "SUCCESS",
      "statusDescription": "SUCCESS",
      "mediaType": "TEXT",
      "mediaAddress": "1005550001"
  }
```

### Retrieve Generated Passcode Text Using Masked Media Address
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
    "cardNumber": "4000200030004000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "jwtTokenFlag": true,
    "mediaType": "TEXT",
    "mediaAddress": "******0001"
  } 
```
#### Response
**HTTP Code:** 200 OK
```
  {
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "otpId": "1234567",
    "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg",
    "status": "SUCCESS",
    "statusDescription": "SUCCESS",
    "mediaType": "TEXT",
    "mediaAddress": "******0001"
  }
```


### Retrieve Generated Passcode Text Using nonTransToken Only
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "jwtTokenFlag": false,
      "mediaType": "TEXT",
      "mediaAddress": "1005550001"
  }
```
#### Response
**HTTP Code:** 201 Created
```
  {
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "otpId": "1234567",
      "status": "SUCCESS",
      "statusDescription": "SUCCESS",
      "mediaType": "TEXT",
      "mediaAddress": "1005550001"
  }
```


### Retrieve Generated Passcode Using cardNumber with Jwt
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
      "cardNumber": "4000200030004000",
      "memberNumber": "0",
      "jwtTokenFlag": true,
      "mediaType": "TEXT",
      "mediaAddress": "1005550001"
  }
```
#### Response
**HTTP Code:** 201 Created
```
  {
      "cardNumber": "400020XXXXXX4000",
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "otpId": "1234567",
      "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg",
      "status": "SUCCESS",
      "statusDescription": "SUCCESS",
      "mediaType": "TEXT",
      "mediaAddress": "1005550001"
  }
```



### Retrieve Generated Passcode Using cardNumber without member number
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
    "cardNumber": "4000200030004000",
    "jwtTokenFlag": true,
    "mediaType": "EMAIL",
    "mediaAddress": "alexsmith@example.com" 
  }
```
#### Response
**HTTP Code:** 201 Created
```
  {
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "otpId": "1234567",
    "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-U8_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom94jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH5L0XC_QqP5TIs3A15fqpAnvMaSwW9O_GDRzxnsUDCgEZCkwQOuEpWYDbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWbMzbindOIefIo4VTrOVMxWOdP_bLNId0E0CBLxSpRHX1u3EeAjUykUdifT2CP4bb6kbJf4pp0dRc_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy.FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUihzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4_eWyUwx4IYpYaJkPeUVd4ni_1eZMBy6-hPr3n39DES_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZcFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6uyCaOnyuWuE_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKwCNM.TOYk3lw2SKYamQL7XiLXlg",
    "status": "SUCCESS",
    "statusDescription": "SUCCESS",
    "mediaType": "EMAIL",
    "mediaAddress": "alexsmith@example.com"
  }
```


### Retrieve Generated Passcode Using cardNumber without nonTransToken
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
      "cardNumber": "4000100020003000",
      "memberNumber": "0",
      "mediaType": "TEXT",
      "mediaAddress": "1005550001"
  }
```
#### Response
**HTTP Code:** 201 Created
```
  {
      "cardNumber": "400010XXXXXX3000",
      "memberNumber": "0",
      "otpId": "1234567",
      "status": "SUCCESS",
      "statusDescription": "SUCCESS",
      "mediaType": "TEXT",
      "mediaAddress": "1005550001"
  }
```


### Retrieve Generated Passcode Using nonTransToken with Jwt
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
      "nonTransToken": "piUVBJKZGfks4000",
      "memberNumber": "0",
      "jwtTokenFlag": true,
      "mediaType": "EMAIL",
      "mediaAddress": "alexsmith@example.com"
  }
```
#### Response
**HTTP Code:** 201 Created
```
  {
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "otpId": "1234567",
    "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.XU56gXVBUVLIH83fDZ_uUNj-C4f2UpGnTbP0kHLKPFEfOjn0vYP-TCcV0Cy8Q5t0bRNxE_eI6LIRT-p-dL-lQkv5Sx1GXVvsC9L_vFBzz4QU2DbkpwVjVin088uA23OV6EhylCgiwf8Yswu_1Pu8jFyvaFJUIiEvwZkFbHX73IE6fJanhMjgn_4Eo42CVdGgmzYJtfDQ9wkbAW3w3D2C2dkvzQiYeiTTCkRdzIxEeTDcN9NSM_vwElz_zO5ONExRa_2LTPlQPcen9meot8Dzlcqlz0i4Jo2xtLmkG6bA2uQzbAID4dRujhaOhCoW-GodyOvRCjOqFNYHX8tVLBio7w.oDrfGhbXOLDEWBNA.avKcJYf5i_zP2fov70cqzEW0B2znGvIF2zdEp4bkRtSDJrRBKfcbJeEaEakLZaItLDAlXz6ANJLUntsCpyrQ0Jm4nWfjRgtVmWFSUF3TvgLUH8_Pd5e8yZsI_TuJCPDMHSIt8XEkrpyRwsQT8BgUIU-iAuGe70KoFK5Cr5qvGNLgKJDIwSzlaZma-z9HFxTs6m8hKM3_5YMK5AUGsSpsy8Fb6QNhE6enfjc3GeZei1_dwhJC3Cfd8NkeNpH8AkYWGrY_ZvyZ1YAfFdgXeasCAA.yxrJMUH91uZWejU5N1VDRQ",
    "status": "SUCCESS",
    "statusDescription": "SUCCESS",
    "mediaType": "EMAIL",
    "mediaAddress": "alexsmith@example.com"
  }
```


### Retrieve Generated Passcode Using nonTransToken without member number
Retrieves a one time passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.


#### Request

**HTTP METHOD:** POST
**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v3/verification/otp
```
  {
    "nonTransToken": "piUVBJKZGfks4000",
    "jwtTokenFlag": true,
    "mediaType": "EMAIL",
    "mediaAddress": "alexsmith@example.com" 
  }
```

#### Response
**HTTP Code:** 201 Created
```
  {
    "cardNumber": "400020XXXXXX4000",
    "nonTransToken": "piUVBJKZGfks4000",
    "memberNumber": "0",
    "otpId": "1234567",
    "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.XU56gXVBUVLIH83fDZ_uUNj-C4f2UpGnTbP0kHLKPFEfOjn0vYP-TCcV0Cy8Q5t0bRNxE_eI6LIRT-p-dL-lQkv5Sx1GXVvsC9L_vFBzz4QU2DbkpwVjVin088uA23OV6EhylCgiwf8Yswu_1Pu8jFyvaFJUIiEvwZkFbHX73IE6fJanhMjgn_4Eo42CVdGgmzYJtfDQ9wkbAW3w3D2C2dkvzQiYeiTTCkRdzIxEeTDcN9NSM_vwElz_zO5ONExRa_2LTPlQPcen9meot8Dzlcqlz0i4Jo2xtLmkG6bA2uQzbAID4dRujhaOhCoW-GodyOvRCjOqFNYHX8tVLBio7w.oDrfGhbXOLDEWBNA.avKcJYf5i_zP2fov70cqzEW0B2znGvIF2zdEp4bkRtSDJrRBKfcbJeEaEakLZaItLDAlXz6ANJLUntsCpyrQ0Jm4nWfjRgtVmWFSUF3TvgLUH8_Pd5e8yZsI_TuJCPDMHSIt8XEkrpyRwsQT8BgUIU-iAuGe70KoFK5Cr5qvGNLgKJDIwSzlaZma-z9HFxTs6m8hKM3_5YMK5AUGsSpsy8Fb6QNhE6enfjc3GeZei1_dwhJC3Cfd8NkeNpH8AkYWGrY_ZvyZ1YAfFdgXeasCAA.yxrJMUH91uZWejU5N1VDRQ",
    "status": "SUCCESS",
    "statusDescription": "SUCCESS",
    "mediaType": "EMAIL",
    "mediaAddress": "alexsmith@example.com"
  }
```



### Retrieve Generated Passcode Text v2 (Active)
Retrieves a one-time use passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v2/verification/otp

``` 
{
  "cardNumber": "4000200030004000",
  "cardMemberNumber": "0",
  "mediaType": "TEXT",
  "mediaAddress": "******0001"
}
```
 
#### Response
**HTTP Code:** 201

``` 
{
    "cardNumber": "***********4000",
    "memberNumber": "0",
    "cardType": "DEBIT",
    "otpId": "1234567",
    "status": "SUCCESS",
    "statusDescription": "SUCCEEDED",
    "mediaType": "TEXT",
    "mediaAddress": "******7366"
}
```
 
### Retrieve Generated Passcode Email v2 (Active)
Retrieves a one time use passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v2/verification/otp

``` 
{
  "cardNumber": "4000200030004000",
  "cardMemberNumber": "0",
  "mediaType": "EMAIL",
  "mediaAddress": "ale******@email.com"
}
```
 
#### Response
**HTTP Code:** 201 Created

``` 
{
    "cardNumber": "***********4000",
    "cardMemberNumber": "0",
    "cardType": "CREDIT",
    "otpId": "1234567",
    "status": "SUCCESS",
    "statusDescription": "SUCCEEDED",
    "mediaType": "EMAIL",
    "mediaAddress": "ale******@email.com"
}
```
### Retrieve Generated Passcode v1 (Deprecated)
Deprecated. Use v2.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/verification/otp

```
{
  "cardNumber": "4000200030004000",
  "cardMemberNumber": "0",
  "mediaType": "TEXT",
  "mediaAddress": "0005550001"
}
```
 
#### Response
**HTTP Code:** 201

``` 
{
    "cardNumber": "400020XXXXXX4000",
    "cardMemberNumber": "0",
    "cardType": "CREDIT",
    "otpId": "1560051",
    "status": "201",
    "statusDescription": "SUCCESS",
    "mediaType": "TEXT",
    "mediaAddress": "0005550001"
}
```
 
### Validate Passcode v2 (Active)
Validates generated passcode sent to Cardholder on chosen media address. Note passcode expires in 10 minutes.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/verification/validation

``` 
{
    "cardNumber": "4000200030004000",
    "memberNumber": "0",
    "otpId": "1234567",
    "otpPassCode": "123456"
}
```
 
#### Response
**HTTP Code:** 200

``` 
{
    "cardNumber": "400020XXXXXX4000",
    "memberNumber": "0",
    "cardType": "DEBIT",
    "otpId": "1816063",
    "status": "SUCCESS",
    "statusDescription": "SUCCESS"
}
```
### Validate Passcode v1 (Deprecated)
Deprecated. Use v2.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/verification/validation

``` 
{
    "cardNumber": "4000200030004000",
    "memberNumber": "0",
    "otpId": "1234567",
    "otpPassCode": "123456"
}
```
#### Response
**HTTP Code:** 200

``` 
{
    "cardNumber": "400020XXXXXX4000",
    "cardType": "DEBIT",
    "otpId": "1234567",
    "status": "SUCCESS",
    "statusDescription": "SUCCESS"
}
```
 
### Verification History
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud//v1/verification/history
```
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0",
   "fromDate": "1989-08-24",
   "toDate": "1990-08-24",
   "pageLimit": 50,
   "pageOffset": 1
}
```
#### Response
**HTTP Code:** 200
```
{
   "verificationHistory": [
      {
         "dateTime": "2021-07-20T07:00:00Z",
         "mediaType": "TEXT",
         "mediaAddress": "1005550001",
         "contactStatus": "SENT",
         "validationStatus": "VALID",
         "updatedByUser": "smith"
      }
   ]
}
```
## Fraud Alert
## Test Cases
### Notify Cardholder
Provides information to identify the given cardholder on the third party vendor’s system along with case and transaction data to allow the cardholder identify if a transaction is a fraud transaction. The URL is determined by the client when this service is configured by Fiserv.

#### Request
**HTTP METHOD:** POST

**Target URL:** /client/provided/uri


``` 
{
   "schemaVersion": "1.0.0",
   "clientId": "07100015",
   "system": "EPOC_CM",
   "clientApplicationName": "FRAUDALERTRWS",
   "clientVersion": "1.0.0",
   "clientVendorName": "ABC VENDOR",
   "clientAuditId": "Maria",
   "systemRecordIdentifier": "",
   "caseData": {
      "caseID": "60384538",
      "workflowCode": "14",
      "lastUpdated": "2019-07-26T11:43:34.291-04:00"
   },
   "cardData": {
      "accountID": "7766889911",
      "numberStart": "476171",
      "numberEnd": "0011",
      "cardholderFName": "JOHN",
      "cardholderLName": "POWER",
      "cardType": "Debit",
      "cardStatus": "R",
      "zip": "07811",
      "mediaAddress": [
         {
            "mediaAddressType": "VOICE",
            "mediaAddressData": "9643419064"
         }
      ]
   },
   "tranData": [
      {
         "tranId": "016001da2e000044",
         "tranDate": "2019-07-26T07:22:04.000-04:00",
         "tranAmount": 600,
         "merchantName": "NETFLIX COM",
         "merchantCity": "LOS GATOS",
         "merchantState": "CA",
         "merchantCntry": "840",
         "tranMcc": "4899",
         "decisionCode": "D"
      }
   ]
}
``` 
#### Response
**HTTP Code:** 200

 
```
{
  "schemaVersion":"1.0.0",
  "clientId":"07100015",
  "system":"EPOC_CM",
  "clientApplicationName":"FRAUDALERTRWS",
  "clientVersion":"1.0.0",
  "clientVendorName":"ABC VENDOR",
  "clientAuditId":"Maria",
  "systemRecordIdentifier":null,
  "csStatus": {
    "statusCode":"0",
    "statusDesc":"SUCCESSFUL",
    "additionalStatus":[],
    {
      "schemaVersion":"1.0.0",
      "clientId":"07100015",
      "system":"EPOC_CM",
      "clientApplicationName":"FRAUDALERTRWS",
      "clientVersion":"1.0.0",
      "clientVendorName":"ABC VENDOR",
      "clientAuditId":"Maria",
      "systemRecordIdentifier":null,
      "csStatus": {
        "statusCode":"0",
        "statusDesc":"SUCCESSFUL",
        "additionalStatus":[]
      },
    "caseID":"60384538",
    "alertVendorCaseId":""
  }
}
```
### Search for a Fraud Case
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/legate/fraud/v1/case/search

``` 
{
   "clientId": "07100015",
   "clientApplicationName": "FRAUDALERTRWS",
   "clientVendorName": "ABC VENDOR",
   "clientAuditId": "Maria",
   "systemRecordIdentifier": " ",
   "caseID": "60384538"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "caseData": [
      {
         "caseID": "60384538",
         "workflowCode": "14",
         "lastUpdated": "2019-07-26T11:43:34.291-04:00"
      }
   ],
   "tranData": [
      {
         "tranId": "016001da2e000044",
         "tranDate": "2019-07-26T07:22:04.000-04:00",
         "tranAmount": 600,
         "merchantName": "NETFLIX COM",
         "merchantCity": "LOS GATOS",
         "merchantState": "CA",
         "merchantCntry": "840",
         "tranMcc": "4899",
         "decisionCode": "D"
      }
   ]
}
```
### Alert Outcome
#### Request
**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/legate/fraud/v1/alertOutcome

``` 
{
   "clientId": "07100015",
   "clientApplicationName": "FRAUDALERTRWS",
   "clientVendorName": "ABC VENDOR",
   "clientAuditId": "Maria",
   "caseData": {
      "caseID": "60384538",
      "lastUpdated": "2019-07-26T11:43:34.291-04:00"
   },
   "tranResult": [
      {
         "result": "NO_FRAUD",
         "number": "177185"
      },
      {
         "result": "FRAUD",
         "number": "177186"
      }
   ],
   "cardStatusAction": "BLOCK",
   "Response": {
      "code": "APIBlock",
      "description": "Transaction identified as suspected fraud by cardholder via API. Requesting to restrict card status."
   },
   "subResponse": {
      "code": "",
      "description": ""
   },
   "notificationTimestamp": "2018-04-13T10:06:02.197-04:00"
}
``` 
#### Response
**HTTP Code:** 200

``` 
No Response body on success.
```
### Close a Fraud Case
#### Request
**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/legate/fraud/v1/caseClose

```
{
   "clientId": "07100015",
   "clientApplicationName": "FRAUDALERTRWS",
   "clientVendorName": "ABC VENDOR",
   "clientAuditId": "Maria",
   "caseData": {
      "caseID": "60384538",
      "lastUpdated": "2019-07-26T11:43:34.291-04:00"
   },
   "caseResultData": {
      "code": "61",
      "description": "Fraud"
   },
   "caseFinish": "2019-06-18T16:18:02.197-04:00"
}
``` 
#### Response
**HTTP Code:** 200

```
No Response body for a successful test.
```
## Fraud Alert
### Outbound API and References
**References**
Refer to these pages for important reference information.

[Fraud Alert Reference Outbound API](?path=/docs/gettingstarted/fred1.md)

[Fraud Alert Reference Codes](?path=/docs/release-notes/fraud/fraud-alert-reference-codes.md)

### Search Travel Exemptions
This operation searches and retrieves any existing travel exemptions created by a cardholder. Two travel exemption lists are possible. To add, update or remove travel exemptions, this search Request must be conducted first to understand what and if any lists exist for a cardholder. The following Request example for the cardholder, with PAN 222297976430017, returns 2 exemption lists with effective start and end dates, and the FI-applied exclusion codes.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/travel/v1/exemptions/search

``` 
{
   "client": {
      "id": "84014831",
      "applicationName": "OpenSystems",
      "vendorName": "Mobiliti",
      "auditId": "Mobiliti"
   },
   "cardholder": {
      "pan": "2222979764340017",
      "memberNumber": "0",
      "firstName": "SUMITRA",
      "middleInitial": "S",
      "lastName": "VEER",
      "zip": "20120"
   }
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
   "travelExemptions": [
      {
         "exemptionNumber": 1,
         "startDateTime": "2019-07-20T07:00:00Z",
         "endDateTime": "2020-07-31T03:59:00Z",
         "lastUpdatedDateTime": "2019-06-07T07:00:00Z",
         "exemptionCodes": {
            "stateCountryCodes": [
               "AFG"
            ]
         }
      },
      {
         "exemptionNumber": 2,
         "startDateTime": "2019-05-03T21:14:00Z",
         "endDateTime": "2019-05-16T20:16:00Z",
         "lastUpdatedDateTime": "2019-05-16T20:16:00Z",
         "exemptionCodes": {
            "stateCountryCodes": [
               "AL",
               "ARM",
               "AUS",
               "BIH",
               "BRA",
               "BRB",
               "BWA",
               "CA",
               "CT",
               "DE",
               "ID",
               "IL",
               "IOT",
               "GA"
            ]
         }
      }
   ],
   "exclusions": [
      {
         "code": "AGO",
         "type": "C"
      },
      {
         "code": "DZL",
         "type": "C"
      },
      {
         "code": "FL",
         "type": "S"
      },
      {
         "code": "GA",
         "type": "S"
      },
      {
         "code": "USA",
         "type": "C"
      }
   ]
}
```
### Add Travel Exemptions
Use to add new travel exemption data for the Requested card number or create a new list. Before you begin, retrieve the Travel Exemption List that includes FI exclusions.

**Important!** A cardholder can have a maximum of two travel plans on a specified card at any given time.

 * If two active travel exemptions exist, an error code results in the statusCode field of the  Response. To include the new information, update an existing list, or expire an existing list to add a new list.

 * If FI-specified exclusion codes are included in a new list Request, an error Response occurs.

 * If a cardholder has not created a list, the return displays an empty list, designated as [ ], but the FI-defined travel exclusions is listed.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/travel/v1/exemptions

``` 
{
   "client": {
      "id": "84014831",
      "applicationName": "OpenSystem",
      "vendorName": "Mobiliti",
      "auditId": "84014831"
   },
   "cardholder": {
      "pan": "2222979764340017",
      "memberNumber": "0",
      "firstName": "SUMITRA",
      "middleInitial": "",
      "lastName": "VEER",
      "zip": "20120"
   },
   "startDateTime": "2020-07-30T22:15:00Z",
   "endDateTime": "2020-08-11T10:50:00Z",
   "exemptionCodes": {
      "stateCountryCodes": [
         "CAN"
      ]
   }
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "travelExemptions": [
        {
            "exemptionNumber": 1,
            "startDateTime": "2020-07-30T22:15:00Z",
            "endDateTime": "2020-08-11T10:50:00Z",
            "lastUpdatedDateTime": "2019-11-19T18:12:00Z",
            "exemptionCodes": {
                "stateCountryCodes": [
                    "CAN"
                ]
            }
        },
        {
            "exemptionNumber": 2,
            "startDateTime": "2019-06-13T19:27:00Z",
            "endDateTime": "2019-06-14T19:27:00Z",
            "lastUpdatedDateTime": "2019-06-13T19:27:00Z",
            "exemptionCodes": {
                "stateCountryCodes": [
                    "AL",
                    "ARM",
                    "AUS",
                    "BIH",
                    "BRA",
                    "BRB",
                    "BWA",
                    "CA",
                    "CT",
                    "DE",
                    "ID",
                    "IL",
                    "IOT",
                    "GA"
                ]
            }
        }
    ],
    "exclusions": [
        {
            "code": "AGO",
            "type": "C"
        },
        {
            "code": "DZL",
            "type": "C"
        },
        {
            "code": "FL",
            "type": "S"
        },
        {
            "code": "GA",
            "type": "S"
        },
        {
            "code": "USA",
            "type": "C"
        }
    ]
}
```
### Update Travel Exemptions
You must first retrieve a travel exemption list for the Requested primary account number (PAN). Using this information, you can then make any necessary updates.

#### Request
**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/travel/v1/exemptions

``` 
{
   "client": {
      "id": "84014831",
      "applicationName": "OpenSystem",
      "vendorName": "Mobiliti",
      "auditId": "84014831"
   },
   "cardholder": {
      "pan": "2222979764340017",
      "memberNumber": "0",
      "firstName": "SUMITRA",
      "middleInitial": "",
      "lastName": "VEER",
      "zip": "20120"
   },
   "exemptionNumber": "1",
   "startDateTime": "2019-11-12T13:15:30Z",
   "endDateTime": "2019-12-15T13:15:30Z",
   "exemptionCodes": {
      "stateCountryCodes": [
         "CAN"
      ]
   }
}
``` 
Response
**HTTP Code:** 200

``` 
{
 "travelExemptions": [
   {
     "exemptionNumber": 1, 
     "startDateTime": "2019-11-12T13:15:00Z", 
     "endDateTime": "2019-12-15T13:15:00Z", 
     "lastUpdatedDateTime": "2019-11-19T18:12:00Z", 
     "exemptionCodes": {
        "stateCountryCodes": [
           "CAN"
        ]
     }
    }
  ],
    "exclusions": [
  {
    "code": "AGO",
    "type": "C"
  },
  {
    "code": "DZL",
    "type": "C"
  },
  {
    "code": "FL",
    "type": "S"
  },
  {
    "code": "GA",
    "type": "S"
  },
  {
    "code": "USA",
    "type": "C"
  }
 ]
}
```
### Expire Travel Exemptions
Use to expire a travel exemptions plan for the requested PAN. Before you begin, retrieve the specified card Travel Exemption List including FI exclusions.

Important! A cardholder can have a maximum of two travel plans on a specified card at any given time.

 * If two lists already exist, an error code results in the statusCode field of the response. To include the new information, an update request can be made to an existing list, or an existing list must first be expired so the new list can be added.

 * If FI-specified exclusion codes are included in a new list request, an error response occurs.

 * If a cardholder has not created a list, the return displays an empty list, designated as [ ], but the FI-defined travel exclusions is listed.
   
#### Request
**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/travel/v1/exemptions/expire

``` 
{
   "client": {
      "id": "84014831",
      "applicationName": "OpenSystems",
      "vendorName": "Mobiliti",
      "auditId": "Mobiliti"
   },
   "cardholder": {
      "pan": "2222979764340017",
      "memberNumber": "0",
      "firstName": "SUMITRA",
      "middleInitial": "S",
      "lastName": "VEER",
      "zip": "20120"
   },
   "exemptionNumber": "1"
}
 ```
#### Response
**HTTP Code**: 200

```
 
{
 "travelExemptions": [
   {
     "exemptionNumber": 1,
     "startDateTime": "2019-11-19T18:12:00Z",
     "endDateTime": "2019-11-19T18:12:00Z",
     "lastUpdatedDateTime": "2019-11-19T18:12:00Z",
     "exemptionCodes": {
     "stateCountryCodes": [
	   "AFG"
     ]
   }
 },
 {
    "exemptionNumber": 2,
    "startDateTime": "2019-05-03T21:14:00Z",
    "endDateTime": "2019-05-03T21:14:00Z",
    "lastUpdatedDateTime": "2019-05-03T21:14:00Z",
    "exemptionCodes": {
    "stateCountryCodes": [
               "AL",
               "ARM",
               "AUS",
               "BIH",
               "BRA",
               "BRB",
               "BWA",
               "CA",
               "CT",
               "DE",
               "ID",
               "IL",
               "IOT",
               "GA"
            ]
     }
   }
 ],
    "exclusions": [
  {
    "code": "AGO",
    "type": "C"
  },
  {
    "code": "DZL",
    "type": "C"
  },
  {
    "code": "FL",
    "type": "S"
  },
  {
    "code": "GA",
    "type": "S"
  },
  {
    "code": "USA",
    "type": "C"
  }
 ]
}
```
### References

Refer to these pages for important reference information.

[Country Currency Codes](?path=/docs/release-notes/fraud/country-currency-codes.md)

[Travel Exemptions Error Codes](?path=/docs/release-notes/fraud/travel-exemptions-error-codes.md)
