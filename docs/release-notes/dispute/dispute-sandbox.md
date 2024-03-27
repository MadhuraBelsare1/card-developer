# Test Cases

## <span style="color:#ff6600;">Dispute API Endpoints</span>

## Dispute Create
**Version 2**

### Create Dispute Case
Creates a dispute case for given transactions of a particular card number.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v2/cases/claim


```
{
        "cardNumber": "4000200030004000",
        "errorBehaviour": "ABORT_ON_FIRST_NO_ROLLBACK",
        "issuerOrAcquirer": "Issuer",
        "caseId": "999999999",
        "listOfTransactions": [
            {
                "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}"
            }
        ]
    }
```
#### Response
**HTTP Code:** 200


```
{
    "caseId": "999999999",
    "caseItemIds": [
        "999999999"
    ]
}
```
**Version 1**

### Create Dispute Case
Creates a draft case for given transactions on a particular card number.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/claim


```
{
    "cardNumber": "4000200030004000",
    "errorBehaviour": "ABORT_ON_FIRST_NO_ROLLBACK",
    "issuerOrAcquirer": "Issuer",
    "caseId": "999999999",
    "listOfTransactions": [
    {
        "transactionId": "{\"lifeCycleKey\":\"552508TVZBHP9604503456091\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}"
    }
    ]
}
```        
 
#### Response
**HTTP Code:** 200 OK
```
{
    "caseId": "999999999",
    "caseItemIds": [
        "999999999"
    ]
}
```        
### Submit Dispute Questionnaire
Submits the questionnaire for given case items.



### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/questionnaire
```
{
    "caseItemIds": [
        "999999999"
    ],
    "questionnaire": [
        {
            "questionName": "QuestVar_CaseItem.Unauth_Participation",
            "questionValue": "Yes"
        }
    ]
}
``` 
#### Response
**HTTP Code:** 200 OK
```
{
    "caseId": "999999999",
    "caseItemDetails": [
        {
            "caseItemType": "DISPUTE",
            "caseItemId": "999999999",
            "caseItemStatus": "QUEUED",
            "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE",
            "reasonCode": "112",
            "reasonCodeDescription": "Merchandise not as described"
        }
    ]
}
```
### Finalize Dispute Case
Finalize the case intake for a case item.

#### Request
**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/finalize


```
{
    "caseItemIds": [
        "999999999"
    ]
}
```
 
#### Response
**HTTP Code:** 200 OK


```
{
    "caseId": "999999999",
    "caseItemDetails": [
        {
            "caseItemId": "999999999",
            "caseItemStatus": "QUEUED",
            "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE"
        }
    ]
}
```

## Dispute Details
### Search Dispute Case by Card
Returns dispute case details for a given card number.

### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/searchByCard


```
{
    "cardNumber": "4000200030004000",
    "createFromDate": "1990-08-24",
    "createToDate": "1990-08-24",
    "claimAmountMin": 25.05,
    "claimAmountMax": 80.5,
    "dispositionIndicator": "UNRESOLVED"
}
```        
 
#### Response
**HTTP Code:** 200 OK


```
{
    "cardNumber": "400020XXXXXX4000",
    "cases": [
    {
        "caseId": "999999999",
        "role": "I",
        "roleDesc": "Issuer",
        "caseItems": [
        {
            "caseItemId": "999999999",
            "accountNumber": "123456XXX7789",
            "type": "DS",
            "typeDesc": "Dispute",
            "status": "Closed",
            "createdDateTime": "1990-08-24T07:00:00Z",
            "closedDateTime": "1990-08-24T07:00:00Z",
            "claimAmount": "200.50",
            "claimCurrency": "string",
            "reasonCode": "112",
            "reasonCodeDescription": "Merchandise not as described",
            "currentStep": 999,
            "issuerFiId": "12345678",
            "acquirerFiId": "87654321",
            "acquirerRefNum": "14515501298011980119806",
            "sequence": "121980",
            "transactionId": "SAHn1+FetxdAUmQ7xORwj7B9KvU= 10818616120200623 0210",
            "transactionDate": "1990-08-24",
            "transactionAmount": "200.50",
            "transactionCurrency": "US Dollar (USD)",
            "network": "VISA",
            "authorizationCode": "628934",
            "terminalId": "VMDIEOS1",
            "terminalName": "Home Supply",
            "stateCode": "299",
            "stateCodeDesc": "Case Closed",
            "completionCode": "390",
            "completionCodeDesc": "Closed - Claim resolved via RDR"
        }
        ]
    }
    ]
}
```        
### Retrieve Dispute Cases by CaseId
 

#### Request
**HTTP METHOD:** GET

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999

 
#### Response
**HTTP Code:**
```
{
    "caseId": "999999999",
    "cardNumber": "400020XXXXXX4000",
    "role": "I",
    "roleDesc": "Issuer",
    "caseItems": [
    {
        "caseItemId": "999999999",
        "accountNumber": "123456XXX7789",
        "type": "DS",
        "typeDesc": "Dispute",
        "status": "Closed",
        "createdDateTime": "2021-07-20T07:00:00Z",
        "closedDateTime": "2021-07-20T07:00:00Z",
        "claimAmount": "200.50",
        "claimCurrency": "US Dollar (USD)",
        "reasonCode": "112",
        "currentStep": 999,
        "issuerFiId": "12345678",
        "acquirerFiId": "87654321",
        "acquirerRefNum": "14515501298011980119806",
        "sequence": "121980",
        "transactionId": "SAHn1+FetxdAUmQ7xORwj7B9KvU= 10818616120200623 0210",
        "transactionDate": "1990-08-24",
        "transactionAmount": "200.50",
        "transactionCurrency": "US Dollar (USD)",
        "network": "VISA",
        "authorizationCode": "628934",
        "terminalId": "VMDIEOS1",
        "terminalName": "Home Supply",
        "stateCode": "299",
        "stateCodeDesc": "Case Closed",
        "completionCode": "390",
        "completionCodeDesc": "Closed - Claim resolved via RDR"
    }
    ]
}
```        
### Retrieve Dispute CaseItems Details
 

#### Request
**HTTP METHOD:** GET

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/caseItems/999999999

 
#### Response
**HTTP Code:** 200 OK
```
 {
    "transactionId": "SAHn1+FetxdAUmQ7xORwj7B9KvU= 10818616120200623 0210",
    "transactionDescription": "Transaction Description",
    "imageCount": "1",
    "adjustments": [
    {
        "id": "55748",
        "type": "CB",
        "typeDesc": "chargeback",
        "intExtType": "I",
        "amount": "20.00",
        "comment": "Credit Cardholder-Disputed Transaction",
        "status": "Done",
        "debitCreditIndicator": "C"
    }
    ],
    "history": [
    {
        "dateTime": "2021-07-20T07:00:00Z",
        "stepName": "EN",
        "description": "johndoe (Public): Item# 999999999:  200.05 04/21/220.   223 - PC credit issued"
    }
    ],
    "forms": [
    {
        "id": "12473205",
        "name": "FRM_Dispute_accepted_and_PC_Given",
        "sourceFileName": "sourceFile.pdf",
        "createdDateTime": "2021-07-20T07:00:00Z"
    }
    ],
    "networkReasonCode": "115"
}
```    
### Retrieve Dispute Case Document
 

#### Request
**HTTP METHOD:** GET


**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/caseItems/999999999/document/999999999

 
#### Response
**HTTP Code:** 200 OK

```
file.pdf
```        

## Dispute Update
Cancel Dispute Case
### Cancels dispute case.

#### Request
**HTTP METHOD:** DELETE

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/99999999

 
#### Response
**HTTP Code:** 204 No Content

```
Successful.
```

### Delete caseItems associated to caseId for Dispute Case - Scenario 1
 

#### Request
**HTTP METHOD:** DELETE

**Target URL:** https://card-sandbox.api.fiservapps.com/api/dispute/v1/cases/999999999/caseItems?caseItemId=999999999

 
#### Response
**HTTP Code:** 204 No Content

 
### Delete caseItems associated to caseId for Dispute Case Scenario 2
 

#### Request
**HTTP METHOD:** DELETE

**Target URL:** https://card-sandbox.api.fiservapps.com/api/dispute/v1/cases/999999999/caseItems?caseItemId=999999999&caseItemId=999999998

 
#### Response
**HTTP Code:** 206 Partial Success 

```
{
    "warningInfo": {
        "message": "caseItem(s) either are not in draft state to be able to be canceled or do not belong to the given caseId: [999999998].",
        "spanId": "c5ac93abafad5ccc",
        "traceId": "df35221b6ee5f9b5",
        "warningDetails": [
        {
            "code": "321",
            "detail": "caseItem(s) either are not in draft state to be able to be canceled or do not belong to the given caseId: [999999998].",
            "spanId": "c5ac93abafad5ccc",
            "timestamp": "2023-01-09T13:40:43.087958"
        }
        ]
    }
}
```
### Upload Dispute Case Document
Upload dispute case document.

#### Request
**HTTP METHOD:** POST

**HTTP Content-Type:** multipart/form-data; boundary=---boundary_marker

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/caseItems/999999999/document
```
Example curl for this endpoint:
    curl --location --#### Request POST 'https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/caseItems/999999999/document' \
        --header 'accept: application/json' \
        --header 'x-fapi-financial-id: 12345678' \
        --header 'Content-Type: multipart/form-data; boundary=' \
        --header 'Authorization: Bearer {token}' \
        --form 'document=@"{your_document}"'
    
Document size cannot exceed 10 MB. File types supported are pdf, tiff, jpeg, and png. Use the appropriate filename extension to indicate filetype.
```
#### Response
**HTTP Code:** 204 No Content
```
Successful.
```

