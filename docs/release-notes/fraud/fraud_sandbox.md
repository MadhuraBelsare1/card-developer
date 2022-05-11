# Test Cases
<!-- theme: info -->
> #### Note to Unregistered Users
>
> The unregistered user journey enables developers to access a range of Standard Bank Platform APIs on Fraud. Currently we are working on developing a registered user journey, therefore all nuances regarding using Banking Hub APIs to our different platforms may not be available on this portal. <br> Once registration is enabled on Developer Studio, you can sign up to obtain credentials along with the instructions to integrate Banking Hub APIs with our banking platforms. Additionally, you get access to our Sandbox environment to test APIs or may choose to test.


Register to the Fiserv Developer Studio to test the APIs in test and live environments. However, registration is not required to learn about our API integration process and test the APIs in API Explorer.

## Retrieve Verification Options
Retrieves allowed and available media addresses for cardholder's Verification. Possible media address types are Voice, Text, and Email. Media addresses are semi-masked for cardholder's confidentiality.


<!-- theme: info -->
> This case activates a card.

#### Request

**HTTP METHOD:** PUT

**Target URL:** [https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cardholders/verification/search](https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cardholders/verification/search)

		
      {
      "cardNumber": "4000200030004000",
      "memberNumber": "0"
      }	

#### Response

HTTP Code: 200

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
		

## Retrieve Generated Passcode
Retrieves a one time use passcode for cardholder's verification. Generated passcode expires in 10 mins. Passcode is delivered on selected media address.

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cardholders/verification/otp

		
      {
         "cardNumber": "4000200030004000",
         "cardMemberNumber": "0",
         "mediaType": "TEXT",
         "mediaAddress": "0005550001"
      }

		

#### Response

HTTP Code: 201

		
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
		
## Validate Passcode
Validates generated passcode sent to Cardholder on chosen media address. Note passcode expires in 10 minutes.

#### Request

**HTTP METHOD:** POST

**Target URL:** [https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cardholders/verification/otp/validation](https://card-sandbox.api.fiservapps.com/cs/fraud/v1/cardholders/verification/otp/validation)

		
      {
         "cardNumber": "4000200030004000",
         "memberNumber": "0",
         "otpId": "1234567",
         "otpPassCode": "123456"
      }

	
#### Response

HTTP Code: 200

		
      {
         "cardNumber": "400020XXXXXX4000",
         "cardType": "DEBIT",
         "otpId": "1234567",
         "status": "SUCCESS",
         "statusDescription": "SUCCESS"
      }

