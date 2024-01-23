See Using the Sandbox before executing test cases. Tests must use only requests given here.

**Test Cases**

**Details**

##### Search Account with Summary Filter

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/search?filter=summary

``` 
{
    "accountNumber": "123456789" 
}
``` 
#### Response
HTTP Code: 200

``` 
{
    "accountType": "Consumer",
    "description": "VISA Classic",
    "customerName": "Doe, Jesse H",
    "association": "PRIMARY",
    "accountStatus": "NORMAL"
}
``` 
##### Search Account with Detail Filter

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/search?filter=detail

``` 
{
    "accountNumber": "123456789" 
}
``` 
#### Response
HTTP Code: 200

``` 
{
    "accountType": "Consumer",
    "description": "VISA Classic",
    "customerName": "Doe, Jesse H",
    "association": "PRIMARY",
    "accountStatus": "NORMAL",
    "accountStatusReason": "00–Normal",
    "accountTransferStatus": "NO_TRANSFER_INVOLVEMENT",
    "accountUsageStatus": "NEVER_ACTIVE",
    "authorizationCode": "0",
    "automaticPaymentCode": "4",
    "automaticPaymentFlag": "1",
    "cashBalance": "30.00",
    "currentBalanceAmount": "3000.00",
    "coveredByMilitaryLendingAct": true,
    "expirationDate": "02/2029",
    "highBalanceDate": "2022-01-09",
    "highBalanceAmount": "90.00",
    "interestAccrualCode": "2",
    "lastNonMonetaryDate": "2020-09-23",
    "lastStatementBalanceAmount": "2500.00",
    "lastStatusChangeDate": "2020-09-23",
    "memberId": "411411",
    "nextCycleDate": "2022-12-09",
    "openedDate": "2020-09-23",
    "plasticCount": 1,
    "prepayCode": "0",
    "secured": "NOT_SECURED",
    "serviceMember": false,
    "serviceStartDate": "2021-12-23",
    "serviceEndDate": "2021-11-23",
    "vip": true
}
```  
##### Limits Search
Successful search of Account Limits
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/limits/search
```
{

    "accountNumber": "123456789"

}
```
**Response**
HTTP Code: 200 OK
```
 {

   
    "currentBalanceAmount": "6457.72",
    "creditLimitAmount": "0000000000006000",
    "availableCreditAmount": "-457.00",
    "cashLimitAmount": "0000000000000070",
    "availableCashAmount": "-6387.00",
    "creditLineMaximumAmount": "0000000000030000",
    "temporaryCreditLine": true,
    "previousCreditLimitAmount": "000000000000000700",
    "temporaryCreditLimitAmount": "000000000000006000",
    "temporaryCreditLineEndDate": "2023-05-22",
    "billingCycle": "04",
    "lastpermanentCreditLimit": "000000000000800",
    "lastPermanentCreditLimitDate": "2023-02",
    "highBalanceDate": "2016-02-19",
    "highBalanceAmount": "6658.00"


}
```

**Limits Update**

Successful update of Account Limits

**Update Credit Limit**

#### Request
Update Credit Limit
**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/v1/limits
```
{

    "accountNumber": "123456789",
	 "creditLimit": 8000

} 
```
#### Response
**HTTP Code:** 204 No Content

 

**Update Cash Limit**

#### Request
**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/v1/limits
```
{

    "accountNumber": "123456789",
	"cashLimit": {
        "limitType": "AMOUNT",
        "amount": 5000
    }

} 
```
#### Response
**HTTP Code:** 204 No Content

 

**Update Temporary-Credit Limit**

#### Request
**Update Temporary-Credit Limit**
**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/v1/limits
```
{

    "accountNumber": "123456789",
	  "temporaryCreditLimit": {
		"setLimit": true,
		"amount": 5000,
		"endDate": "2024-06-30"
	}

}
```
#### Response
**HTTP Code:** 204 No Content


**Remove Temporary-Credit Limit**

#### Request
**Remove Temporary-Credit Limit**
**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com /cs/v1/limits

{

    "accountNumber": "123456789",
	  "temporaryCreditLimit": {
		"setLimit": false
	}

} 
#### Response
**HTTP Code**: 204 No Content

**Statements**

**Retrieve Statement with Detail Filter**

Returns full detail information.

#### Request
**HTTP METHOD:** POST

**Target URL:**   https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/statements/search?filter=detail

``` 
{
    "accountNumber": "123456789",
    "fromDate": "2020-12-09",
    "toDate": "2022-12-28"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "cardNumber": [
        "4257691000200020",
        "4257691000200021"
    ],
    "statementDetails": [
        {
            "statementDate": "2021-12-30",
            "statementEndingBalance": "1500.00",
            "delinquentAmount": "100.00",
            "statementFinanceChargeAmount": "10.00",
            "minimumPaymentDueAmount": "200.00",
            "paymentDueDate": "12-25",
            "statementOpeningBalanceAmount": "3000.00",
            "statementDebitAmount": "1500.00",
            "statementSalesAmount": "12.09",
            "statementOtherCreditsAmount": "15.15",
            "statementPaymentAmount": "400.00",
            "externalAccountStatusCode": "NORMAL",
            "yearToDateInterestAmount": "30.00",
            "purchaseCount": "15",
            "creditCount": "5",
            "paymentsCount": "10",
            "daysInBillingCycle": "31",
            "billingCycleCode": "28",
            "sinceLastStatementInterestAmount": "1.09",
            "overlimitFees": "5.00",
            "skipPaymentFlag": "No",
            "statementCreditLineAmount": "5000.00",
            "availableCreditRemaining": "4000.00",
            "statementTotals": {
                "adjustments": "99485.00",
                "cashAdvance": "1692.00",
                "credit": "10100.00",
                "payment": "665572.00",
                "purchase": "39181.00"
            },
            "statementTransactionDetails": {
                "totalTransactionsCount": 1,
                "statementTransactions": [
                    {
                        "cardOrAccountNumber": "4000200030004000",
                        "cardOrAccountTransactions": [
                            {
                                "authorizationCode": "606",
                                "currencyCode": "840",
                                "issuerAmount": "10.00",
                                "merchandiseDescription": "shoes",
                                "merchantAccount": "123456XXXXXX4067",
                                "merchantCategoryCode": "6010",
                                "merchantDescription": "Store1",
                                "merchantCity": "Newark",
                                "merchantState": "NJ",
                                "postDate": "2022-01-11",
                                "transactedCardOrAccountNumber": "400020XXXXXX4000",
                                "transactionAccountNumber": "123456XXXXXX4067",
                                "transactionCode": "251",
                                "transactionDate": "2021-04-24"
                            }
                        ]
                    }
                ]
            }
        }
    ]
}
 ```


**Retrieve Statement with Summary Filter** 

Returns summary information only.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/statements/search?filter=summary

``` 
{
    "accountNumber": "123456789",
    "fromDate": "2020-12-09",
    "toDate": "2022-12-28"
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "cardNumber": [
        "4257691000200020",
        "4257691000200021"
    ],
    "statementDetails": [
        {
            "statementDate": "2021-12-30",
            "statementEndingBalance": "1500.00",
            "delinquentAmount": "100.00",
            "statementFinanceChargeAmount": "10.00",
            "minimumPaymentDueAmount": "200.00",
            "paymentDueDate": "12-25"
        }
    ]
}
 ```


**Transactions**

**Retrieve Transaction Summary**
 

#### Request
**HTTP METHOD:** POST

**Target URL:** https://cardsandbox.api.fiservapps.com/cs/accounts/v1/accounts/transactions/search?filter=summary
```
{
    "accountNumber": "123456789",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-09-17"
        },
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-10-22"
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
            "transactionDateTime": "2022-10-22T19:50:40Z",
            "merchantName": "Store1",
            "authorizationCode": "121052",
            "transactionCode": "255",
            "transactionType": "Return",
            "merchantCategoryCode": "00000",
            "transactionStatus": "POSTED",
            "transactionAmount": "40.00"
        },
        {
            "transactionDateTime": "2022-09-17T04:00:00Z",
            "merchantName": "Store1",
            "authorizationCode": "121052",
            "transactionCode": "255",
            "transactionType": "Return",
            "merchantCategoryCode": "00000",
            "transactionStatus": "POSTED",
            "transactionAmount": "100.00"
        }
    ]
}
```
**Retrieve Transaction Summary with pageOffset and pageLimit**
 

#### Request
**HTTP METHOD:** POST

**Target URL:** https://cardsandbox.api.fiservapps.com/cs/accounts/v1/accounts/transactions/search?filter=summary&pageOffset=1&pageLimit=2
```
{
    "accountNumber": "123456789",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-09-17"
        },
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-10-22"
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
            "transactionDateTime": "2022-10-22T19:50:40Z",
            "merchantName": "Store1",
            "authorizationCode": "121052",
            "transactionCode": "255",
            "transactionType": "Return",
            "merchantCategoryCode": "00000",
            "transactionStatus": "POSTED",
            "transactionAmount": "40.00"
        },
        {
            "transactionDateTime": "2022-09-17T04:00:00Z",
            "merchantName": "Store1",
            "authorizationCode": "121052",
            "transactionCode": "255",
            "transactionType": "Return",
            "merchantCategoryCode": "00000",
            "transactionStatus": "POSTED",
            "transactionAmount": "100.00"
        }
    ]
}
```
**Retrieve Transaction Detail**
 

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/transactions/search?filter=detail
```
{
    "accountNumber": "123456789",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-09-17"
        },
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-10-22"
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
            "authorizationCode": "121052",
            "merchantCategoryCode": "00000",
            "merchantCity": "Newark",
            "merchantState": "NJ",
            "transactionDateTime": "2022-10-22T19:50:40Z",
            "transactedCardOrAccountNumber": "400020XXXXXX4000",
            "statusDescription": "64-PILOST",
            "merchantName": "Store1",
            "transactionCode": "255",
            "transactionType": "Return",
            "transactionStatus": "POSTED",
            "transactionAmount": "40.00",
            "responseCode": "096",
            "responseCodeDescription": "SYSTEM MALFUNCTION",
            "postedTransactionDetails": {
                "cardholderAccountNumber": "XXXXXXXXXXXX6789",
                "transactionDescription": "BALANCE TRANSFER CASH",
                "promotionId": "124",
                "postingDate": "2014-10-02",
                "detailTransactionIdentifier": "0000001234",
                "referenceNumber": "85548362L00XTMK3P"
            }
        },
        {
            "authorizationCode": "121052",
            "merchantCategoryCode": "00000",
            "merchantCity": "Newark",
            "merchantState": "NJ",
            "transactionDateTime": "2022-09-17T04:00:00Z",
            "transactedCardOrAccountNumber": "400020XXXXXX4000",
            "statusDescription": "64-PILOST",
            "merchantName": "Store1",
            "transactionCode": "255",
            "transactionType": "Return",
            "transactionStatus": "POSTED",
            "transactionAmount": "100.00",
            "responseCode": "096",
            "responseCodeDescription": "-NETWORK NOT FOUND",
            "postedTransactionDetails": {
                "cardholderAccountNumber": "XXXXXXXXXXXX6789",
                "transactionDescription": "BALANCE TRANSFER CASH",
                "promotionId": "124",
                "postingDate": "2014-11-20",
                "detailTransactionIdentifier": "0000001234",
                "referenceNumber": "76248362L00XTMK3P"
            }
        }
    ]
}
````
**Retrieve Transaction Detail with pageOffset and pageLimit**
 

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/transactions/search?filter=detail&pageOffset=1&pageLimit=2
```
{
    "accountNumber": "123456789",
    "filterCriteria": [
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-09-17"
        },
        {
            "filterBy": "FROM_DATE",
            "filterValue": "2022-10-22"
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
            "authorizationCode": "121052",
            "merchantCategoryCode": "00000",
            "merchantCity": "Newark",
            "merchantState": "NJ",
            "transactionDateTime": "2022-10-22T19:50:40Z",
            "transactedCardOrAccountNumber": "400020XXXXXX4000",
            "statusDescription": "64-PILOST",
            "merchantName": "Store1",
            "transactionCode": "255",
            "transactionType": "Return",
            "transactionStatus": "POSTED",
            "transactionAmount": "40.00",
            "responseCode": "096",
            "responseCodeDescription": "SYSTEM MALFUNCTION",
            "postedTransactionDetails": {
                "cardholderAccountNumber": "XXXXXXXXXXXX6789",
                "transactionDescription": "BALANCE TRANSFER CASH",
                "promotionId": "124",
                "postingDate": "2014-10-02",
                "detailTransactionIdentifier": "0000001234",
                "referenceNumber": "85548362L00XTMK3P"
            }
        },
        {
            "authorizationCode": "121052",
            "merchantCategoryCode": "00000",
            "merchantCity": "Newark",
            "merchantState": "NJ",
            "transactionDateTime": "2022-09-17T04:00:00Z",
            "transactedCardOrAccountNumber": "400020XXXXXX4000",
            "statusDescription": "64-PILOST",
            "merchantName": "Store1",
            "transactionCode": "255",
            "transactionType": "Return",
            "transactionStatus": "POSTED",
            "transactionAmount": "100.00",
            "responseCode": "096",
            "responseCodeDescription": "-NETWORK NOT FOUND",
            "postedTransactionDetails": {
                "cardholderAccountNumber": "XXXXXXXXXXXX6789",
                "transactionDescription": "BALANCE TRANSFER CASH",
                "promotionId": "124",
                "postingDate": "2014-11-20",
                "detailTransactionIdentifier": "0000001234",
                "referenceNumber": "76248362L00XTMK3P"
            }
        }
    ]
}
```





**Transactions**
