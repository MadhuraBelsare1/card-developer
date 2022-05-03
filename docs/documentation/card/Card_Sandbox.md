#### Card

  ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACUAAAAlCAMAAADyQNAxAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAFxUExURQAAAP8AAICAgP+AAP9VAEBAQICAgP9mAFVVVW1tbVVVVXFxcWJiYmZmZmFhYWhoaP9oAGRkZGFhYWhoaP9kAGdnZ/9nAP9lAP9rAGNjY2ZmZmVlZWRkZP9lAGNjY2dnZ2VlZWNjY2dnZ/9lAP9kAGZmZv9mAP9lAGdnZ2ZmZmhoaGhoaGNjY2ZmZv9mAP9lAP9lAGVlZf9rAGVlZWRkZP9lAP9nAP9oAGVlZWZmZmVlZWdnZ2ZmZmhoaGVlZWZmZmRkZGZmZv9mAGhoaGRkZGZmZmhoaGlpaWhoaGRkZGZmZmhoaGVlZWVlZWZmZmdnZ2dnZ/9qAGRkZGZmZmVlZWVlZWdnZ2ZmZmhoaGlpaWpqamhoaGhoaP9sAGRkZGZmZmhoaGZmZmdnZ2dnZ2dnZ2ZmZmdnZ2lpaWZmZmhoaGdnZ2lpaWlpaWVlZWZmZmdnZ2lpaf9pAGdnZ2ZmZmdnZ2xsbG1tbW5ubm9vb/9vAP91AKGI4acAAABzdFJOUwABAgIDBAQFBgcJCQ0UFRYWFx0gISoqKyssLTAzNUNDREhISUpLS0xPUFFYWlpaW11tbm9wcnKMkJOVlZaWl5mbnp6foKCgoKSlpaWmp6evsLCysrPHx8jJysrLzNDT0+zt7e7z9PT09fX2+fr7+/v7+/2AJMj7AAAACXBIWXMAABcRAAAXEQHKJvM/AAAB9UlEQVQ4T3WU/V/SUBSHTyiIIaRYVkCgFiWppdkL5PKtzAyd1lLKDNKiF1Naynanf313d9/JuBefH7bn3J3PPrt35xwKMliYrR5ZzDqqzt0fxJpMfm2P1bf12aKmb9fZt7U81oNkNs2TD5OpRJh7OJEaN07MzYz36JzIzM/DxXQIkUsovXj4+3EEkaBv3t7JwVvkPtrzfXBOrOysJOBBEi+dcgxO0QWnFIVzLuHOiZacBf/JNFvthXJuvbsO4/SusmnP0gefr3gmmDq7B3MZ2D1Iu/ewYWbFAnhwehsmyJqGu9GR5rIXAymLXjVH+bmsH6cQe8hZqeP1ECX3DYRAziJjP0kFNo4IKFkTbIzmvl9DBJSsm3WNqpU4IqBkxStVauhtf7RDVkT/S5aGwEfJIs0iuwj3UbOKNlnP4T4PT+/AfPi7lO+aOrsLAxG9QTV5j0PPrsJAvFJTz0vBPa+CI529wqQzpv7H7v5uGDC+JpWa6Hr65UkXXCBqQq6vnqV/Sz1wwXJzhF/lWh16dAMmyJrv3Ubmdb87IBY64de93ENttHpI7scA0RI770eKvWGvO/b2ilO+DOfwOfFpGN4it9M2Jy6YOX9+zEiVQJkNPr8m2ubXhjy/XPJv99ivLV3js3DrolnowudqrWHZVqP2ohCYq0T/ASzGYHMoOcj7AAAAAElFTkSuQmCC)  **See [Using the Sandbox](/documentation/api-portal-card-developers/how-validate-apis-sandbox) before executing test cases.**

[Test Cases](#sectiont)
-----------------------

### [Activations](#opdiv575)

#### [Activate Card: Unactivated credit card](#collapse1)

This case activates a card.

#### Request

**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations

		
{
  "cardNumber": "4000100020003001"
}
		

#### Response

HTTP Code: 200

{
  "cardType": "CREDIT",
  "cardActivationStatus": "ACTIVATED"
}
		

#### [Activate Card: Unactivated debit card](#collapse2)

This case activates a debit card.

#### Request

**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations

		
		{
		"cardNumber": "4000100020003000"
		}
		

#### Response

HTTP Code: 200

		
		{
		"cardType": "DEBIT",
		"activationRequiredByDate": "2021-10-31",
		"availableForUseDate": "2021-07-26",
		"cardActivationDate": "2021-09-23",
		"cardActivationStatus": "ACTIVATED",
		"lastActivationAttemptDate": "2021-09-23",
		"activationMethod": "OPERATOR\_ACTIVATE",
		"numberOfAttempts": "0",
		"verificationCallerID": "9900020"
		}
		

#### [Search for Card Activation Details: Unactivated credit card](#collapse3)

This case demonstrates a case when the card is not activated.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search

		
		{
		"cardNumber": "4000100020003001"
		}
		

#### Response

HTTP Code: 200

		
		{
		"cardType": "CREDIT",
		"cardActivationStatus": "ACTIVATION\_REQUIRED"
		}
		

#### [Search for Card Activation Details: Activated credit card](#collapse4)

This case demonstrates a case when the card is activated.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search

		
		{
		"cardNumber": "4000200030004001"
		}
		

#### Response

HTTP Code: 200

		
		{
		"cardType": "CREDIT",
		"cardActivationStatus": "NO\_ACTIVATION\_REQUIRED"
		}
		

#### [Search for Card Activation Details: Unactivated debit card](#collapse5)

This case demonstrates a case when the debit card is unactivated.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search

		
		{
		"cardNumber": "4000100020003000"
		}
		

#### Response

HTTP Code: 200

		
		{
		"cardType": "DEBIT",
		"activationRequiredByDate": "2021-10-31",
		"availableForUseDate": "2021-07-26",
		"cardActivationStatus": "NOT\_ACTIVATED",
		"numberOfAttempts": "0"
		}
		

#### [Search for Card Activation Details: Activated debit card](#collapse6)

This case demonstrates a case when the debit card is activated.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/activations/search

		
		{
		  "cardNumber": "4000200030004000"
		}
		

#### Response

HTTP Code: 200

		
		{
		  "cardType": "DEBIT",
		  "activationRequiredByDate": "2022-12-31",
		  "cardActivationDate": "2021-09-21",
		  "cardActivationStatus": "ACTIVATED",
		  "lastActivationAttemptDate": "2021-09-21",
		  "activationMethod": "OPERATOR\_ACTIVATE",
		  "numberOfAttempts": "1"
		}
		

### [Details](#opdiv5762)

#### [Cardholder Search with Full Record](#collapse8)

Retrieve cardholder information based on other commonly known information

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search

		{
		  "cardNumber": "4000200030004000",
		  "ssnOrTaxid": "987001234",
		  "accNumber": "123456789",
		  "phone": "0005550001",
		  "emailAddress": "alexsmith@email.com",
		  "dateOfBirth": "10/1/52",
		  "postalCode": "12345",
		  "lastFourCardNumber": "4000",
		  "lastFourAccNumber": "6789",
		  "lastName": "Smith"
		}
		

#### Response

HTTP Code: 200

		
		{
		  "cardholderCardsDetails": \[
			{
			"cardholderDetails": {
			  "cardholderName": "Alex Smith"
			},
			"cards": \[
			  {
				"cardNumber": "4000200030004000",
				"accountNumber": \[
				  "123456789"
				\],
				"cardMemberNumber": "001",
				"cardStatus": "NORMAL",
				"cardType": "CREDIT",
				"association": "PRIMARY",
				"postalCode": "12345",
				"phone": "0005550001",
				"dateOfBirth": "10/1/52",
				"emailAddress": "alexsmith@email.com"
			  }
			\]
			}
		  \]
		}
		  

#### [Cardholder Search with Card Number Only](#collapse9)

This case returns cardholder records using cardNumber only in the request.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search

		
		{
		  "cardNumber": "4000200030004000"
		}
		

#### Response

HTTP Code: 200

		
		{
		  "cardholderCardsDetails": \[
			{
			"cardholderDetails": {
			  "cardholderName": "Alex Smith"
			},
			"cards": \[
			  {
				"cardNumber": "4000200030004000",
				"accountNumber": \[
				  "123456789"
				\],
				"cardMemberNumber": "001",
				"cardStatus": "NORMAL",
				"cardType": "CREDIT",
				"association": "PRIMARY",
				"postalCode": "12345",
				"phone": "0005550001",
				"dateOfBirth": "10/1/52",
				"emailAddress": "alexsmith@email.com"
			  }
			\]
			}
		  \]
		}
		

#### [Cardholder Search with SSN/Tax ID and Name](#collapse10)

This case returns cardholder records using SSN/tax id and last name only in the request.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search

		
		{
		  "ssnOrTaxid": "123005678",
		  "lastName": "Smith"
		}
		

#### Response

HTTP Code: 200

		
		{
		  "cardholderCardsDetails": \[
			{
			"cardholderDetails": {
			  "cardholderName": "Alex Smith"
			},
			"cards": \[
			  {
				"cardNumber": "4000100020003000",
				"accountNumber": \[
				  "123456789"
				\],
				"cardMemberNumber": "001",
				"cardStatus": "ACTIVE"",
				"cardType": "DEBIT""
				"postalCode": "12345",
				"phone": "0005550001",
				"emailAddress": "alexdoe@email.com"
			  }
			\]
			}
		  \]
		}
		

#### [Cardholder Search with email only](#collapse11)

This case returns cardholder records using email address only in the request.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search

		
		{
		  "emailAddress": "alexsmith@email.com"
		}
		

#### Response

HTTP Code: 200

		
		{
		  "cardholderCardsDetails": \[
			{
			"cardholderDetails": {
			  "cardholderName": "Alex Smith"
			},
			"cards": \[
			  {
				"cardNumber": "4000200030004000",
				"accountNumber": \[
				  "123456789"
				\],
				"cardMemberNumber": "001",
				"cardStatus": "NORMAL",
				"cardType": "CREDIT",
				"postalCode": "12345",
				"phone": "0005550001",
				"emailAddress": "alexsmith@email.com"
			  }
			\]
			}
		  \]
		}
		

#### [Cardholder Search with Account and Phone Numbers](#collapse12)

This case returns cardholder records using account and phone number only in the request.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cardholders/search

		
		{
		  "accNumber": "123456789",
		  "phone": "0005550001"
		}
		

#### Response

HTTP Code: 200

		
		{
		  "cardholderCardsDetails": \[
			{
			"cardholderDetails": {
			  "cardholderName": "Alex Smith"
			},
			"cards": \[
			  {
				"cardNumber": "4000200030004000",
				"accountNumber": \[
				  "123456789"
				\],
				"cardMemberNumber": "001",
				"cardStatus": "NORMAL",
				"cardType": "CREDIT",
				"postalCode": "12345",
				"phone": "0005550001",
				"emailAddress": "alexsmith@email.com"
			  }
			\]
			}
		  \]
		}
		

### [Display Digital Card](#opdiv577)

Enables the retrieval of CVV and expiration date information for any given card number.

#### [Card Authorization Details](#collapse7)

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/authDetails

		
		{
		  "cardNumber": "4000200030004000"
		}
		

#### Response

HTTP Code: 200

		
		{
		  "cardNumber": "400020XXXXXX4000",
		  "cv2": "888",
		  "expirationDate": "0624"
		}
		

### [Limits](#opdiv578)

#### [Search Limits](#collapse192)

Search limits with cardNumber and memberNumber.

#### Request

**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/limits/search

 
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0"
}
 

#### Response

HTTP Code: 200

 
{
   "cardLimits": {
      "noneExpiring": "NO",
      "expirationDate": "2021-12-31",
      "limitType": "OVERRIDE",
      "atmTotalAmount": "600.00",
      "atmOfflineAmount": "300.00",
      "posTotalAmount": "2500.00",
      "posOfflineAmount": "500.00",
      "cashEquivTotalAmount": "10.00",
      "cashEquivOfflineAmount": "2.00",
      "customerNPTotalAmount": "1500.00",
      "customerNPOfflineAmount": "500.00",
      "signatureDebitPOSTotalAmount": "0",
      "signatureDebitPOSOfflineAmount": "0",
      "cashAdvanceTotalAmount": "0",
      "cashAdvanceOfflineAmount": "0",
      "aggregateTotalAmount": "2500.00",
      "accountOpenToBuyTotalAmount": "0",
      "cardOpenToBuyTotalAmount": "0",
      "dayOfDepositAvailabilityTotalAmount": "0",
      "accountOpenToBuyOfflineAmount": "0",
      "cardOpenToBuyOfflineAmount": "0",
      "aggregateOfflineAmount": "500.00",
      "mtFundingAmtPerTranTotalAmount": "0",
      "mtFundingAmtPerTranOfflineAmount": "0",
      "mtFundingDlyCntTotal": "0",
      "mtFundingDlyCntOffline": "0",
      "mtFundingDlyTotalAmount": "0",
      "mtFundingDlyOfflineAmount": "0",
      "mtCreditPerTranTotalAmount": "0",
      "mtCreditPerTranOfflineAmount": "0",
      "mtCreditDlyCntTotal": "0",
      "mtCreditDlyCntOffline": "0",
      "mtCreditDlyTotalAmount": "0",
      "mtCreditDlyOfflineAmount": "0",
      "aggMaxCardUsage": "0",
      "aggTimeInterval": "00:00",
      "atmMaxCardUsage": "0",
      "posMaxCardUsage": "0",
      "cashEquivMaxCardUsage": "0",
      "atmTimeInterval": "00:00",
      "posTimeInterval": "00:00",
      "cashEquivTimeInterval": "00:00",
      "retail": "0",
      "travel": "0",
      "lastMaintenanceBy": "Alex",
      "lastMaintainanceDateTime": "2014-10-02T15:01:23.045Z"
   }
}

 

#### [Update Daily Limits](#collapse102)

Update daily limits with cardNumber and memberNumber.

#### Request

**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/limits/daily

 
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0",
   "dailyLimits": {
      "noneExpiring": "YES",
      "atmTotalAmount": "2000",
      "atmOfflineAmount": "200",
      "posTotalAmount": "3000",
      "posOfflineAmount": "400",
      "cashEquivTotalAmount": "500",
      "cashEquivOfflineAmount": "100",
      "customerNPTotalAmount": "0",
      "customerNPOfflineAmount": "0",
      "signatureDebitPOSTotalAmount": "0",
      "signatureDebitPOSOfflineAmount": "0",
      "cashAdvanceTotalAmount": "0",
      "cashAdvanceOfflineAmount": "0",
      "aggregateTotalAmount": "0",
      "dayOfDepositAvailabilityTotalAmount": "0",
      "aggregateOfflineAmount": "0",
      "mtFundingAmtPerTranTotalAmount": "0",
      "mtFundingAmtPerTranOfflineAmount": "0",
      "mtFundingDlyCntTotal": "0",
      "mtFundingDlyCntOffline": "0",
      "mtFundingDlyTotalAmount": "0",
      "mtFundingDlyOfflineAmount": "0",
      "mtCreditPerTranTotalAmount": "0",
      "mtCreditPerTranOfflineAmount": "0",
      "mtCreditDlyCntTotal": "0",
      "mtCreditDlyCntOffline": "0",
      "mtCreditDlyTotalAmount": "0",
      "mtCreditDlyOfflineAmount": "0"
   }
}
 

#### Response

HTTP Code: 204

 
Empty response body

 

#### [Update OpenToBuy Limits](#collapse104)

Update OpenToBuy limits

#### Request

**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/limits/opentobuy

 
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0",
   "openToBuyLimits": {
      "accountOpenToBuyTotalAmount": "9999",
      "cardOpenToBuyTotalAmount": "9999",
      "accountOpenToBuyOfflineAmount": "123",
      "cardOpenToBuyOfflineAmount": "123"
   }
}
 

#### Response

HTTP Code: 204

 
Empty response body

 

#### [Update Velocity Limits](#collapse105)

Update Velocity limits

#### Request

**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/limits/velocity

 
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0",
   "velocityLimits": {
      "aggMaxCardUsage": "20",
      "aggTimeInterval": "10:10",
      "atmMaxCardUsage": "20",
      "posMaxCardUsage": "4",
      "cashEquivMaxCardUsage": "4",
      "atmTimeInterval": "10:10",
      "posTimeInterval": "10:10",
      "cashEquivTimeInterval": "10:10"
   }
}
 

#### Response

HTTP Code: 204

 
Empty response body

 

#### [Set to Default Limits](#collapse106)

Set limits to the defaults.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/limits/default

 
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0"
}
 

#### Response

HTTP Code: 200

 
{
   "cardNumber": "400020XXXXXX4000",
   "dailyLimits": {
      "noneExpiring": "YES",
      "atmTotalAmount": "600.00",
      "atmOfflineAmount": "300.00",
      "posTotalAmount": "2500.00",
      "posOfflineAmount": "500.00",
      "cashEquivTotalAmount": "10.00",
      "cashEquivOfflineAmount": "5.00",
      "customerNPTotalAmount": "1500.00",
      "customerNPOfflineAmount": "500.00",
      "signatureDebitPOSTotalAmount": "0",
      "signatureDebitPOSOfflineAmount": "0",
      "cashAdvanceTotalAmount": "0",
      "cashAdvanceOfflineAmount": "0",
      "aggregateTotalAmount": "2500.00",
      "dayOfDepositAvailabilityTotalAmount": "0",
      "aggregateOfflineAmount": "500.00",
      "mtFundingAmtPerTranTotalAmount": "0",
      "mtFundingAmtPerTranOfflineAmount": "0",
      "mtFundingDlyCntTotal": "0",
      "mtFundingDlyCntOffline": "0",
      "mtFundingDlyTotalAmount": "0",
      "mtFundingDlyOfflineAmount": "0",
      "mtCreditPerTranTotalAmount": "0",
      "mtCreditPerTranOfflineAmount": "0",
      "mtCreditDlyCntTotal": "0",
      "mtCreditDlyCntOffline": "0",
      "mtCreditDlyTotalAmount": "0",
      "mtCreditDlyOfflineAmount": "0"
   },
   "openToBuyLimits": {
      "accountOpenToBuyTotalAmount": "0",
      "cardOpenToBuyTotalAmount": "9999.00",
      "accountOpenToBuyOfflineAmount": "0",
      "cardOpenToBuyOfflineAmount": "123.00"
   },
   "velocityLimits": {
      "aggMaxCardUsage": "0",
      "aggTimeInterval": "00:00",
      "atmMaxCardUsage": "0",
      "posMaxCardUsage": "0",
      "cashEquivMaxCardUsage": "0",
      "atmTimeInterval": "00:00",
      "posTimeInterval": "00:00",
      "cashEquivTimeInterval": "00:00"
   }
}
 

### [Replacement](#opdiv580)

#### [Order Card Replacement - Rush Type None](#collapse1rpl)

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/orderReplacement

 
{
   "cardNumber": "4000200030004000",
   "rushType": "NONE",
   "memberNumber": "0"
}
 

#### Response

HTTP Code: 204

 
No response body.
 

#### [Order Card Replacement - Rush Type Regular](#collapse2rpl)

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/orderReplacement

 
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0",
   "rushType": "REGULAR",
   "waiveReplacementFeeInd": "Y",
   "personalizedEmbossingText": "Chris",
   "cardStock": "00",
   "plasticsCount": "01"
}
 

#### Response

HTTP Code: 204

 
No response body.
 

### [PIN](#opdiv579)

Set and manage a PIN.

#### [Obtain PINselect Token](#collapse107)

In order to select a PIN, you must supply the JWT returned by this operation. This JWT changes each time you make this request.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/token

 
{
   "cardNumber": "4000100020003000"
}
 

#### Response

HTTP Code: 200

 
{
   "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnI
   joiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-
   U8\_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom9
   4jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH
   5L0XC\_QqP5TIs3A15fqpAnvMaSwW9O\_GDRzxnsUDCgEZCkwQOuEpWY
   DbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWb
   MzbindOIefIo4VTrOVMxWOdP\_bLNId0E0CBLxSpRHX1u3EeAjUykUdi
   fT2CP4bb6kbJf4pp0dRc\_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy
   .FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUi
   hzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4\_eWyUwx4IYpYaJkPeUV
   d4ni\_1eZMBy6-hPr3n39DES\_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZ
   cFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6u
   yCaOnyuWuE\_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKw
   CNM.TOYk3lw2SKYamQL7XiLXlg"
}
 

#### [Reset PIN Attempts](#collapse109)

Reset the number of PIN attempts to zero.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinAttempts

 
{
   "cardNumber": "4000200030004000"
}
 

#### Response

HTTP Code: 204

 
No response body
 

#### [Select a PIN](#collapse108)

You must first obtain a JWT with the token operation. Use the JWT returned from the token request.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pin

 
{
   "pin":"2938",
   "jwt": "eyJ0eXAiOiJKV1QiLCJlbmMiOiJBMTI4R0NNIiwiYWxnI
   joiUlNBLU9BRVAtMjU2In0.WrliT8nLQOTRnXldrYj0brobAyi6M7-
   U8\_iHovmTH1VAZksc4mOGQCfaSx-sbDNjdkpeznR8lU1sHOX26qom9
   4jBO6uePEw1cBbTHLpOSEPDYiWS6SzTgxguF7zT2g5Ui1HHi2GKgPtH
   5L0XC\_QqP5TIs3A15fqpAnvMaSwW9O\_GDRzxnsUDCgEZCkwQOuEpWY
   DbM7r7yKrfAlkWKOHOlZuUtvJvg3k8p-1qwKpuGexhWXQdgKsWphBWb
   MzbindOIefIo4VTrOVMxWOdP\_bLNId0E0CBLxSpRHX1u3EeAjUykUdi
   fT2CP4bb6kbJf4pp0dRc\_uPZGJLj7faPyq6UeQ.zTLJMNI8bjGh-KBy
   .FW0W0ihL2sj7pYin2iY1gavS4W-yPswjKmrb6-ROwHgEOscfeGGLmUi
   hzoV6vy9KvTJ9ytnIPqh-K94UsShUJ0-KgsY4\_eWyUwx4IYpYaJkPeUV
   d4ni\_1eZMBy6-hPr3n39DES\_kXfnv3MJOiZZj0I-GJXw99WBV7xhl7KZ
   cFKyMXYnszyboV8Xi2iZqHglvEoYRjKLvOlEq2j4pJoMRVfBB8oIOZm6u
   yCaOnyuWuE\_Lg1HeuNMnHddTm8gexDAfwj3WYHkJazsN1PZVhPZVImyKw
   CNM.TOYk3lw2SKYamQL7XiLXlg"
}

 

#### Response

HTTP Code: 201

 
Blank body.
 

#### [Set PIN Offset](#collapse1090)

Set the Pin offset for a card.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/pinOffset

 
{
        "cardNumber": "4000200030004000",
        "memberNumber": "0",
        "pinOffset": "1234"
    }

 

#### Response

HTTP Code: 204

 
No response body on success.
 

### [Transactions](#opdiv5190)

Search for card transactions.

#### [Search Credit Transactions with Summary Filter](#collapse160)

The response contains only summary information.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/transactions/search?filter=summary

 
{
   "cardNumber": "4000100020003000",
   "memberNumber": "1",
   "filterCriteria": \[
      {
         "filterBy": "FROM\_DATE",
         "filterValue": "2021-09-10"
      },
      {
         "filterBy": "TO\_DATE",
         "filterValue": "2021-10-14"
      }
   \]
}
 

#### Response

HTTP Code: 200

 
{
   "count": 2,
   "transactions": \[
      {
         "transactionDateTime": "2021-09-14T05:00:00Z",
         "merchantName": "LATE FEE",
         "transactionAmount": "29.00",
         "transactionType": "Late Charge",
         "transactionStatus": "POSTED",
         "transactionDetails": {}
      },
      {
         "transactionDateTime": "2021-07-14T05:00:00Z",
         "merchantName": "Interest Charge on Cash A",
         "transactionAmount": "6.73",
         "transactionType": "Cash Advance Finance Charge",
         "transactionStatus": "POSTED",
         "transactionDetails": {}
      }
   \]
}
 

#### [Search Credit Transactions with Detail Filter](#collapse260)

The response contains full detail information.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/transactions/search?filter=detail

 
{
   "cardNumber": "4000100020003000",
   "memberNumber": "1",
   "filterCriteria": \[
      {
         "filterBy": "FROM\_DATE",
         "filterValue": "2021-09-10"
      },
      {
         "filterBy": "TO\_DATE",
         "filterValue": "2021-10-14"
      }
   \]
}
 

#### Response

HTTP Code: 200

 
{
    "count": 2,
    "transactions": \[
        {
            "transactionDateTime": "2021-10-14T06:00:00Z",
            "merchantName": "LATE FEE",
            "transactionAmount": "29.00",
            "transactionType": "Late Charge",
            "transactionStatus": "POSTED",
            "postedTransactionDetails": {
                "cardholderAccountNumber": "123456789",
                "transactionDescription": "LATE FEE",
                "postingDate": "2021-11-14",
                "detailTransactionIdentifier": "000000000000000",
                "merchantCategoryCode": "00000",
                "transactionCode": "961"
            },
            "transactionDetails": {}
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
            },
            "transactionDetails": {}
        }
    \]
}

 

#### [Search Debit Transactions with Summary Filter](#collapse360)

The response contains only summary information.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/transactions/search?filter=summary

 
{
    "cardNumber": "4000200030004000",
    "memberNumber": "1",
    "filterCriteria": \[
        {
            "filterBy": "FROM\_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO\_DATE",
            "filterValue": "2021-10-14"
        }
    \]
}

 

#### Response

HTTP Code: 200

 
{
    "count": 2,
    "transactions": \[
        {
            "systemRecordId": "011103LMFI4F4321377761184",
            "cardNumber": "400020XXXXXX4000",
            "memberNumber": "0",
            "sequenceNumber": "000002",
            "subResponseCode": "M",
            "subResponseCodeDescription": "96-M Error processing PIN",
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
            "systemRecordId": "011103LMFI4F4321377761184",
            "cardNumber": "400020XXXXXX4000",
            "memberNumber": "0",
            "sequenceNumber": "000107",
            "subResponseCode": "B",
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
    \]
}

 

#### [Search Debit Transactions with Detail Filter](#collapse460)

The response contains full detail information.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/transactions/search?filter=detail

 
{
    "cardNumber": "4000200030004000",
    "memberNumber": "1",
    "filterCriteria": \[
        {
            "filterBy": "FROM\_DATE",
            "filterValue": "2021-09-10"
        },
        {
            "filterBy": "TO\_DATE",
            "filterValue": "2021-10-14"
        }
    \]
}
 

#### Response

HTTP Code: 200

 
{
    "count": 2,
    "transactions": \[
        {
            "cardNumber": "400020XXXXXX4000",
            "memberNumber": "0",
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
                    "sequenceNumber": "000002"
                },
                "tokenAndEmvInfo": {
                    "tokenTransaction": "No",
                    "emvCard": "Yes",
                    "emvTerminal": "Yes",
                    "emvFallback": "N/A"
                },
                "riskInfo": {},
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
            "cardNumber": "400020XXXXXX4000",
            "memberNumber": "0",
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
                    "sequenceNumber": "000107"
                },
                "tokenAndEmvInfo": {
                    "tokenTransaction": "No",
                    "emvCard": "Yes",
                    "emvTerminal": "Yes",
                    "emvFallback": "N/A"
                },
                "riskInfo": {},
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
    \]
}

 

### [Update Status](#opdiv5770)

Update status of card.

#### [Update Card Status](#collapse13)

Allow clients to retrieve and update the Status and Reason codes for a debit card. 

#### Request

**HTTP METHOD:** PUT

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/cards/v1/cards/status

 
{
   "cardNumber": "4000200030004000",
   "memberNumber": "0",
   "cardStatus": "ACTIVE",
   "statusReasonCode": "NONE",
   "fraudActivity": "NONE\_SUSPECTED",
   "securityMemo": "memo"
}
 

#### Response

HTTP Code: 204

 
Empty response body

 

[Error Handling](#sectione)
---------------------------

#### [Parameter: addressType](#collapse660)

**IDX**

**Scenario**

**Response**

1

Invalid value

**HTTP** 400

{
   "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
   "title": "Invalid Request",
   "instance": "/cs/cards/v1/cards/{operation}",
   "status": "400",
   "detail": "addressType : must contain a valid value"
} 

**Solution** Correct and resend.

#### [Parameter: beginDate](#collapse661)

**IDX**

**Scenario**

**Response**

2

Invalid value, such as 22-02-2024

**HTTP** 400

{
   "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
   "title": "Invalid Request",
   "instance": "/cs/cards/v1/cards/{operation}",
   "status": "400",
   "detail": "beginDate : must be a valid date in UTC format"
} 

**Solution** Valid format YYYY-MM-DD.

#### [Parameter: cardNumber](#collapse20)

IDX

**Scenario**

**Response**

3

Blank cardNumber; this is required

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title":"Invalid Request",
 "instance": "/cs/cards/v1/cards/{operation}",
 "status": "400",
 "detail": "cardNumber is required"
}

**Solution** Add to the request body "cardNumber":"

4

Missing cardNumber; this is required

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title":"Invalid Request",
 "instance": "/cs/cards/v1/cards/{operation}",
 "status": "400",
 "detail": "cardNumber must not be null"
}

**Solution** Add to the request body "cardNumber":"

5

Passing special characters in cardNumber like “411!!@#%$#@8971”

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title":"Invalid Request",
 "instance": "/cs/cards/v1/cards/{operation}",
 "status": "400",
 "detail": "cardNumber is invalid"
}

**Solution** Correct number and resend.

6

cardNumber not available

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title":"Invalid Request",
 "instance": "/cs/cards/v1/cards/{operation}",
 "status": "400",
 "detail": "No matching search results found or you do not have sufficient access
}

**Solution** Correct number and resend.

#### [Parameter: cardStatus](#collapse29)

IDX

**Scenario**

**Response**

7

With cardStatus value "CAPTURE" and empty statusReasonCode value

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title": "Invalid Request",
 "instance": "/cs/cards/v1/cards/status",
 "status": "400",
 "detail": "Invalid value for field: statusReasonCode"
}

**Solution** Correct request and resend. 

8

With cardStatus value "ACTIVE/RESTRICTED/ISSUED" provides statusReasonCode value other than "None"

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title": "Invalid Request",
 "instance": "/cs/cards/v1/cards/status",
 "status": "400",
 "detail": "9000:Active or Restricted Cards must have a Reason Code of '00'."
}

**Solution** Correct request and resend. 

9

With cardStatus value "DEACTIVATE" provides statusReasonCode value "None"

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title": "Invalid Request",
 "instance": "/cs/cards/v1/cards/status",
 "status": "400",
 "detail": "9000:Statused Cards must NOT use a Reason Code of '00'"
}

**Solution** Correct request and resend. 

10

With cardStatus value "CAPTURE" provides statusReasonCode value "None"

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title": "Invalid Request",
 "instance": "/cs/cards/v1/cards/status",
 "status": "400",
 "detail": "9000:Statused Cards must NOT use a Reason Code of '00'"
}

**Solution** Correct request and resend. 

11

cardStatus value "NOT\_ACTIVE" provides statusReasonCode value "TEMP\_BLOCK\_BY\_AGENT "

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title": "Invalid Request",
 "instance": "/cs/cards/v1/cards/status",
 "status": "400",
 "detail": "Invalid value for field: statusReasonCode"
}

**Solution** Correct code and resend.

12

cardStatus value "LOST/STOLEN" provides statusReasonCode value "REVOKED"

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title": "Invalid Request",
 "instance": "/cs/cards/v1/cards/status",
 "status": "400",
 "detail": "Invalid value for field: cardStatus"
}

**Solution** Correct code and resend.

13

cardStatus value "LOST\_OR\_STOLEN" provides statusReasonCode value "REVOKED"

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title": "Invalid Request",
 "instance": "/cs/cards/v1/cards/status",
 "status": "400",
 "detail": "Invalid value for field: statusReasonCode"
}

**Solution** Correct code and resend.

#### [Parameter: dateOfBirth](#collapse6621)

**IDX**

**Scenario**

**Response**

14

Invalid date, such as 02-02-2022 

**HTTP** 400

{
    "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
    "title": "Invalid Request",
    "instance": "/cs/cards/v1/cards/{operation}",
    "status": "400",
    "detail": "dateOfBirth : must be valid date in UTC format"
}
 

**Solution** Valid format is YYYY-MM-DD.

#### [Parameter: jwt](#collapse31)

IDX

**Scenario**

**Response**

15

Blank or missing jwt; this is required

**HTTP** 500 Internal Server Error

 
{
	"errorResponse": {
		"code": "500-01",
		"message": "internal server error",
		"developerInfo": {
			"developerMessage": "internal server error",
			"moreInfo": "There was a problem handling your 
			request.  Please try again.  If the problem 
			persists please contact Support"
			"messageid": "3689-1481694-1"
		}
	}
}

**Solution**  Correct request body and resend.

16

Invalid jwt

**HTTP** 401 Unauthorized

 
{
   "type": "https://card.developer.fiserv.com/cards/error#unauthorized",
   "title": "Unauthorized",
   "instance": "/cs/cards/v1/cards/pin",
   "status": 401,
   "detail": "Invalid JWT"
}

**Solution**  Correct request body and resend.

17

Expired jwt

**HTTP** 401 Unauthorized

 
{
    "type": "https://card.developer.fiserv.com/cards/error#unauthorized",
    "title": "Unauthorized",
    "instance": "/cs/cards/v1/cards/pin",
    "status": 401,
    "detail": "Access token has expired"
}

**Solution**  Correct request body and resend.

#### [Parameter: memberNumber](#collapse25)

IDX

**Scenario**

**Response**

18

Invalid memberNumber

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title":"Invalid Request",
 "instance": "/cs/cards/v1/cards/{operation}",
 "status": "400",
 "detail": "memberNumber must be numeric and must be between 0-9.
}

**Solution** Correct memberNumber and resend.

#### [Parameter: noneExpiring](#collapse26)

IDX

**Scenario**

**Response**

19

Empty or wrong value of noneExpiring

**HTTP** 400 Bad Request

 
{
 "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
 "title":"Invalid Request",
 "instance": "/cs/cards/v1/cards/{operation}",
 "status": "400",
 "detail": "Invalid Non Expiring value in the request."									
}

**Solution** Correct value and resend.

#### [Parameter: pin](#collapse32)

IDX

**Scenario**

**Response**

20

Blank, missing or invalid PIN (Not integers, not 4 digits long, 3 repeating characters in a row. sequential characters)

**HTTP** 500 Internal Server Error

 
{
   "errorResponse": {
      "code": "500-01",
      "message": "internal server error",
      "developerInfo": {
         "developerMessage": "internal server error",
         "moreInfo": "There was a problem handling your 
		 request.  Please try again.  If the problem persists 
		 please contact Support",
         "messageid": "3690-1551271-6"
      }
   }

**Solution**  Correct request body and resend.

#### [Parameter: pinOffset](#collapse652)

**IDX**

**Scenario**

**Response**

21

Pin Offset is less than 4 digits 

**HTTP** 400 Bad Request

{
    "instance": "/cs/cards/v1/cards/pinOffset",
    "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
    "title": "Invalid Request",
    "status": "400",
    "detail": "9000:PIN offset invalid"
}

**Solution** Correct and resend.

22

Pin Offset is more than 4 digits 

**HTTP** 400 Bad Request

{
    "instance": "/cs/cards/v1/cards/pinOffset",
    "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
    "title": "Invalid Request",
    "status": "400",
    "detail": "PIN Offset should consist of 4 digits"
}

**Solution** Correct and resend.

#### [Parameter: stateCode](#collapse6631)

**IDX**

**Scenario**

**Response**

23

Invalid state code 

**HTTP** 400

{
   "type": "https://card.developer.fiserv.com/cards/error#invalid-request",
   "title": "Invalid Request",
   "instance": "/cs/cards/v1/cards/cardholders/address",
   "status": "400",
   "detail": "stateCode : must be valid with max 2 chars long"
} 

**Solution** Correct and resend.