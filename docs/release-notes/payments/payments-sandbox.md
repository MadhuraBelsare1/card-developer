![image](https://github.com/Fiserv/card-developer/assets/159808568/149b79c1-1147-4b1e-a2ef-b0243d51f081)
# Test Cases

## <span style="color:#ff6600;">Payments API Endpoints</span>

## Payment Search

Tests must use only requests given here.![image](https://github.com/Fiserv/card-developer/assets/159808568/222cd667-c5e5-4644-8486-4610af2e9357)
![image](https://github.com/Fiserv/card-developer/assets/159808568/3df92881-615a-4153-9a2f-6fe11fecfcd9)

### Payment Search
This case searches for a payment.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/search

``` 
{
    "accountNumber": "123456789" 
}
``` 
#### Response
**HTTP Code:** 200 OK

``` 
{
    "count": 2,
    "payments": [
        {
            "paymentDate": "2023-12-15",
            "paymentAmount": "14.00",
            "dueDate": "2023-12-17",
            "effectiveDate": "2023-12-15",
            "cycleDate": "2023-11-22",
            "paymentDueAmount": "0.00",
            "daysDelinquent": "0",
            "reversalCode": "Not Reversed",
            "description": "Payments",
            "delinquentAmount": "0.00",
            "fixPaymentAmount": "0.00",
            "paymentTicketIdentifier": "349301656011603",
            "postDate": "2023-12-15",
            "transactionAmount": "-14.00",
            "transactionCode": "271",
            "interestFeesDistribution": [
                {
                    "paymentBalanceDescription": "REV CASH ADVANCE",
                    "balanceId": "0000000",
                    "paymentChangeToPrincipalAmount": "-14.00",
                    "paymentFeeAdjustmentAmount": "0.00"
                }
            ]
        },
        {
            "paymentDate": "2023-11-16",
            "paymentAmount": "40675.48",
            "dueDate": "2023-11-16",
            "effectiveDate": "2023-11-16",
            "cycleDate": "2023-10-22",
            "paymentDueAmount": "40675.48",
            "reversalCode": "Not Reversed",
            "description": "Payments",
            "daysDelinquent": "240",
            "delinquentAmount": "40675.48",
            "fixPaymentAmount": "0.00",
            "paymentTicketIdentifier": "320312500000001",
            "postDate": "2023-11-16",
            "transactionAmount": "-40675.48",
            "transactionCode": "271",
            "interestFeesDistribution": [
                {
                    "paymentBalanceDescription": "REV MERCHANDISE",
                    "balanceId": "0000000",
                    "paymentChangeToPrincipalAmount": "-9698.60",
                    "paymentFeeAdjustmentAmount": "-407.42"
                },
                {
                    "paymentBalanceDescription": "AHBALXFR",
                    "balanceId": "2217901",
                    "paymentChangeToPrincipalAmount": "-29532.98",
                    "paymentFeeAdjustmentAmount": "-1036.48"
                }
            ]
        }
     ]
   }
```

## Payment Actions

Tests must use only requests given here.

### Scheduled Payments
This case searches for a payment.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/scheduledPayments/search

``` 
{
  "accountNumber": "123456789",
    "registrationId": "1234567",
    "registrationLookup": "12345678"
}
``` 
#### Response
**HTTP Code:**  200 OK

``` 
 {
    "scheduleCount": 3,
    "scheduledPayments": [
        {
            "paymentDate": "2024-02-25",
            "paymentAmount": "100.00",
            "paymentType": "ONETIME_ACH",
            "routingNumberBankId": "123456789",
            "bankAccountNumber": "XXXXX6789",
            "paymentAccountType": "SAVINGS",
            "registrationId": "1234567",
            "confirmationNumber": "12345678",
            "recurringPaymentId": "12345",
            "appId": "1234",
            "transactionResultCode": "Payment_Pending",
            "paymentMedium": "eCheck"
        },
        {
            "paymentDate": "-",
            "paymentAmount": "-",
            "paymentType": "RECURRING_ACH",
            "routingNumberBankId": "123456789",
            "bankAccountNumber": "XXXXX6789",
            "paymentAccountType": "SAVINGS",
            "recurringPaymentType": "PayMinimumDue",
            "recurringStartDate": "2024-08-19",
            "recurringEndDate": "2024-12-20",
            "recurrenceDate": "ON_TIME_PAYMENT_DUE",
            "autoPaymentChargeDdaFlag": "I",
            "automaticPaymentCode": "I",
            "savingsAccountIdentifier": "XXXXX6789"
        },
        {
            "paymentDate": "2024-10-25",
            "paymentAmount": "100.00",
            "paymentType": "RECURRING_ACH",
            "routingNumberBankId": "123456789",
            "bankAccountNumber": "XXXXX6789",
            "paymentAccountType": "SAVINGS",
            "recurringPaymentType": "PayMinimumDue",
            "recurringStartDate": "2024-10-14",
            "recurringEndDate": "2024-12-11",
            "recurringCalendarDay": "25",
            "recurrenceDate": "SPECIFIC_DAY_MONTH",
            "registrationId": "1234567",
            "convenienceFeeRefundAmount": "0.00",
            "recurringPaymentId": "12345",
            "isDisabled": false,
            "recurringIntervalType": "Monthly",
            "intervalParam1": "Days",
            "intervalParam2": "25",
            "convFeeAmount": "0.00",
            "reference": "123456789002/08/2024",
            "appId": "1234",
            "nextPayDate": "2024-10-25",
            "createddate": "2024-02-08"
        }
    ]
}
```

### Reverse Right Time Payment
This API is used reverse a right time payment authorization.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/reverseRightTimePayment

``` 
{
    "merchantNumber": "123456789",
    "cardNumber": "4000200030004001",
    "paymentAmount": "05.09",
    "paymentSourceCode": "UNKNOWN",
    "paymentTypeCode": "UNKNOWN",
    "transactionDate": "2023-10-31"
}
``` 
#### Response
**HTTP Code:**  204 No Content

``` 
Reverse Right Time Payment Updated Succesfully.
```

### Reverse Right Time Payment
This API is used reverse a right time payment authorization.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/rightTimePayment

``` 
{
    "paymentAmount": "05.09",
    "transactionDate": "2023-10-31",
    "cardNumber": "4000200030004001"
}
``` 
#### Response
**HTTP Code:** 200 OK

``` 
Successful.
```

### Right Time Payment
This API is used to manage transactions.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/search?filter=summary

``` 
{
    "accountNumber": "123456789" 
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "count":
}
```

### Registered Account Search
This API is used search for registered accounts.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/registeredAccount/search

``` 
{
 "accountNumber": "123456789",
"registrationId": "1234567",
"registrationLookup": "12345678"
}
``` 
#### Response
**HTTP Code:** 200 OK

``` 
{
    "registeredAccounts": [
    {
        "registrationId": "1234567",
        "bankRoutingNumber": "123456789",
        "accountType": "SAVINGS",
        "bankAccountNumber": "1234",
        "nameFirst": "John",
        "namelast": "Doe",
        "nameFull": "johndoe",
        "paymentmedium": "eCheck"
    },
    {
        "registrationId": "1234567",
        "bankRoutingNumber": "123456789",
        "accountType": "SAVINGS",
        "bankAccountNumber": "1234",
        "nameFirst": "John",
        "namelast": "Doe",
        "nameFull": "johndoe",
        "paymentmedium": "eCheck"
    },
    {
        "registrationId": "1234567",
        "bankRoutingNumber": "123456789",
        "accountType": "SAVINGS",
        "bankAccountNumber": "1234",
        "nameFirst": "John",
        "namelast": "Doe",
        "nameFull": "johndoe",
        "paymentmedium": "eCheck"
    }
  ]
}
```

### Registered Account
This API is used for a registered account.

#### Request
**HTTP METHOD:** POST
**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/registeredAccount

``` 
{
    "accountNumber": "123456789",
    "addRegisteredAccount": {
	"registrationId": "1234567",
        "bankRoutingNumber": "123456789",
        "accountType": "SAVINGS",
        "bankAccountNumber": "123456789",
        "nameFirst": "JOHN",
        "nameLast": "DOE",
        "nameFull": "JOHN DOE",
        "authorizationMedium": "Voice",
        "paymentMedium": "eCheck",
        "lookupReference": "123456789",
        "agreedToTerms": "true"
    }
}
``` 
#### Response
**HTTP Code:** 201 Created

``` 
{
    "registeredAccounts": [
        {
            "registrationId": "1234567",
            "bankRoutingNumber": "123456789",
            "accountType": "SAVINGS",
            "bankAccountNumber": "XXXXX6789",
            "nameFirst": "JOHN",
            "nameLast": "DOE",
            "nameFull": "JOHNDOE",
            "authorizationMedium": "Voice",
            "paymentMedium": "eCheck",
            "lookupReference": "XXXXX6789",
            "agreedToTerms": "true"      
		}
	]
}
```

### Delete Registered Account

#### Request
**HTTP METHOD:** POST
**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/registeredAccount

``` 
{
    "accountNumber": "123456789",
      
   "deleteRegisteredAccount": {
    "registrationId": "1234567",
    "accountType": "CHECKING",
    "firstName": "JOHN",
    "lastName": "DOE",
    "fullName": "JOHN DOE",
    "authorizationMedium": "Web",
    "paymentMedium": "e-Check",
    "lookupReference": "123456789",
    "agreedToTerms": true
  }
}
``` 
#### Response
**HTTP Code:**  201 Created

``` 
{
    "registeredAccounts": [
        {
            "registrationId": "1234567",
            "bankRoutingNumber": "123456789",
            "accountType": "SAVINGS",
            "bankAccountNumber": "XXXXX6789",
            "nameFirst": "JOHN",
            "nameLast": "DOE",
            "nameFull": "JOHNDOE",
            "authorizationMedium": "Voice",
            "paymentMedium": "eCheck",
            "lookupReference": "XXXXX6789",
            "agreedToTerms": "true"
        }
    ]
}
```



## Payment Hold

Tests must use only requests given here.

### Payments Holds Search
This API searches for payment holds.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/search?filter=summary

``` 
{
    "accountNumber": "123456789" 
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "count":
}
```

### Payments Hold Search
This API searches for payment holds.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/holds/search

``` 
{
    "accountNumber": "123456789" 
}
``` 
#### Response
**HTTP Code:** 200 OK

``` 
{
 "floatPayments": 1,
"paymentHolds": [
	{
	"paymentEventIdentifier": "089060007812",
	"transactionCode": 271,
	"description": "Payment",
	"postingDate": "2023-12-26",
	"effectiveDate": "2023-12-26",
	"paymentAmount": "000000000065.00",
	"ageOffDate": "2024-01-21",
	"floatAmount": 35,
	"floatExpirationDate": "2024-01-15",
	"currentStatusText": "CH - Payment float amount and/or date changed",
	"availableCreditAmount": "0000000000097886"
	}
	]
}
```

### Payment Hold Update
This API updates payments on hold.

#### Request

**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/hold

``` 
{
    "accountNumber": "123456789",
     "paymentEventIdentifier": "169030085708",
     "update": {
                 "floatAmount": 18,
                 "floatExpDate": "2023-12-26"
                } 
}
``` 
#### Response
**HTTP Code:** 204 No Content

### Payments Hold Release
This API releases an API hold.

#### Request

**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/payments/v1/payments/hold

``` 
{
 "accountNumber": "123456789",
                        "paymentEventIdentifier": "169030085708",
                        "release": {
                            "floatAmount": 18
                        }
}
``` 
#### Response
**HTTP Code:** 204 No Content


