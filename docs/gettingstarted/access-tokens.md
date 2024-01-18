### Access Tokens

Token API is designed to generate the Access Token by performing Basic Authorization operation on consumer key and consumer secret (generated from portal apps) with grant_type value client_credentials. This access token then passed in header as Bearer type to authenticate APIs.

**Note:** you must obtain a token for the correct environment.  A Sandbox token will not work in Production. A Production token will not work in Sandbox.


