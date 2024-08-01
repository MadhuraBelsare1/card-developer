# Test Cases

<span style="color:#ff6600;">**Dispute API Endpoints**</span>

## Dispute create
**Version 3**

### Create claim V3: Single transaction ID
Creates a dispute case for given transactions of a particular card number.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v3/cases/claim

```
{
  "cardNumber": "4000200030004000",
  "listOfTransactions": [
    {
      "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}"
    }
  ]
}
```
#### Response
**HTTP Code:** 200 OK

```
{
  "caseId": "999999999",
  "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
  "caseItemIds": [
    "transactionID[{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}]:caseItemId[999999999]"
  ]
}
```

### Create claim V3: Multiple transaction IDs
Creates a dispute case for given transactions of a particular card number.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v3/cases/claim


```
{
  "cardNumber": "4000200030004000",
  "listOfTransactions": [
    {
      "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}"
    },
    {
      "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200527\"}"
    }
  ]
}
```
#### Response
**HTTP Code:** 200 OK

```
{
    "caseId": "999999999",
    "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
    "caseItemIds": [
        "transactionID[{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}]:caseItemId[999999999]",
        "transactionID[{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200527\"}]:caseItemId[999999998]"
    ]
}
```
### Create claim V3: Partial scenario
Creates a dispute case for given transactions of a particular card number.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v3/cases/claim


```
{
    "cardNumber": "4000200030004000",
    "listOfTransactions": [
        {
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}"
        },
        {
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200527\"}"
        },
        {
            "transactionId": "{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200528\"}"
        }
    ]
}
```
#### Response
**HTTP Code:** 206 Partial Successful

```
{
     "caseId": "999999999",
    "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
    "caseItemIds": [
        "transactionID[{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200526\"}]:caseItemId[999999999]",
        "transactionID[{\"lifeCycleKey\":\"12323301232312331\",\"activeKey\":\"0210\",\"duID\":\"11348539120200527\"}]:caseItemId[999999998]"
    ],
    "warningInfo": {
        "message": "Draft caseitem could not be created for some of the transactionId(s)",
        "warningDetails": [
            {
                "code": "321",
                "detail": "INFO: [3] transactionId - That transaction is already in use by 999999997.",
                "spanId": "b4a6e572-dbf3-4edb-9cb4-ea295d504aa2",
                "timestamp": "2023-01-09T13:40:43.087Z"
            }
        ]
    },
    "instance": "/api/basepath",
    "status": "206"
}
```

 
### Questionnaire withdrawal nonfraud
Submits a questionnaire for a case item. Questionnaires belongs in the Withdrawal-Nonfraud Flow.

#### Request
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
        },
        {
            "questionName": "QuestVar_CaseItem.ATMWDL_DSReason",
            "questionValue": "B" 
        },
        {
            "questionName": "QuestVar_CaseItem.ATM_ReceiveAmount",
            "questionValue": "10.00"
        },
        {
            "questionName": "QuestVar_CaseItem.AdditionalInformation",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.GeneralComments",
            "questionValue": "This is for testing Dispute Case"
        },
        {
            "questionName": "QuestVar_CaseItem.OralNotification",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.OralNotificationDate",
            "questionValue": "04/10/2023"
        }
    ]
}
``` 
#### Response
**HTTP Code:** 200 OK
```
{
  "caseId": "999999999",
  "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
  "caseItemDetails": [
    {
      "caseItemType": "DISPUTE",
      "caseItemId": "999999999",
      "caseItemStatus": "PENDING",
      "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE",
      "reasonCode": "105",
      "reasonCodeDescription": "CHARGED MORE THAN ONCE"
        }
    ]
}
```
###  Questionnaire deposit nonfraud: Multi caseItem
Submits the questionnaire for a case item. Questionnaires belongs to Deposit- Nonfraud Flow for Multi-case Items.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/questionnaire
```
{
   "caseItemIds": [
        "999999999"
        "999999998"
    ],
    "questionnaire": [
        {
            "questionName": "QuestVar_CaseItem.Unauth_Participation",
            "questionValue": "Yes"
        }    "caseItemIds": [
        "999999999"
        "999999998"
    ],
    "questionnaire": [
        {
            "questionName": "QuestVar_CaseItem.Unauth_Participation",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.SelectATMDSReason",
            "questionValue": "A" 
        },
        {
            "questionName": "QuestVar_CaseItem.Cash_or_Checks_Returned",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.AmountReturned",
            "questionValue": "10.00"
        },
        {
            "questionName": "QuestVar_CaseItem.TotalAmountofDispute",
            "questionValue": "5.00"
        },
        {
            "questionName": "QuestVar_CaseItem.AdditionalInformation",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.GeneralComments",
            "questionValue": "This is for testing Dispute Case"
        },
        {
            "questionName": "QuestVar_CaseItem.OralNotification",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.OralNotificationDate",
            "questionValue": "04/10/2023"
        }
    ]
}
``` 
#### Response
**HTTP Code:** 200 OK
```
{
 "caseId": "999999999",
  "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
  "caseItemDetails": [
    {
      "caseItemType": "DISPUTE",
      "caseItemId": "999999999",
      "caseItemStatus": "PENDING",
      "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE",
      "reasonCode": "101",
      "reasonCodeDescription": "DEPOSIT NOT POSTED"
    },
    {
      "caseItemType": "DISPUTE",
      "caseItemId": "999999998",
      "caseItemStatus": "PENDING",
      "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE",
      "reasonCode": "101",
      "reasonCodeDescription": "DEPOSIT NOT POSTED"
        }
    ]
}
```
### Questionnaire payment merchant: Nonfraud
Submits the questionnaire for a case item. Questionnaires belongs to Withdrawal- Nonfraud Flow.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/questionnaire
```
    "caseItemIds": [
        "999999999"
    ],
    "questionnaire": [
        {
            "questionName": "QuestVar_CaseItem.Unauth_Participation",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.DisputeCategory",
            "questionValue": "D" 
        },
        {
            "questionName": "QuestVar_CaseItem.SelectDisputeDetails",
            "questionValue": "A" 
        },
        {
            "questionName": "QuestVar_CaseItem.ChargesOnSameCard",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.HotelRentalCarChrg",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.FinalBill",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.ChargeDescription",
            "questionValue": "Yes" 
        },
        {
            "questionName": "QuestVar_CaseItem.Auth_MerchantDesc",
            "questionValue": "for purchasing product"
        },
        {
            "questionName": "QuestVar_CaseItem.DateValidCharge",
            "questionValue": "04/10/2024"    
        },
        {
            "questionName": "QuestVar_CaseItem.AmountofValidCharge",
            "questionValue": "15"
        },
        {
            "questionName": "QuestVar_CaseItem.DisputePortion",
            "questionValue": "A" 
        },
        {
            "questionName": "QuestVar_CaseItem.MerchContactAttemptMer",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.CaptureMerchResp",
            "questionValue": "Method - Email , Response - Try to resolve the issue at the earliest."    
        },
        {
            "questionName": "QuestVar_CaseItem.MerchantAttemptResolveDate",
            "questionValue": "01/14/2024"
        },
        {
            "questionName": "QuestVar_CaseItem.AdditionalInformation",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.GeneralComments",
            "questionValue": "This is for testing Dispute Case"
        },
        {
            "questionName": "QuestVar_CaseItem.OralNotification",
            "questionValue": "No"
        }
    ]
}
``` 
#### Response
**HTTP Code:** 200 OK
```
{
 "caseId": "999999999",
 "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
  "caseItemDetails": [
    {
      "caseItemType": "DISPUTE",
      "caseItemId": "999999999",
      "caseItemStatus": "PENDING",
      "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE",
      "reasonCode": "137",
      "reasonCodeDescription": "CHARGED INCORRECT AMOUNT"
        }
    ]
}
```


### Questionnaire fraud
Submits a questionnaire for a case item. Questionnaires belongs in the Fraud Flow.

#### Request
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
            "questionValue": "No"
        },
        {
            "questionName": "QuestVar_CaseItem.CardLostStolen",
            "questionValue": "Yes" 
        },
        {
            "questionName": "QuestVar_CaseItem.LostOrStolen",
            "questionValue": "A" 
        },
        {
            "questionName": "QuestVar_CaseItem.WhoUsedCard",
            "questionValue": "No"
        },
        {
            "questionName": "QuestVar_CaseItem.Unauth_AuthorizedUsers",
            "questionValue": "TEST"
        },
        {
            "questionName": " QuestVar_CaseItem.CardUsePermission",
            "questionValue": "Yes"
        },
        {  
            "questionName": " QuestVar_CaseItem.PINConsent",
            "questionValue": "No"
        },
        {
            "questionName": "QuestVar_CaseItem.AdditionalInformation",
            "questionValue": "Yes"
        },
        {
            "questionName": "QuestVar_CaseItem.GeneralComments",
            "questionValue": "This is for testing Dispute Case"
        },
        {
            "questionName": "QuestVar_CaseItem.OralNotification",
            "questionValue": "No"
        },
        {
            "questionName": "QuestVar_CaseItem.OralNotificationDate",
            "questionValue": "04/02/2024"
        }
    ]
}
``` 
#### Response
**HTTP Code:** 200 OK
```
{
  "caseId": "999999999",
  "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
  "caseItemDetails": [
    {
      "caseItemType": "FRAUD",
      "caseItemId": "999999999",
      "caseItemStatus": "PENDING",
      "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE",
      "reasonCode": "114",
      "reasonCodeDescription": "LOST"
        }
    ]
}
```

### Finalize case: Single case item
Finalize  intake for a case item.

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
  "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
  "caseItemDetails": [
    {
      "caseItemId": "999999999",
      "caseItemStatus": "QUEUED",
      "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE"
    }
  ]
}
```


### Finalize case: Multi case item
Finalize intake for a  case with multple caseItemIds.

#### Request
**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/finalize

```
{
   "caseItemIds": [
    "999999999",
    "999999998"
  ]
}
```
 
#### Response
**HTTP Code:** 200 OK

```
{
"caseId": "999999999",
 "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
  "caseItemDetails": [
    {
      "caseItemId": "999999999",
      "caseItemStatus": "QUEUED",
      "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE"
    },
    {
      "caseItemId": "999999998",
      "caseItemStatus": "QUEUED",
      "caseItemStateCodeDescription": "QUESTIONNAIRE_COMPLETE"
    }
  ]
}
```

## Dispute details

### Retreive cases by cardNumber
Returns dispute case details for a given card number.

#### Request
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
  "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
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
          "createdDateTime": "2021-07-20T07:00:00Z",
          "closedDateTime": "2021-07-20T07:00:00Z",
          "claimAmount": "200.50",
          "claimCurrency": "US Dollar (USD)",
          "reasonCode": "112",
          "reasonCodeDescription": "Merchandise not as described",
          "currentStep": 999,
          "issuerFiId": "12345678",
          "acquirerFiId": "87654321",
          "acquirerRefNum": "14515501298011980119806",
          "sequence": "121980",
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
   
### Retrieve cases by caseId
Returns dispute case details for a given caseId. 'caseId' must be unique, regardless of the number of transactions involved in a given case. 'caseItemId' must be unique to a single transaction in a given case.

#### Request
**HTTP METHOD:** GET

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999

#### Response
**HTTP Code:**  200 OK
```
{
  "caseId": "999999999",
  "cardNumber": "400020XXXXXX4000",
  "role": "I",
  "roleDesc": "Issuer",
  "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
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
    },
    {
      "caseItemId": "999999998",
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

### Retrieve caseItems details by caseID and caseItemIDs

 Returns dispute case Item details for a disputed transaction.

#### Request
**HTTP METHOD:** GET

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/caseItems/999999999

 
#### Response
**HTTP Code:** 200 OK
```
 {
  "transactionDescription": "Transaction Description",
  "imageCount": "1",
  "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
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
      "description": "johndoe (Public): Item# 123456789:  200.05 04/21/220.   223 - PC credit issued"
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

### Retrieve case document
Retrieves a document attached to a case item. 

**Note**: There are three parameters in URL:

   - CaseID- It must be unique, regardless of number of transactions involved in a given case creation.
   - CaseItemID- It must be unique to a single transaction in a given case.
   - DocID- It is a Document ID which is returned in Query Item Status.

#### Request
**HTTP METHOD:** GET

**Target URL:** https://card-sandbox.api.fiservapps.com/api/dispute/v1/cases/999999999/caseItems/999999999/document/987654321369

 
#### Response
**HTTP Code:** 200 OK

```
file.pdf
```

### View questionnaire
View submitted questionnaire answers for a completed case item. 

#### Request
**HTTP METHOD:** GET

**Target URL:**  https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/questionnaire/999999999

#### Response
**HTTP Code:** 200 OK

```
{
  "caseItemId": "999999999",
  "referenceId": "serv.net:___212344MBVKXK4K:0103b250-a424-4cd7-bfaa-807f0ff79d23",
  "questions": [
        {
            "questionName": "QuestVar_CaseItem.Unauth_Participation",
            "questionValue": "Yes",
            "questionDescription": "Did you participate in the transaction?"
        },
        {
            "questionName": "QuestVar_CaseItem.DisputeCategory",
            "questionValue": "C",
            "questionDescription": "Why are you disputing this transaction?"
        },
        {
            "questionName": "QuestVar_CaseItem.Auth_MerchantDesc",
            "questionValue": "Test",
            "questionDescription": "What did you purchase? Please be specific as possible. (Brand, size, color, etc.) "
        },
        {
            "questionName": "QuestVar_CaseItem.Merchnds_Or_Service",
            "questionValue": "B",
            "questionDescription": "Is this merchandise or a service?"
        },
        {
            "questionName": "Questvar_CaseItem.DisputeReasonService",
            "questionValue": "Test",
            "questionDescription": "Why are you dissatisfied with the service? (Please be as detailed as possible.)"
        },
        {
            "questionName": "QuestVar_CaseItem.RecurringCharge",
            "questionValue": "No",
            "questionDescription": "Is this a recurring charge?"
        },
        {
            "questionName": "QuestVar_CaseItem.DisputePortion",
            "questionValue": "A",
            "questionDescription": "How much of the transaction amount are you disputing?"
        },
        {
            "questionName": "QuestVar_CaseItem.MerchContactAttemptMer",
            "questionValue": "No",
            "questionDescription": "Did you attempt to contact the merchant to resolve the issue?"
        },
        {
            "questionName": "QuestVar_CaseItem.AdditionalInformation",
            "questionValue": "No",
            "questionDescription": "Is there any additional information you would like to provide?"
        },
        {
            "questionName": "QuestVar_CaseItem.OralNotification",
            "questionValue": "No",
            "questionDescription": "Change date of Oral Notification?"
        }
  ]
}
```        

## Dispute update
Updates dispute cases by canceling, finalizing, deleting, etc.

### Cancel a case
Cancels an open dispute case.

#### Request
**HTTP METHOD:** DELETE

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/99999999

#### Response
**HTTP Code:** 204 No Content

```
Successful.
```

### Delete caseItems associated with caseId: Single caseItemId
Deletes the caseItems associated with the caseId for a DisputeCase.

#### Request
**HTTP METHOD:** DELETE

**Target URL:** https://card-sandbox.api.fiservapps.com/api/dispute/v1/cases/999999999/caseItems?caseItemId=999999999

 
#### Response
**HTTP Code:** 204 No Content

### Delete caseItems associated with caseId: partial scenario
Deletes the caseItems associated with the caseId for a partial success DisputeCase.

#### Request
**HTTP METHOD:** DELETE

**Target URL:** https://card-sandbox.api.fiservapps.com/api/dispute/v1/cases/999999999/caseItems?caseItemId=999999999&amp;caseItemId=999999998&amp;caseItemId=999999997


#### Response
**HTTP Code:** 206 Partial Success
```
{
  "warningInfo": {
    "message": "caseItem(s) either are not in draft state to be able to be canceled or do not belong to the given caseId: [999999997].",
    "spanId": "c5ac93abafad5ccc",
    "traceId": "df35221b6ee5f9b5",
    "warningDetails": [
      {
        "code": "321",
        "detail": "caseItem(s) either are not in draft state to be able to be canceled or do not belong to the given caseId: [999999997].",
        "spanId": "c5ac93abafad5ccc",
        "timestamp": "2023-01-09T13:40:43.087958"
      }
    ]
  }
}
```


### Delete caseItems associated with caseId: Multi case itemID
Deletes the caseItems associated with a caseId for a multi-case DisputeCase 

#### Request
**HTTP METHOD:** DELETE

**Target URL:** https://card-sandbox.api.fiservapps.com/api/dispute/v1/cases/999999999/caseItems?caseItemId=999999999&amp;caseItemId=999999998

 
#### Response
**HTTP Code:** 204 No Content


### Upload case document
Attaches a document to a dispute case. The 'caseId' will be unique, regardless of number of transactions involved in a given case. 'caseItemId' is unique to a single transaction in a given case.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/caseItems/999999999/document
```
Example curl for this endpoint:
    curl --location 'https://card-sandbox.api.fiservapps.com/cs/dispute/v1/cases/999999999/caseItems/999999999/document' \
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
 
### Upload case note by caseId and caseItemId
 Update dispute case with notes.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/api/dispute/v1/cases/999999999/caseItems/999999999/note

```
{
   "notes": "string of notes"
}
```
 
#### Response
**HTTP Code:** 204 No Content

### Upload case document by caseId and caseItemId
Attaches a document to a dispute case. The'caseId' must be unique, regardless of number of transactions involved in a given case. The 'caseItemId' must be unique to a single transaction in a given case.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/api/dispute/v1/cases/999999999/caseItems/999999999/document

```
MULTIPART/FORM-DATA

document: Select a file to upload. The maximum size is 5 MB.
File name (fileName) and extension type: allowed file types are pdf, tiff, jpeg, or png. For example. Fpr example, if you are uploading a pdf file, the extension is ".pdf".
```
 
#### Response
**HTTP Code:** 204 No Content
