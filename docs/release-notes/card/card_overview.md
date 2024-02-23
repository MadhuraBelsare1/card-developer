 Card API enables a financial institution or cardholder to manage and maintain their card information through various touchpoints.

<span style="color:#ff6600;">**Platform Support:**</span> **DBE**=Debit Enhanced EPOC, **CGW**=Credit Gateway, **CSL**=Credit Select 


<span style="color:#ff6600;">**PAN Tokenization:**</span> Our PAN Token service replaces the use of actual card numbers with a token referred to as a Non-Transaction Token. Using these tokens instead of PANs reduce the impact of a card compromise. Support is now available on most features below, with expansion planned for additional APIs.

*Activation of Data Defense Tokenization service is required.*

   * PAN Tokenization replaces the sensitive card number with a non-sensitive placeholder called 'token'.
   * Different from encryption where a key can be used to detokenize to the original information.
   * Eliminates the need for securing the data at rest and during transit, support clients that are not PCI compliant.

### <p style="text-align: center;">Features</p>

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
    
    Increased touchpoints to deactivate or re-activate a card, increasing fraud mitigation

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/access-card.png)
    
    #### Access Card Details
    
    Retrieve the card number, expiration date and CVV in real time
    
</div>
</div>

<span style="color:#ff6600;">**Activation**</span> feature helps clients empower their cardholders to quickly activate cards online, through online mobile banking or other channels or directly with a representative. Expanding activation channels and improving digital touchpoints supports card adoption and use. *Supports Pan Tokenization (Non-Transaction Token - NTT)*

   * **Activate Card**: activate a card instantaneously after issue. The API can be integrated across multiple channels such as Online Banking, the Customer Service Portal, and IVR.
   * **Activation Search**: retrieve the current activation status of a card including, other pertinent details like the activation date, activation method, and last activation attempt through a specific operation.
 
<span style="color:#ff6600;">**Add**</span> feature allows Financial Institutions to add a new card record modeled on an existing card number, account number or FI defaults (logo, prefix, card class). Supports Pan Tokenization (Non-Transaction Token - NTT)

   * **Add Card:** adds a primary cardholder record to Fiserv system by way of a primary account number (PAN) based on an existing PAN (copy) or a default template that the institution has established.
   * **Non-Transaction Token Search:** allows for search of a non-transaction token for an existing PAN 
 

<span style="color:#ff6600;">**Audit**</span> feature allows user to retrieve the audit details of a given debit card enabling investigation of cardholder data and provides six months of cardholder audit history. 

   * **Audit Search:** retrieves audit log records. Response time will vary based on search criteria. 
   * **Audit Details:** retrieves the details of audit log records.
 

<span style="color:#ff6600;">**Demographics**</span> feature provides the ability to retrieve and update details beyond basic cardholder information -- including address, contact information, and TCPA revocation information -- using the full card number. The service also enables the update of address and contact information along with related ATM-specific preferences for a given cardholder.  _Supports Pan Tokenization (Non-Transaction Token - NTT)_

   * **Address:** updates address information of a cardholder.
   * **Demographics Search:** retrieves additional cardholder information based on card type, card number or member number.
   * **Contact:** updates contact information for a cardholder.
 

<span style="color:#ff6600;">**Details**</span> feature provides for searches to retrieve basic cardholder information using full card number or other details such as email address, last name and phone. The service enables entities that do not store and maintain sensitive card information, such as digital providers needing data for use with other card APIs, to gain access to basic cardholder information based on commonly known information. _Supports Pan Tokenization (Non-Transaction Token - NTT)_

   * **Cardholder Search:** retrieves cardholder information based on other commonly known information. 
   * **Additional Info Search:** retrieve additional information of a cardholder.
   * **Additional Info:** update the additional information of a cardholder.
   * **ATM Preferences Search:** retrieve  ATM preferences for a cardholder. Applies to debit card program.
   * **ATM Preferences:** update ATM preferences for a cardholder. Applies to debit card program.
 

<span style="color:#ff6600;">**Digital Card Display**</span> feature provides consumers the ability to digitally display card details prior to receiving their physical plastic or the need arises for an established card.​ Consumers can immediately retrieve card number, expiration date and CVV to immediately perform ecommerce transactions.

   * **Auth Details:** enables the retrieval of CVV and expiration date information for any given card number.
The card identifier (PAN) is required to retrieve the relevant card details.

 

<span style="color:#ff6600;">**Limit**</span> feature enables users to maintain daily online and offline limits for ATM and POS transactions for a selected debit cardholder. Only available for debit card programs. _Supports Pan Tokenization (Non-Transaction Token - NTT)_

   * **Search:** returns the limit values for a given card.
   * **Daily:** overrides the daily limit values for a specific card.
   * **OpenToBuy:** updates the open to buy limit values for a specific card.
   * **Velocity:** updates maximim times user per period limit for a specific card.
   * **Default:** sets the cardholder limits to default values established by the FI at the Cardbase\Card Class settings.
 

<span style="color:#ff6600;">**Order**</span> feature enables users to retrieve order history as well as allows cardholders to update or cancel an pending card order. _Supports Pan Tokenization (Non-Transaction Token - NTT)_
   * **Search:** retrieves order details of a given card.
   * **Order:** updates or cancel a pending order for a particular card. Order update is available for EPOC and Credit Gateway only. 
 

<span style="color:#ff6600;">**PIN**</span> feature allows for clients to have the ability to reset the number PIN tries for their cardholders to zero (0) as well as having the ability to set a PIN in real-time via mobile or online banking. _Supports Pan Tokenization (Non-Transaction Token - NTT)_

   * **Set PIN:** allows consumer to choose their own PIN within the mobile app or online banking without the need to visit a branch ATM or to call IVR operations to set PIN. Only available for debit card programs. 
   * **Reset PIN Attempts:** updates the number of PIN tries to zero (0) when the number of attempts exceeds the maximum allowed limit. Only available for debit card programs. 
   * **Pin Offset:** 4-digit numeric element calculated to set PIN number for a card.
 

<span style="color:#ff6600;">**Replacement**</span> feature allows clients to reorder a particular card. _Supports Pan Tokenization (Non-Transaction Token - NTT)_

   * **Order Replacement:**  creates an order to replace card, same card number.
   * **Instant Issuance:** allows the institution to replace a plastic for an existing cardnumber without sending an order to the card producer. Only available for debit card programs. 
 

<span style="color:#ff6600;">**Related Accounts**</span> feature allows clients to retrieve and maintain account details of a given debit card. _Supports Pan Tokenization (Non-Transaction Token - NTT)_

   * **Search:**  retrieves account association details.
   * **Add:**  adds account associations.
   * **Update:**  updates account associations.
   * **Delete:** deletes account associations.
 

<span style="color:#ff6600;">**Transaction**</span> feature enables cardholders to retrieve recent card transactions history as well as allow cardholders to search for multiple transactions by specific search criteria, multiple dates and multiple merchant. _(Non-Transaction Token - NTT)_

   * **Search:** retrieves transaction details of a given card based on the criteria submitted. 
   * **Terminal Search:** retrieves transaction details for a specified terminal. Available for EPOC and Credit Gateway only.
 

<span style="color:#ff6600;">**Update Status**</span> feature allow clients to retrieve and update the Status and Reason codes for a debit card. Cards may be identified by Card Number or Member Number. The API may be used to provide client users convenient access to maintain cards or to allow cardholders to perform simple updates, such as to deactivate or re-activate a card. _Supports Pan Tokenization (Non-Transaction Token - NTT)_

   * **Status:** updates the card status
   * **Search:** retrieves the card status 
To perform maintenance on the card record, the cardholder ID (PAN) is provided to read the relevant record. They system returns the required schema that contains card details. Use this schema to edit the information and sent a request to update the record.

