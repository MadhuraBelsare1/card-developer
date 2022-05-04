# Test Cases

## Activations

### Activate Card: Unactivated credit card

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
		

### Activate Card: Unactivated debit card

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
		

## Details

### Cardholder Search with Full Record

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
		  
