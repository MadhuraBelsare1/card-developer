# Access Tokens

Token API is designed to generate the Access Token by performing Basic Authorization operation on consumer key and consumer secret (generated in the Card Developer Workspace) with grant_type value client_credentials. This access token then passed in header as Bearer type to authenticate APIs.

**Note:** you must obtain a token for the correct environment.  A Sandbox token will not work in Production. A Production token will not work in Sandbox.

Below are the specifications of the token enpoint. Also, see [Token 1.0.0](../api/?type=post&path=/token&version=api)

### Servers

**Production server (uses live data):** https://card.api.fiservapps.com/cs/oauth2

**Sandbox server (uses test data):** https://card-sandbox.api.fiservapps.com/cs/oauth2

## Access Token
API to generate Access Token (OAuth 2.0 bearer token).

### Version: 1.0.1

### Security
**basicAuth**  

API to generate an access token.

|basic|*Basic*|
|---|---|

### /v1/token

#### POST

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| scope | query | Specifies the access available to the client application after it is authenticated. | Yes | string |
| accept | header | Identifies the media format that clients accepts. | No | string |
| content-type | header | Identifies the type of the payload (for POST and PUT operations) that the client is sending. It should be the same as what the server is expecting. | Yes | string |
| authorization | header | Authenticates the user and the system. Enter the API Key:Secret, separated by a colon, encoded in Base64 format.  Format basic [Base64 encoded (Key:Secret)] Find the API Key and API Secret from your Card Developer Workspace (Credentials tab). The keys are app-specific and can have subscription to one or more Fiserv API products. | Yes | string |
| x-fapi-financial-id | header | 8 digit unique financial institute id assigned to each FI by Fiserv. If your application is serving multiple clients then x-fapi-financial-id signifies the financial institute id of FI your application is sending request for. | Yes | number |
| x-fapi-interaction-id | header | Represents a transaction identification (transaction ID) value for tracking purposes. This field is optional in the request but always returned in the response. If a value is provided in the request, the same will be sent back in the response. Otherwise, a Fiserv-generated ID is added to the response. | No | string |
| request | body |  | Yes |  |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | OK | tokenResponse |
| 400 | Bad Request | object |
| 401 | Unauthorized access | object |
| 404 | Resource Not Found |  |
| 415 | Unsupported Media Type | object |
| 429 | Too Many Requests | object |
| 500 | Server Error | object |

##### Security

| Security Schema | Scopes |
| --- | --- |
| basicAuth | |

### Models


#### tokenRequest

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| grant_type | string | Required. The method for granting access to resources. | No |

#### tokenResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| token_type | string |  | No |
| issued_at | string (utc-millisec) |  | No |
| api_key | string |  | No |
| access_token | string |  | No |
| expires_in | string (utc-millisec) | Access Token is valid for 15 minutes (900 milliseconds) | No |

