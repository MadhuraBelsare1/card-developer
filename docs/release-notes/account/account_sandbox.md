   ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACUAAAAlCAMAAADyQNAxAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAFxUExURQAAAP8AAICAgP+AAP9VAEBAQICAgP9mAFVVVW1tbVVVVXFxcWJiYmZmZmFhYWhoaP9oAGRkZGFhYWhoaP9kAGdnZ/9nAP9lAP9rAGNjY2ZmZmVlZWRkZP9lAGNjY2dnZ2VlZWNjY2dnZ/9lAP9kAGZmZv9mAP9lAGdnZ2ZmZmhoaGhoaGNjY2ZmZv9mAP9lAP9lAGVlZf9rAGVlZWRkZP9lAP9nAP9oAGVlZWZmZmVlZWdnZ2ZmZmhoaGVlZWZmZmRkZGZmZv9mAGhoaGRkZGZmZmhoaGlpaWhoaGRkZGZmZmhoaGVlZWVlZWZmZmdnZ2dnZ/9qAGRkZGZmZmVlZWVlZWdnZ2ZmZmhoaGlpaWpqamhoaGhoaP9sAGRkZGZmZmhoaGZmZmdnZ2dnZ2dnZ2ZmZmdnZ2lpaWZmZmhoaGdnZ2lpaWlpaWVlZWZmZmdnZ2lpaf9pAGdnZ2ZmZmdnZ2xsbG1tbW5ubm9vb/9vAP91AKGI4acAAABzdFJOUwABAgIDBAQFBgcJCQ0UFRYWFx0gISoqKyssLTAzNUNDREhISUpLS0xPUFFYWlpaW11tbm9wcnKMkJOVlZaWl5mbnp6foKCgoKSlpaWmp6evsLCysrPHx8jJysrLzNDT0+zt7e7z9PT09fX2+fr7+/v7+/2AJMj7AAAACXBIWXMAABcRAAAXEQHKJvM/AAAB9UlEQVQ4T3WU/V/SUBSHTyiIIaRYVkCgFiWppdkL5PKtzAyd1lLKDNKiF1Naynanf313d9/JuBefH7bn3J3PPrt35xwKMliYrR5ZzDqqzt0fxJpMfm2P1bf12aKmb9fZt7U81oNkNs2TD5OpRJh7OJEaN07MzYz36JzIzM/DxXQIkUsovXj4+3EEkaBv3t7JwVvkPtrzfXBOrOysJOBBEi+dcgxO0QWnFIVzLuHOiZacBf/JNFvthXJuvbsO4/SusmnP0gefr3gmmDq7B3MZ2D1Iu/ewYWbFAnhwehsmyJqGu9GR5rIXAymLXjVH+bmsH6cQe8hZqeP1ECX3DYRAziJjP0kFNo4IKFkTbIzmvl9DBJSsm3WNqpU4IqBkxStVauhtf7RDVkT/S5aGwEfJIs0iuwj3UbOKNlnP4T4PT+/AfPi7lO+aOrsLAxG9QTV5j0PPrsJAvFJTz0vBPa+CI529wqQzpv7H7v5uGDC+JpWa6Hr65UkXXCBqQq6vnqV/Sz1wwXJzhF/lWh16dAMmyJrv3Ubmdb87IBY64de93ENttHpI7scA0RI770eKvWGvO/b2ilO+DOfwOfFpGN4it9M2Jy6YOX9+zEiVQJkNPr8m2ubXhjy/XPJv99ivLV3js3DrolnowudqrWHZVqP2ohCYq0T/ASzGYHMoOcj7AAAAAElFTkSuQmCC)  **See [Using the Sandbox](/documentation/api-portal-card-developers/how-validate-apis-sandbox) before executing test cases.**

### Account

#### [Test Cases](#grpdiv888)

### [Retrieve Statement with Detail Filter](#collapse654)

Returns full detail information.

### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/statements/search?filter=detail

 
{
   "accountNumber": "123456789",
   "fromDate": "2022-01-09",
   "toDate": "2022-01-09"
}
 

### Response

HTTP Code: 200

 
{
    "cardNumber": \[
        "400020XXXXXX4000"
    \],
    "statementDetails": \[
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-10",
            "statementOpeningBalanceAmount": "0.00",
            "statementDebitAmount": "0.00",
            "statementSalesAmount": "0.00",
            "statementOtherCreditsAmount": "0.00",
            "statementPaymentAmount": "0.00",
            "externalAccountStatusCode": "NORMAL",
            "yearToDateInterestAmount": "0.00",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "0",
            "daysInBillingCycle": "31",
            "billingCycleCode": "9",
            "sinceLastStatementInterestAmount": "0.00",
            "overlimitFees": "0.00",
            "skipPaymentFlag": "No",
            "statementCreditLineAmount": "670000.00",
            "availableCreditRemaining": "669962.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "0.00",
                "credit": "0.00",
                "payment": "0.00",
                "purchase": "0.00"
            }
        },
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-10",
            "statementOpeningBalanceAmount": "0.00",
            "statementDebitAmount": "0.00",
            "statementSalesAmount": "0.00",
            "statementOtherCreditsAmount": "0.00",
            "statementPaymentAmount": "0.00",
            "externalAccountStatusCode": "NORMAL",
            "yearToDateInterestAmount": "0.00",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "0",
            "daysInBillingCycle": "31",
            "billingCycleCode": "9",
            "sinceLastStatementInterestAmount": "0.00",
            "overlimitFees": "0.00",
            "skipPaymentFlag": "No",
            "statementCreditLineAmount": "670000.00",
            "availableCreditRemaining": "669962.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "0.00",
                "credit": "0.00",
                "payment": "0.00",
                "purchase": "0.00"
            }
        },
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-10",
            "statementOpeningBalanceAmount": "0.00",
            "statementDebitAmount": "0.00",
            "statementSalesAmount": "0.00",
            "statementOtherCreditsAmount": "0.00",
            "statementPaymentAmount": "0.00",
            "externalAccountStatusCode": "NORMAL",
            "yearToDateInterestAmount": "0.00",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "0",
            "daysInBillingCycle": "30",
            "billingCycleCode": "9",
            "sinceLastStatementInterestAmount": "0.00",
            "overlimitFees": "0.00",
            "skipPaymentFlag": "No",
            "statementCreditLineAmount": "670000.00",
            "availableCreditRemaining": "669962.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "0.00",
                "credit": "0.00",
                "payment": "0.00",
                "purchase": "0.00"
            }
        },
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-10",
            "statementOpeningBalanceAmount": "0.00",
            "statementDebitAmount": "0.00",
            "statementSalesAmount": "0.00",
            "statementOtherCreditsAmount": "0.00",
            "statementPaymentAmount": "0.00",
            "externalAccountStatusCode": "NORMAL",
            "yearToDateInterestAmount": "0.00",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "0",
            "daysInBillingCycle": "31",
            "billingCycleCode": "9",
            "sinceLastStatementInterestAmount": "0.00",
            "overlimitFees": "0.00",
            "skipPaymentFlag": "No",
            "statementCreditLineAmount": "670000.00",
            "availableCreditRemaining": "669962.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "0.00",
                "credit": "0.00",
                "payment": "0.00",
                "purchase": "0.00"
            }
        },
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-10",
            "statementOpeningBalanceAmount": "0.00",
            "statementDebitAmount": "0.00",
            "statementSalesAmount": "0.00",
            "statementOtherCreditsAmount": "0.00",
            "statementPaymentAmount": "50.00",
            "externalAccountStatusCode": "NORMAL",
            "yearToDateInterestAmount": "0.00",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "2",
            "daysInBillingCycle": "30",
            "billingCycleCode": "9",
            "sinceLastStatementInterestAmount": "0.00",
            "overlimitFees": "0.00",
            "skipPaymentFlag": "No",
            "statementCreditLineAmount": "660000.00",
            "availableCreditRemaining": "659962.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "50.00",
                "credit": "0.00",
                "payment": "11.00",
                "purchase": "0.00"
            },
            "statementTransactionDetails": {
                "count": 4,
                "statementTransactions": \[
                    {
                        "CardOrAccountNumber": "400020XXXXXX4000",
                        "CardorAccountTransactions": \[
                            {
                                "transactionDate": "2022-01-09",
                                "postDate": "2022-01-09",
                                "transactionCode": "271",
                                "merchantDescription": "PAYMENT - THANK YOU",
                                "issuerAmount": "10.00",
                                "transactedCardOrAccountNumber": "400020XXXXXX4000",
                                "merchantCategoryCode": "06010",
                                "merchantAccount": "425769000002808",
                                "transactionAccountNumber": "400020XXXXXX4000",
                                "merchandiseDescription": "PAYMENT - THANK YOU",
                                "currencyCode": "840"
                            },
                            {
                                "transactionDate": "2022-01-09",
                                "postDate": "2022-01-09",
                                "transactionCode": "271",
                                "merchantDescription": "PAYMENT - THANK YOU",
                                "issuerAmount": "10.00",
                                "transactedCardOrAccountNumber": "400020XXXXXX4000",
                                "merchantCategoryCode": "06010",
                                "merchantAccount": "425769000002808",
                                "transactionAccountNumber": "400020XXXXXX4000",
                                "merchandiseDescription": "PAYMENT - THANK YOU",
                                "currencyCode": "840"
                            }
                        \]
                    },
                    {
                        "CardOrAccountNumber": "123456789",
                        "CardorAccountTransactions": \[
                            {
                                "transactionDate": "2022-01-09",
                                "postDate": "2022-01-09",
                                "transactionCode": "997",
                                "merchantDescription": "TEST GUY",
                                "issuerAmount": "10.00",
                                "transactedCardOrAccountNumber": "400020XXXXXX4000",
                                "merchantCategoryCode": "00006",
                                "merchantAccount": "425769000002055",
                                "transactionAccountNumber": "400020XXXXXX4000",
                                "merchandiseDescription": "TEST GUY",
                                "currencyCode": "840"
                            },
                            {
                                "transactionDate": "2022-01-09",
                                "postDate": "2022-01-09",
                                "transactionCode": "254",
                                "merchantDescription": "CASH ADVANCE",
                                "issuerAmount": "10.00",
                                "transactedCardOrAccountNumber": "123456789",
                                "merchantCategoryCode": "00006",
                                "merchantAccount": "425769000002055",
                                "transactionAccountNumber": "123456789",
                                "merchandiseDescription": "CASH ADVANCE",
                                "currencyCode": "840"
                            }
                        \]
                    }
                \]
            }
        }
    \]
}
 

### [Retrieve Statement with Summary Filter](#collapse655)

Returns summary information only.

### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/statements/search?filter=summary

 
{
   "accountNumber": "123456789",
   "fromDate": "2022-01-09",
   "toDate": "2022-01-09"
}
 

### Response

HTTP Code: 200

 
{
    "statementDetails": \[
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-10",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "0",
            "billingCycleCode": "9",
            "overlimitFees": "0.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "0.00",
                "credit": "0.00",
                "payment": "0.00",
                "purchase": "0.00"
            }
        },
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-10",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "0",
            "billingCycleCode": "9",
            "overlimitFees": "0.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "0.00",
                "credit": "0.00",
                "payment": "0.00",
                "purchase": "0.00"
            }
        },
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-10",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "0",
            "billingCycleCode": "9",
            "overlimitFees": "0.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "0.00",
                "credit": "0.00",
                "payment": "0.00",
                "purchase": "0.00"
            }
        },
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-10",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "0",
            "billingCycleCode": "9",
            "overlimitFees": "0.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "0.00",
                "credit": "0.00",
                "payment": "0.00",
                "purchase": "0.00"
            }
        },
        {
            "statementTransactionDetails": {
                "count": 4,
                "statementTransactions": \[
                    {
                        "CardOrAccountNumber": "400020XXXXXX4000",
                        "CardorAccountTransactions": \[
                            {
                                "transactionDate": "2022-01-09",
                                "postDate": "2022-01-09",
                                "transactionCode": "271",
                                "merchantDescription": "PAYMENT - THANK YOU",
                                "issuerAmount": "-00000000010.00",
                                "transactedCardOrAccountNumber": "400020XXXXXX4000",
                                "merchantCategoryCode": "06010",
                                "merchantAccount": "425769000002808",
                                "transactionAccountNumber": "400020XXXXXX4000",
                                "merchandiseDescription": "PAYMENT - THANK YOU",
                                "currencyCode": "840"
                            },
                            {
                                "transactionDate": "2022-01-09",
                                "postDate": "2022-01-09",
                                "transactionCode": "271",
                                "merchantDescription": "PAYMENT - THANK YOU",
                                "issuerAmount": "-00000000001.00",
                                "transactedCardOrAccountNumber": "400020XXXXXX4000",
                                "merchantCategoryCode": "06010",
                                "merchantAccount": "425769000002808",
                                "transactionAccountNumber": "400020XXXXXX4000",
                                "merchandiseDescription": "PAYMENT - THANK YOU",
                                "currencyCode": "840"
                            }
                        \]
                    },
                    {
                        "CardOrAccountNumber": "123456789",
                        "CardorAccountTransactions": \[
                            {
                                "transactionDate": "2022-01-09",
                                "postDate": "2022-01-09",
                                "transactionCode": "997",
                                "merchantDescription": "TEST GUY",
                                "issuerAmount": "000000000000.00",
                                "transactedCardOrAccountNumber": "400020XXXXXX4000",
                                "merchantCategoryCode": "00006",
                                "merchantAccount": "425769000002055",
                                "transactionAccountNumber": "400020XXXXXX4000",
                                "merchandiseDescription": "TEST GUY",
                                "currencyCode": "840"
                            },
                            {
                                "transactionDate": "2022-01-09",
                                "postDate": "2022-01-09",
                                "transactionCode": "254",
                                "merchantDescription": "CASH ADVANCE",
                                "issuerAmount": "000000000050.00",
                                "transactedCardOrAccountNumber": "123456789",
                                "merchantCategoryCode": "00006",
                                "merchantAccount": "425769000002055",
                                "transactionAccountNumber": "123456789",
                                "merchandiseDescription": "CASH ADVANCE",
                                "currencyCode": "840"
                            }
                        \]
                    }
                \]
            }
        }
    \]
}
 

### [No Records Found](#collapse656)

No records found based on request parameters.

### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/statements/search?filter=detail

 
{
    "accountNumber": "123456789",
    "fromDate": "2011-01-09",
    "toDate": "2011-01-10"
}
 

### Response

HTTP Code: 200

 
{
    "statementDetails": \[
        {
            "statementDate": "2022-01-09",
            "statementEndingBalance": "38.00",
            "delinquentAmount": "0.00",
            "statementFinanceChargeAmount": "0.00",
            "minimumPaymentDueAmount": "0.00",
            "paymentDueDate": "02-03",
            "purchaseCount": "0",
            "creditCount": "0",
            "paymentsCount": "0",
            "billingCycleCode": "9",
            "overlimitFees": "0.00",
            "statementTotals": {
                "adjustments": "0.00",
                "cashAdvance": "0.00",
                "credit": "0.00",
                "payment": "0.00",
                "purchase": "0.00"
            }
        }
    \],
    "warningInfo": {
        "message": "Transaction - RECORD NOT FOUND",
        "warningDetails": \[
            {
                "code": "304",
                "detail": "Transaction not found for statementDate 2022-01-09",
                "timestamp": "2022-02-28T04:48:47.029740"
            }
        \]
    }
}
 

#### [Error Handling](#grpdiv819)

### [Parameter: accountNumber](#collapse805)

**IDX**

**Scenario**

**Response**

1

Empty accountNumber.

{  
"accountNumber": "",  
"fromDate": "2011-01-09",  
"toDate": "2011-01-10"  
}

**HTTP** 400 Bad Request

{
    "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
    "title": "Invalid Request",
    "instance": "/cs/cards/v1/accounts/statements/search",
    "status": 400,
    "detail": "accountNumber is required"
}

**Solution:** Include accountNumber and resend.

2

Missing accountNumber.  
{

"fromDate": "2011-01-09",  
"toDate": "2011-01-10"  
}

**HTTP** 400 Bad Request

 
{
    "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
    "title": "Invalid Request",
    "instance": "/cs/cards/v1/accounts/statements/search",
    "status": "400",
    "detail": "accountNumber: must not be null"
}

**Solution:** Include accountNumber and resend.

3

Account not found.  
{  
"accountNumber": "1234567891",  
"fromDate": "2011-01-09",  
"toDate": "2011-01-10"  
}

**HTTP** 400 Bad Request

 
{
    "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
    "title": "Invalid Request",
    "instance": "/cs/cards/v1/accounts/statements/search",
    "status": "400",
    "detail": "ERROR: Statements - RECORD NOT FOUND"
}

**Solution:** Use different request values.