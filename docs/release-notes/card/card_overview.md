# Card overview

 Card API gives a financial institutions and cardholders a robust set of features to help manage and maintain their card information.

<span style="color:#ff6600;">**Platform Support:**</span> **DBE**=Debit Enhanced EPOC, **CGW**=Credit Gateway, **CSL**=Credit Select 


<span style="color:#ff6600;">**PAN tokenization:**</span>  The primary account number (PAN) is replaced with a surrogate value called a token. is replaced with a surrogate value called a token.  and _non-transaction_ tokens (NTT). This is a security upgrade because when you no longer pass encrypted card numbers, you eliminate the risk of decryption with a key; PAN NTT has no key and is tokenized, meaning it cannot be re-identified. By using NTTs, you can reinforce customer trust in your API product suite. 



 <h3 style="text-align: center">Features</h3>

<style>
.col-md-4 ul li {
    list-style: none;
}
</style>

<div class="row" style="text-align:center;" markdown=1>
<div class="col-md-4" markdown=1>

*   ![](assets/images/manage-card.png)
    
    #### Manage
    
    Retrieve and update the status and reason codes for a debit card

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/security-card.png)
    
    #### Security
    
    Increase touchpoints to deactivate or re-activate a card, minimizing unauthorized transactions.

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/access-card.png)
    
    #### Access card details
    
    Real-time retrieval of card details: card numbers, expiration dates and card security codes.
    
</div>
</div>

The following features are supported by Card Developer:

#### PAN tokenization
   * replaces sensitive card numbers with, a token, a de-identified placeholder.
   * removes the need to secure data at rest or during transit.
   * supports clients that are not PCI compliant.
   * _noted higher security difference from encryption_.
     
&nbsp; &nbsp;&nbsp;**Required**: An activated data defense tokenization service.


**Notes on data at rest and in transit**

* Data at rest is inactive data that is stored and not moving between devices or networks. Tokenization at rest protects this data from unauthorized access, data breaches, and physical theft. 
* Data in transit is data that is being transferred between two nodes of a network. Tokenization in transit protects this data from decryption  and otherwise tampering during transmission.

#### Card features

<span style="color:#ff6600;">**Activation**</span> feature helps clients empower their cardholders to quickly activate cards online, through online mobile banking or other channels or directly with a representative. Expanding activation channels and improving digital touchpoints supports card adoption and use. _Supports Pan Tokenization (non-transaction token: NTT)_

   * **Activate card**: activate a card instantaneously after issue. The API can be integrated across multiple channels such as Online Banking, the Customer Service Portal, and IVR.
   * **Activation search**: retrieve the current activation status of a card including, other pertinent details like the activation date, activation method, and last activation attempt through a specific operation.
 
<span style="color:#ff6600;">**Add**</span> feature adds a new card record modeled on an existing card number, account number or FI defaults (logo, prefix, card class). _Supports Pan Tokenization (non-transaction token: NTT)_

   * **Add card:** adds a primary cardholder record to Fiserv system by way of a PAN based on an existing PAN (copy) or a default template that the institution has established.
   * **Non-transaction token search:** NTT searches on card numbers and returns PAN non-transaction tokens. 
 

<span style="color:#ff6600;">**Audit**</span> feature retrieves the up to six months of cardholder audit history. 

   * **Audit record details:** retrieves _audit records details_ for card numbers.
   * **Audit log search"::** retrieves _audit log search_ for card numbers. Response time varies based on search criteria. 
  
 

<span style="color:#ff6600;">**Compromised cards**</span> feature returns a details of compromised cards for both debit and credit for the provided cardnumber. The following informtion is required for a list or details of compromised cards:

  * cardnumber
  * networkalert
  * fromdate
  * todate
  * pageLimit
  * pageOffset

<span style="color:#ff6600;">**Demographics**</span> feature retrieves and updates details beyond basic cardholder information--including address, contact information, and TCPA revocation information--using the full card number. It can update the address and contact information based on ATM-specific preferences for the cardholder.  _Supports Pan Tokenization (non-transaction token: NTT)_

   * **Address:** update address information of a cardholder.
   * **Demographics search:** retrieve additional cardholder information based on card type, card number or member number.
   * **Contact:** update contact information for a cardholder.
 

<span style="color:#ff6600;">**Details**</span> feature retrieves basic cardholder information using the full card number or other details such as email address, last name and phone. You can you Details endpoint to retrieve commonly known cardholder information for use with other Card Developer Card APIs on entities that don't store sensitive card information. _Supports Pan Tokenization (non-transaction token: NTT)_

   * **Cardholder search:** retrieve cardholder information based on other commonly known information. 
   * **Additional info search:** retrieve additional information of a cardholder.
   * **Additional info:** update the additional information of a cardholder.
   * **ATM preferences search:** retrieve  ATM preferences for a cardholder. Applies to debit card program.
   * **ATM preferences:** update ATM preferences for a cardholder. Applies to debit card program.
 

<span style="color:#ff6600;">**Digital Card display**</span> feature provides consumers the ability to digitally display card details prior to receiving their physical plastic or the need arises for an established card.​ Consumers can immediately retrieve card number, expiration date and CVV to immediately perform ecommerce transactions.

   * **Auth details:** retrieve CVV and expiration date information for any given card number.
The card identifier (PAN) is required to retrieve the relevant card details.

 

<span style="color:#ff6600;">**Limits**</span> feature maintains daily online and offline limits for ATM and POS transactions for a selected debit cardholder. Only available for debit card programs. _Supports Pan Tokenization (non-transaction token: NTT)_

   * **Search:** return the limit values for a given card.
   * **Daily:** override the daily limit values for a specific card.
   * **OpenToBuy:** update the open to buy limit values for a specific card.
   * **Velocity:** update maximim times user per period limit for a specific card.
   * **Default:** set the cardholder limits to default values established by the FI at the Cardbase\Card Class settings.
 

<span style="color:#ff6600;">**Order**</span> feature retrieves order history and updates or cancels a pending card order. _Supports Pan Tokenization (non-transaction token: NTT)_
   * **Search:** retrieve order details of a given card.
   * **Order:** update or cancel pending orders for specified cards. Limited to EPOC and Credit Gateway. 
 

<span style="color:#ff6600;">**PIN**</span> feature resets cardholder's number of PIN attempts to zero (0). This feature resets a PIN in real-time using mobile or online banking. _Supports Pan Tokenization (non-transaction token: NTT)_

   * **Set PIN:** A PIN chose option on the mobile app or with online banking. This eliminates personal branch ATM visits or phonecalls to set a PIN. Limited to debit card programs. 
   * **Reset PIN attempts:** updates the number of PIN tries to zero (0) when the number of attempts exceeds the maximum allowed limit. Only available for debit card programs. 
   * **Pin offset:** 4-digit numeric element calculated to set PIN number for a card.
 


<span style="color:#ff6600;">**Related Accounts**</span> feature retrieves and maintains account details of specified debit cards. _Supports Pan Tokenization (non-transaction token: NTT)_

   * **Search:**  retrieves account association details.
   * **Add:**  adds account associations.
   * **Update:**  updates account associations.
   * **Delete:** deletes account associations.

     
<span style="color:#ff6600;">**Replacement**</span> feature reorders specified cards. _Supports Pan Tokenization (non-transaction token: NTT)_

   * **Order replacement:** creates an order to replace card, same card number.
   * **Instant issuance:** replaces a plastic for an existing cardnumber without sending an order to the card producer. Only available for debit card programs. 
 
 

<span style="color:#ff6600;">**Transaction**</span> feature retrieves recent card transactions history and searches for multiple transactions by specific search criteria, multiple dates and multiple merchant. _(non-transaction token: NTT)_

   * **Search:** retrieves transaction details of a given card based on the criteria submitted. 
   * **Terminal search:** retrieves transaction details for a specified terminal. Available for EPOC and Credit Gateway only.
 

<span style="color:#ff6600;">**Update status**</span> feature retrieves and updates the status and reason codes for specified debit cards. Cards can be identified by either card or member numbers. An update example is to deactivate or re-activate specified cards. _Supports Pan Tokenization (non-transaction token: NTT)_

   * **Status:** updates the card status
   * **Search:** retrieves the card status 
To perform maintenance on the card record, the cardholder ID (PAN) is provided to read the relevant record. They system returns the required schema that contains card details. Use this schema to edit the information and sent a request to update the record.

