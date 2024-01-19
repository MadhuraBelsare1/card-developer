### Access Tokens



Token API is designed to generate the Access Token by performing Basic Authorization operation on consumer key and consumer secret (generated from portal apps) with grant_type value client_credentials. This access token then passed in header as Bearer type to authenticate APIs.

**Note:** you must obtain a token for the correct environment.  A Sandbox token will not work in Production. A Production token will not work in Sandbox.


[![Token](assets/images/token-button.png)](https://card-dit1-dsp.apimz.onefiserv.net:8079/tou/2637/915)



[Token.yaml](assets/Token-API-3_2.yaml)










### Access Token   **1.0.1  OAS3**

API to generate Access Token (OAuth 2.0 bearer token).

Servers:

https://card.api.fiservapps.com/cs/oauth2 - Production server (uses live data)

https://card-sandbox.api.fiservapps.com/cs/oauth2 - Sandbox server (uses test data)




[Token](https://card.developer.fiserv.com/apis/token1#/Token:~:text=Token-,POST,-/v1/token)      /v1/token API to generate an access token.

##### Parameters

|                          Name                                |   Description                                                                                                                                                                                                                                                                                                                                     |
|--------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **scope** **required*<br>(query)                 |   Required. Specifies the access available to the client application after it is authenticated.   <br>Example : /cs/api   /cs/api                                                                                                                                                                                                                                     |
|   **accept**           <br>(header)                 |   Identifies the media format that clients accepts.                                                                                                                                                                                                                                                                                                               |
|   **content-type** **required*<br>(header)         |   Required. Identifies the type of the payload (for POST and PUT operations) that the client is sending. It should be the same as what the server is expecting.                                                                                                                                                                                                   |
|   **authorization** **required*<br>(header)        |   Required. Authenticates the user and the system. Enter the app Key:Secret, separated by a colon, encoded in Base64 format. Format basic [Base64 encoded (Key:Secret)] Find the API Key and API Secret from your Developer App (Keys tab) in the Card Developer Portal. The keys are app-specific and can have subscription to one or more Fiserv API products.  |
|   **x-fapi-financial-id** **required*<br>(header)  |   8 digit unique financial institute id assigned to each FI by Fiserv. If your application is serving multiple clients then x-fapi-financial-id signifies the financial institute id of FI your application is sending request for.                                                                                                                               |
|   **x-fapi-interaction-id**<br>(header)  |   Optional. Represents a transaction identification (transaction ID) value for tracking purposes. This field is optional in the request but always returned in the response. If a value is provided in the request, the same will be sent back in the response. Otherwise, a Fiserv-generated ID is added to the response.                                        |
|   **request** **required*<br>object       <br>(body)           |   Example Value   		Schema  <br>``` {```<br>```     "grant_type": "client_credentials"```<br>```  } ```  <br>Parameter content type   <br>application/x-www-form-urlencoded                                                                                                                                                                                                                              |

#### Responses

![carefully-crafted Markdown table](assets/images/responses-access-token.png)
