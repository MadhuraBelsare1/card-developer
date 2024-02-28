# Test Cases
## Rewards
### Add Cardholder Points

Add reward points for cardholder

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/addpoints

``` 
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
``` 
#### Response
**HTTP Code:** 200

``` 
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
``` 
## Redeem Cardholder Points
**Test Cases**
### Redeem reward points for cardholder
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/redeempoints

``` 
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
``` 
#### Response
**HTTP Code:** 200

``` 
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
``` 
## Retrieve Cardholder Points
**Test Cases**
### Retrieve reward points for cardholder
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/points

``` 
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
``` 
#### Response
**HTTP Code:** 200

``` 
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
``` 
## Retrieve Rewards SSO
**Test Cases**
### Retrieve Rewards SSO Link
#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/uChooseRewards/v1/sso-url

``` 
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
```
#### Response
**HTTP Code:** 200

``` 
{
 "destURL": "https://uat.uchooserewards.com/members
/ssoredirect.php?sid=40XpKlKoY837589&xmembid
=32380882&redoip=y"
}
``` 
## View Offers
**Test Cases**
### Activation
Activate an offer.

#### Request
**HTTP METHOD:** PATCH

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/rewards/v1/offers/activation
```
{
  "cardNumber": "4000200030004000",
  "accountNumber": "123456789",
  "offerId": "654321"
}
```
#### Response
**HTTP Code:** 204 No Content

### Retrieve Offer by OfferId
The offerID is given at the end of the URL.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/rewards/v1/offers/103557
```
{
  "cardNumber": "4000200030004000",
  "accountNumber": "123456789" 
}
```
#### Response
**HTTP Code:** 200
```
{
    "offerId": "103557",
    "offerValue": "5",
    "offerValueDescription": "2%",
    "offerTermsAndConditions": "Offer expires 2015-06-30.",
    "offerExpirationDate": "2022-09-23",
    "categories": [
        {
            "categoryId": "38460",
            "categoryDescription": "Kids & Toys"
        }
    ],
    "shopType": [
        "IN_STORE"
    ],
    "merchantPartnerName": "The 1St Lady Boutique OR Boutique",
    "merchantOfferDescription": "Earn 5 Points per $1 at 1000 Degrees Neapolitan Pizza.",
    "merchantNameOfferDescription": "Earn 5 Points per dollar at Rock Me Makeup on purchases of $50 or more.",
    "merchantOfferExternalUrl": "",
    "merchantLogoFileNameUrl": "https://uchooserewards.com/data/images/lego_90x50_4.2.08.gif",
    "activated": true,
    "requiresActivation": false,
    "partnerId": "24966",
    "shortMerchantOffer": "5 Points per dollar",
    "locationCount": "10",
    "alphaIndex": "r",
    "spend": "",
    "clickTrend": "",
    "fundingCategory": "FEATURED",
    "bonusEarned": false,
    "stores": [
        {
            "storesId": "232232",
            "name": "Bed Bath & Beyond",
            "locationName": "Mira Loma",
            "address": "6365 Pats Ranch Road",
            "city": "Mira Loma",
            "street": "CA",
            "zip": "91752",
            "longtitude": "-117.54465999999999",
            "latitude": "33.972551000000003",
            "phone": "7568142562",
            "venueId": "",
            "notes": "Next to shoprite",
            "distance": "0.0"
        }
    ]
}
```
### Search
Search for offers.

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/rewards/v1/offers/search
```
{
  "cardNumber": "4000200030004000",
  "accountNumber": "123456789",
  "offerId": "654321"
}
```
#### Response
**HTTP Code:** 200
```
{
    "offerSearchParameters": {
        "radius": 50,
        "offerRecordsPerPage": "15",
        "totalPages": "10",
        "pageCount": "1",
        "groupBy": "1",
        "sort": "NONE",
        "sortOrder": "ASC",
        "geoFilter": true,
        "offers": [
            {
                "offerId": "103557",
                "merchantPartnerName": "LEGO",
                "merchantLogoFileNameUrl": "https://uchooserewards.com/data/images/lego_90x50_4.2.08.gif",
                "merchantPartnerId": "string",
                "offerTermsAndConditions": ">Offer expires 2015-03-31.",
                "merchantOfferExternalUrl": "http://click.linksynergy.com/fs-bin/click?id=E7Il34ja9WM&offerid=115554.10000195&type=3&subid=0&u1=26XXdKrlo26",
                "offerValueDescription": "",
                "categories": [
                    {
                        "categoryId": "38460",
                        "categoryDescription": "Kids & Toys"
                    }
                ],
                "offerExpirationDate": "2022-09-23",
                "requiresActivation": false,
                "offerValue": "2",
                "activated": true,
                "shopType": [
                    "IN_STORE"
                ],
                "offerDescription": "Earn 2% Cash back at LEGO.",
                "shortMerchantOffer": "2% Cash back",
                "merchantOfferDescription": "Earn 2% Cash back at LEGO.",
                "locationCount": "10",
                "partnerId": "2537",
                "alphaIndex": "l",
                "spend": "",
                "clickTrend": "",
                "fundingCategory": "FEATURED",
                "bonusEarned": false,
                "stores": [
                    {
                        "storesId": "232232",
                        "name": "Bed Bath & Beyond",
                        "locationName": "Mira Loma",
                        "address": "6365 Pats Ranch Road",
                        "city": "Mira Loma",
                        "street": "CA",
                        "zip": "91752",
                        "longtitude": "-117.54465999999999",
                        "latitude": "33.972551000000003",
                        "phone": "7568142562",
                        "venueId": "",
                        "notes": "Next to shoprite",
                        "distance": "0.0"
                    }
                ]
            }
        ]
    }
}
```
### Search With Filter FeaturedOffers
Search With Filter FeaturedOffers

#### Request
**HTTP METHOD:** POST

**Target URL:** https://card-sandbox.api.fiservapps.com/cs/rewards/v1/offers/search?filter=featuredOffers
```
{
  "cardNumber": "4000200030004000",
  "accountNumber": "123456789",
  "offerId": "654321"
}
```
#### Response
**HTTP Code:** 200
```
{
    "offerSearchParameters": {
        "radius": 50,
        "offerRecordsPerPage": "15",
        "totalPages": "10",
        "pageCount": "1",
        "groupBy": "1",
        "sort": "NONE",
        "sortOrder": "ASC",
        "geoFilter": true,
        "offers": [
            {
                "offerId": "103557",
                "merchantPartnerName": "LEGO",
                "merchantLogoFileNameUrl": "https://uchooserewards.com/data/images/lego_90x50_4.2.08.gif",
                "merchantPartnerId": "string",
                "offerTermsAndConditions": ">Offer expires 2015-03-31.",
                "merchantOfferExternalUrl": "http://click.linksynergy.com/fs-bin/click?id=E7Il34ja9WM&offerid=115554.10000195&type=3&subid=0&u1=26XXdKrlo26",
                "offerValueDescription": "",
                "categories": [
                    {
                        "categoryId": "38460",
                        "categoryDescription": "Kids & Toys"
                    }
                ],
                "offerExpirationDate": "2022-09-23",
                "requiresActivation": false,
                "offerValue": "2",
                "activated": true,
                "shopType": [
                    "IN_STORE"
                ],
                "offerDescription": "Earn 2% Cash back at LEGO.",
                "shortMerchantOffer": "2% Cash back",
                "merchantOfferDescription": "Earn 2% Cash back at LEGO.",
                "locationCount": "10",
                "partnerId": "2537",
                "alphaIndex": "l",
                "spend": "",
                "clickTrend": "",
                "fundingCategory": "FEATURED",
                "bonusEarned": false,
                "stores": [
                    {
                        "storesId": "232232",
                        "name": "Bed Bath & Beyond",
                        "locationName": "Mira Loma",
                        "address": "6365 Pats Ranch Road",
                        "city": "Mira Loma",
                        "state": "CA",
                        "zip": "91752",
                        "longtitude": "-117.54465999999999",
                        "latitude": "33.972551000000003",
                        "phone": "7568142562",
                        "venueId": "",
                        "notes": "Next to shoprite",
                        "distance": "0.0"
                    }
                ]
            },
            {
                "offerId": "214318",
                "merchantPartnerName": "Under Armour",
                "merchantLogoFileNameUrl": "https://images.affinitysolutions.com/common/images/underarmour_120x60.jpg",
                "merchantPartnerId": "3358",
                "offerTermsAndConditions": "Offer valid through 09-30-2022. This offer cannot be combined with any other offer, coupon code(s), or promotion, unless available through this site. Offers are subject to change. Points are earned by clicking the Shop Now button associated with this offer to be redirected to the retailer’s website, then making a qualified purchase using your uChoose Rewards |CARDTYPE|. Points are awarded based on the net price of eligible goods and services, excluding tax, shipping and handling or any special services. Offer not valid on purchases of certain restricted consumer electronic products, charity/promotional items, gift cards and on quantities of five or more of the same product purchased by resellers for the sole purchase of re-sale. Points are added to your Points balance within 30 days of purchase or 30 days after travel completion. Any return, exchange, or other adjustment of your qualifying purchase may result in your purchase being ineligible for Points and any Points already earned may be deducted from your account. Points will not be earned on purchases made with third-party partners where the customer is leaving the uChoose Rewards® website. Purchases made with Google Wallet may not be eligible for Points. Other restrictions may apply.
Rewards cannot be earned on orders placed by Under Armour employees or Under Armour sponsored athletes. Offer not valid on purchases of gift cards. Orders suspected as reseller activity do not earn rewards.",
                "merchantOfferExternalUrl": "https://www.awin1.com/awclick.php?gid=353819&mid=15431&awinaffid=249915&linkid=2307530&clickref=40XAUENqc888840",
                "offerValueDescription": "",
                "categories": [
                    {
                        "categoryId": "8419",
                        "categoryDescription": "Jewelry"
                    },
                    {
                        "categoryId": "8389",
                        "categoryDescription": "Apparel, Accessories & Shoes"
                    }
                ],
                "offerExpirationDate": "2022-09-30",
                "requiresActivation": false,
                "offerValue": "3",
                "activated": false,
                "shopType": [
                    "ONLINE"
                ],
                "offerDescription": "Earn 3 Points per $1 at Under Armour.",
                "shortMerchantOffer": "3 Points per $1",
                "merchantOfferDescription": "Earn 3 Points per $1 at Under Armour.",
                "locationCount": "0",
                "partnerId": "3358",
                "alphaIndex": "u",
                "spend": "",
                "clickTrend": "",
                "fundingCategory": "NONE",
                "bonusEarned": false,
                "stores": null
            }
        ]
    }
}
```
