# Test Cases

## Company API endpoints

**Details**
## Search Account
Tests must use only requests given here.

## Search Account with Summary Filter

#### Request

**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/accounts/v1/accounts/search?filter=summary

``` 
{
    "accountNumber": "123456789" 
}
``` 
#### Response
**HTTP Code:** 200

``` 
{
    "accountType": "Consumer",
    "description": "VISA Classic",
    "customerName": "Doe, Jesse H",
    "association": "PRIMARY",
    "accountStatus": "NORMAL"
}
``` 
