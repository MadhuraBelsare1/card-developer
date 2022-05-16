 Card API enables a financial institution or cardholder to manage and maintain their card information through various touchpoints.

<span style="color:#ff6600;">**Platform Support:**</span> **DBE**=Debit Enhanced EPOC, **CGW**=Credit Gateway, **CSL**=Credit Select 

### Features

![](https://card.developer.fiserv.com/sites/default/files/manage%20card%20.png)
    
    
#### Manage
    
Retrieve and update the status and reason codes for a debit card

![](https://card.developer.fiserv.com/sites/default/files/Security%20Card.png)
    
   
#### Security
    
Increased touchpoints to deactivate or re-activate a card, increasing fraud mitigation

![](https://card.developer.fiserv.com/sites/default/files/Access%20Card.png)

   
#### Access Card Details
    
Retrieve the card number, expiration date and CVV in real time

<span style="color:#ff6600;">**Activation**</span> feature helps clients empower their cardholders to quickly activate cards online, through online mobile banking or other channels or directly with a representative. Expanding activation channels and improving digital touchpoints supports card adoption and use.

* **Activate Card**: activate a card instantaneously after issue. The API can be integrated across multiple channels such as Online Banking, the Customer Service Portal, and IVR.
* **Activation Search**: retrieve the current activation status of a card including, other pertinent details like the activation date, activation method, and last activation attempt through a specific operation.

<span style="color:#ff6600;">**Details**</span> feature provides for searches to retrieve basic cardholder information using full card number or other details such as email address, last name and phone. The service enables entities that do not store and maintain sensitive card information, such as digital providers needing data for use with other card APIs, to gain access to basic cardholder information based on commonly known information.

* **Cardholder Search**: retrieve cardholder information based on other commonly known information. 

<span style="color:#ff6600;">**Digital Card Display**</span> feature provides consumers the ability to digitally display card details prior to receiving their physical plastic or the need arises for an established card.​ Consumers can immediately retrieve card number, expiration date and CVV to immediately perform ecommerce transactions.

_Requires subscription of Instant Digital Issuance solution_

* **Auth Details**: enables the retrieval of CVV and expiration date information for any given card number.

The card identifier (PAN) is required to retrieve the relevant card details.

<span style="color:#ff6600;">**Limit**</span> feature enables users to maintain daily online and offline limits for ATM and POS transactions for a selected debit cardholder. Only available for debit card programs. 

* **Search:** returns the limit values for a given card.
* **Daily:** overrides the daily limit values for a specific card.
* **OpenToBuy:** updates the open to buy limit values for a specific card.
* **Velocity:** updates maximim times user per period limit for a specific card.
* **Default:** sets the cardholder limits to default values established by the FI at the Cardbase\\Card Class settings.

<span style="color:#ff6600;">**PIN**</span> feature allows for clients to have the ability to reset the number PIN tries for their cardholders to zero (0) as well as having the ability to set a PIN in real-time via mobile or online banking. 

* **Set PIN**: allows the consumer to choose their own PIN within the mobile app or online banking without the need to visit a branch ATM or to call IVR operations to set PIN.
* **Reset PIN Attempts**: update the number of PIN tries to zero (0) when the number of attempts has exceeded the maximum allowed limit.
* **Pin Offset: **4-digit numeric element calculated to set PIN number for a card. 

<span style="color:#ff6600;">**Replacement**</span> feature allows clients to reorder a particular card. 

* **Order Replacement: ** creates an order to replace card, same card number.

<span style="color:#ff6600;">**Transaction**</span> feature enables cardholders to retrieve recent card transactions history as well as allow cardholders to search for multiple transactions by specific search criteria, multiple dates and multiple merchant.

* **Search:** retrieve transaction details of a given card based on the criteria submitted. 

<span style="color:#ff6600;">**Update Status**</span> feature allow clients to retrieve and update the Status and Reason codes for a debit card. Cards may be identified by Card Number or Member Number. The API may be used to provide client users convenient access to maintain cards or to allow cardholders to perform simple updates, such as to deactivate or re-activate a card. 

* **Details**: view or change the card status

To perform maintenance on the card record, the cardholder ID (PAN) is provided to read the relevant record. They system returns the required schema that contains card details. Use this schema to edit the information and sent a request to update the record.