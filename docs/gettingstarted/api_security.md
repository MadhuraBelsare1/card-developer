# API Security

Fiserv uses both **TLS 1.2 transport layer security** and **OAuth 2.0 application layer security** to protect transactions with the API Gateway.

## Two-Way-SSL (Mutual Authentication)
In order to integrate with Fiserv Card Services APIs a valid client certificate must be procured from Fiserv and configured in the client application.

The client certificate issued by Fiserv will be in PFX (aka PKCS #12) format. It is a password protected certificate archive that contains the certificate chain plus the matching private key.

## Target Host URLs
A product and resource endpoint has a URL address that enables a client request to communicate with the Card Developer gateway. See each product reference to see the URLs for endpoints, or for the bearer token.

## OAuth 2.0
In order to make calls to Fiserv Card Services APIs, a valid access token must be passed in the Authorization header in the HTTP requests.

You can obtain a time-limited token (15 minute expiry) by requesting one from the token endpoint.  The request for a token uses a Basic authorization header created from the API Key and Secret assigned to an app you create on the Portal.

**Also see:** [Token API](../api?type=post&path=/cs/oauth2/token)

## Onboarding

Please follow the below steps to get the access token for your Developer App and then use the access token to call the Fiserv APIs.

### Step 1: Retrieve API Key and Secret

Your Developer App(s) are assigned unique API key and Secret. Please make a note of these values as they are required to get an access token. API Key and Secret should be kept securely and should not be shared and passed in the URL, or URI query-string parameters, or posted in public forums.

### Step 2: Generate an Access Token

To generate an access token, issue a HTTP POST against the access token endpoint with your App Key and Secret values:

Sample Request:

```
curl --location --request POST 'https://{host}/cs/oauth2/v1/token?scope=/cs/api' \
  --header 'Content-Type: application/x-www-form-urlencoded'\
  --header 'x-fapi-financial-id: {client id}' \
  --header 'Authorization: Basic {base64 encoded({your_app_key}:{your_app_secret})}' \
  --data-urlencode 'grant_type=client_credentials'
```

Note:

1. 'host' value for Sandbox and Production are card-sandbox.api.fiservapps.com and card.api.fiservapps.com respectively.

2. 'scope' should be passed as '/cs/api' and 'grant_type' should be 'client_credentials' in the access token request.

Sample Response:

```
{
  "token_type": "BearerToken",
  "issued_at": "1596806825144",
  "api_key": "FPRlRB2FbonS0bUwJQUT3YwN",
  "access_token": "62vZg9z3viV4qYtkHLcg5Pn",
  "expires_in": "899"
}
```

### Step 3: Make API Request

Once the access token is received, API requests can be made by including an Authorization header in the HTTP call to Fiserv Card Services APIs. This will have the format Bearer + {space} + {accessToken}.

Sample Request:

```
curl --location --request POST '{host}/cs/{api}/{apiVersion}/{apiMethod}' \
  --header 'Content-Type: application/json' \
  --header 'x-fapi-financial-id: {client id}' \
  --header 'Authorization: Bearer 62vZg9z3viV4qYtkHLcg5Pn' \
  --data-raw '{
    JSON Request...
  }'>
```
