# Test Cases
<!-- theme: info -->
> #### Note to Unregistered Users
>
> The unregistered user journey enables developers to access a range of Standard Bank Platform APIs on Fraud. Currently we are working on developing a registered user journey, therefore all nuances regarding using Banking Hub APIs to our different platforms may not be available on this portal. <br> Once registration is enabled on Developer Studio, you can sign up to obtain credentials along with the instructions to integrate Banking Hub APIs with our banking platforms. Additionally, you get access to our Sandbox environment to test APIs or may choose to test.


Register to the Fiserv Developer Studio to test the APIs in test and live environments. However, registration is not required to learn about our API integration process and test the APIs in API Explorer.

## Add reward points for cardholder



<!-- theme: info -->
> This case adds reward points.

<span style="font-size:25px;">**Request**</span>

**HTTP METHOD:** POST

**Target URL:** [https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/addpoints](https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/addpoints)

		
    {
        "client": {
          "id": "11122203",
          "applicationName": "CM",
          "vendorName": "ITI",
          "auditId": "Saint Michael"
       },
       "rewardsKeyInfo": {
          "cardNumber": "5004065676691",
          "accountNumber": "3445454545",
          "useMultiAuth": "false"
       },
       "addPoints": {
          "points": "19",
          "description": "Add",
          "vest": "true"
       }
    }	

<font size="5">**Response** </font>

HTTP Code: 200

    {
       "pointsInfo": {
          "pointsToDate": 50,
          "availablePoints": 10,
          "vestedPoints": 35,
          "ccName": "A1",
          "ccType": "MASTERCARD",
          "ccStatus": true,
          "earnStart": "2017-10-19",
          "earnEnd": "2050-12-31"
       },
       "scoreId": "78901"
    }
		

## Redeem reward points for cardholder

<!-- theme: info -->
> This case Redeem reward points.


<font size="5">**Request** </font>

**HTTP METHOD:** POST

**Target URL:** [https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/redeempoints](https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/redeempoints)

		
    {
        "client": {
          "id": "11122203",
          "applicationName": "CM",
          "vendorName": "ITI",
          "auditId": "Saint Michael"
        },
        "rewardsKeyInfo": {
          "cardNumber": "5004065676691",
          "accountNumber": "3445454545",
          "useMultiAuth": "false"
        },
        "redeemPoints": {
          "points": "19",
          "description": "b",
          "reference": "B"
        }
    }


<font size="5">**Response** </font>

HTTP Code: 200

		
    {
        "pointsInfo": {
            "pointsToDate": 50,
            "availablePoints": 10,
            "vestedPoints": 35,
            "ccName": "A1",
            "ccType": "MASTERCARD",
            "ccStatus": true,
            "earnStart": "2017-10-19",
            "earnEnd": "2050-12-31"
         },
         "redeemID": "78901"
    }
		
## Retrieve reward points for cardholder

<!-- theme: info -->
> This case Retrieve reward points.



<font size="5">**Request** </font>

**HTTP METHOD:** POST

**Target URL:** [https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/points](https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/points)

		
    {
        "client": {
            "id":11122203,
            "applicationName":"CM",
            "vendorName":"ITI",
            "auditId":"123456"
        },
            "rewardsKeyInfo": {
            "cardNumber":"5004065676691",
            "accountNumber":"3445454545",
            "useMultiAuth":true
        }
    }

	
<font size="5">**Response** </font>

HTTP Code: 200

    {
        "pointsInfo": {
          "pointsToDate": 0,
          "availablePoints": 0,
          "vestedPoints": 0,
          "ccName": "A1",
          "ccType": "MASTERCARD",
          "ccStatus": true,
          "earnStart": "2017-10-19",
          "earnEnd": "2050-12-31"
         }
    }
    
    

## Retrieve Rewards SSO Link

<!-- theme: info -->
> This case Retrieve Rewards SSO Link.



<font size="5">**Request** </font>

**HTTP METHOD:** POST

**Target URL:** [https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/sso-url](https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/sso-url)

		
    {
        "client" : {
          "id":"11122203",
          "applicationName":"CM",
          "vendorName":"ITI",
          "auditId":"123456"
         },
         "rewardsKeyInfo" : {
          "cardNumber":"5004065676691",
          "accountNumber":"3445454545",
          "useMultiAuth":false
         },
         "email":"sandbox.app@fiserv.com"
    }

	
<font size="5">**Response** </font>

HTTP Code: 200

    {
        "destURL": "https://uat.uchooserewards.com/members/ssoredirect.php?sid=40XpKlKoY837589&xmembid=32380882&redoip=y"
    }

