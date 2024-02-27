Fraud API enables a financial institution or cardholder to manage, mitigate fraud losses and create travel exemptions while minimizing friction for the consumer.

<span style="color:#ff6600;">**Platform Support:</span> DBE**\=Debit Enhanced EPOC, **CGW**\=Credit Gateway, **CSL**\=Credit Select

 <h3 style="text-align: center">Features</h3>

<style>
.col-md-4 ul li {
    list-style: none;
}
</style>

<div class="row" style="text-align:center;" markdown=1>
<div class="col-md-4" markdown=1>

*   ![](https://card.developer.fiserv.com/sites/default/files/Alert_0.png)
    
    #### Cardholder Alerts
    
    Give cardholders security functionality to confirm potential fraud, unblock their card, and increase retention.
    
</div>
<div class="col-md-4" markdown=1>
    
*   ![](https://card.developer.fiserv.com/sites/default/files/Fraud%204.png)
    
    #### Convenient Experience
    
    Empower cardholders to manage exemptions as well and quickly respond to fraud notifications.
    
</div>
<div class="col-md-4" markdown=1>
    
*   ![](https://card.developer.fiserv.com/sites/default/files/Fraud%203_0.png)
    
    #### Verification
    
    Retrieves media addresses and methods that can be used for cardholder verification.
    
</div>
</div>
    

<span style="color:#ff6600;">**Verification**</span> feature provides digital providers the ability to request an one-time-passcode (OTP) verification for a cardholder via Text, Voice or Email. **Note:** _OTP expires in 10 minutes_

*   **Search Verification**: Retrieves media addresses and methods that can be used for cardholder verification. Possible methods are Voice, Text and Email. Media addresses are semi-masked for cardholder's confidentiality.
*   **OTP Verification:** Generate a OTP for Cardholder verification. 
*   **Validate Verification:** Validation of a OTP sent to a selected media address and method.

                           ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA3UAAAACCAMAAADIHwX2AAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJUExURQAAAKWlpaWlpaK/EAwAAAACdFJOUwCfFiND7QAAAAlwSFlzAAAXEQAAFxEByibzPwAAABxJREFUOE9jYBoFo2AU0BMwMozmulEwCugLGBkA2vsNz2Gb0lUAAAAASUVORK5CYII=)

<span style="color:#ff6600;">**Fraud Alert API**</span> provides integration partners the ability to receive alerts for potential fraudulent transactions, retrieve case data for fraudulent cases, and notify Fiserv of the results of an alert notification.

*   **Search Case**: Retrieve information for fraud cases from Fiserv.
*   **Alert Outcome:** Notify Fiserv of updates to a case under review. Fiserv returns a response that identifies if a case outcome request is accepted or if the request is rejected and why the request was rejected.
*   **Case Close**: Notify Fiserv of a case for potential fraud being closed on the vendor platform.

<span style="color:#ff6600;">**Travel Exemptions API**</span> enables collection and application of all travel exemptions for a specific card number. Any cardholder updates are captured and used by other web services in the authorization rules for each card transaction, reducing false declines and giving users more control over how they use their card. 

*   **Search Exemptions:** Obtain information on all existing travel exemptions for the requested card number.
*   **Add Exemptions:** Add travel exemptions for the requested primary account number (PAN)\\, up to the maximum of two lists. Cardholders can make exemptions by state or country.
*   **Update Exemptions:** Update existing travel exemptions for the requested primary account number (PAN).
*   **Expire Exemptions:** Terminate existing travel exemptions at any time to create a new list, expiring the old version to enable the new list.

#### **Coming Soon!** 

<span style="color:#ff6600;">**Fraud Case**</span> feature will provide the ability to manage a case by way of retrieving detailed case information and viewing case comments.

### FAQs

#### Are travel notices available in online banking within the Travel Exemptions functionality?

The feature is a web-message specification that can be coded to make this possible; however, the online banking tool will need to be modified as well coding to use the service to send and receive the necessary information will need to be done.

#### Exclusions are set by the financial institution through Client Central and provided as part of the Travel Exemptions feature. Do these states/countries need to be excluded from the consumer user interface?

Design of the consumer or internal user interface is outside of the scope of Travel Exemptions feature. However, if an excluded state or country is sent as an exemption an error response message will be sent.

#### Is there a unique error code the Travel Exemption feature detects a request to add a country in the financial institution’s exclusion list?

Yes. The unique code for this scenario WS205.This is different than when a state or country validation can’t occur (e.g. CA for CAN) whose code is WS204.  

#### What is the Fraud Alert feature?

This feature allows an entity outside of CWSi Card Management to be able to retrieve case data regarding fraudulent cases, notifies Fiserv of case results or a case closed. The data contains the case information including card details and up to three (3) transactions that may be considered fraud. This allows the client to determine the locations of where notifications are sent internally and to consumers.

#### What are the prerequisites for implementing the Fraud Alert feature?

All clients who participate in a Risk Solution Set (Risk Essentials, Risk Advisor or Risk Advantage) can implement the Fraud Alert feature.

#### Will the Fraud Alert feature replace my existing notifications?

No. Alerts sent through the Fraud Alert feature are in addition to the existing notifications you are currently sending. When a case is created, the Fraud Alert feature is initiated in conjunction with the first notification type you have in your existing notifications. If a case is closed as “NO FRAUD,” “FRAUD” or the card status is changed to a “Closed” status, the contact attempts stop through both the API and the existing channels, similar to the existing process.

#### Will Automated Risk Exemption Service (ARES) trigger if a transaction is confirmed as not fraud through the Fraud Alert feature?

If a client is signed up for ARES, it executes within minutes. Similar to existing functionality, when a case is closed as “NO FRAUD", ARES is triggered to exempt a cardholder from risk rules for a set amount of time as determined by the client.

#### What is the Travel Exemptions feature?

This is a RESTful message that allows an entity outside of the CWSi card management system to be able to update the cardholder record regarding state and country exemptions.  This will require coding to specification and completing a certifications process as well as interfacing the API to the user interface (for example:  digital app or online banking service).  

#### How does the Travel Exemptions feature work?

Updates will need to be made to the system you want to integrate so that your cardholder or internal staff can enter the necessary data.  That system sends an initial “getTrvlExemptionsList” so that current cardholder record information can be displayed.  Fiserv finds the cardholder’s record and sends all current state and country exemptions along with any location exclusions where you have indicated you don’t want automated exemptions configured.  The cardholder or internal staff make the changes and a follow up message (add, update or expire) is sent to Fiserv.  Fiserv reviews the information and sends back the response (success or error message).   

#### What other risk services does my financial institution require prior to consuming the Travel Exemptions feature?

You need to utilize at least one of the following risk rule tools – TranBlockerSM, Card Risk Mitigation: EnFact® or Card Risk OfficeSM Advantage: RuleManager.  If you are currently on Card Risk Office Essentials, Card Risk Office Advisor or Card Risk Office Advantage) you are able to utilize the Travel Exemptions feature.

#### What are the benefits of the Travel Exemptions feature to the financial institution and the cardholder?

This feature offers the ability to integrate from your own applications into to the Fiserv risk systems in real-time.  It gives you flexibility to have your cardholders to self-service through existing tools they know. 

#### Does the Travel Exemptions feature allow the cardholder to enter future travel plans?

Yes, each cardholder can have two exemptions configured each containing up to 15 locations (states and/or countries).  Each exemption has start and end dates and times.   

#### Can different start and stop dates be set for different countries with the Travel Exemptions feature? For instance, if someone is traveling to five different countries, but to one country per week?

No, exemptions are maintained by group; the group has its own start and end dates.  Each group can contain up to 15 locations (countries and/or states). 

#### What list of countries should be displayed in the internal system that feeds the Travel Exemptions feature?

A standard ISO country list can be used, the API requires 3-character country values and 2-character state values.  You will need to decide how you want to work with your exclusion list.  Some people don’t display these options and others choose to simply let the error message return and address it then. 

#### With the Travel Exemptions feature, how are exclusion groups created?

This is done within the card management system of Debit Processing: Client CentralSM.  A maximum of two exclusion groups can be created.  A maximum of 51 State/Country codes can be part of an individual exclusion group.  The exclusion groups are kept at the client (LOGO) level and contain up to 50 BINs.  

#### If a cardholder calls and says they are driving to a certain state. Is it best to list all of the states under the travel exemptions that they are driving through and the dates?

Yes.
