## Event Streaming – Webhook

### What Is a Webhook?

A webhook is a way for web applications to communicate with each other in real-time and facilitate application to application communication whenever a certain event happens. Unlike the traditional request-response model, where a server must continually check or “poll” another server for a specific piece of data, a webhook delivers data automatically as soon as it becomes available. This real-time data transfer capability means that systems can react real-time to events, which improves processes and ensures timely data delivery. Events will be generated for non-monetary changes on Fiserv Card Services. Push notifications are sent to the provided subscribers endpoint. Events are available for subscription after successful contract/onboarding with Fiserv for the Event Streaming – Webhook product has been completed. 

Please [Click Here](https://qa-developerstudio.fiserv.com/product/CardDeveloper/docs/?path=docs/webhook/cardactivation-1.0.0.md&branch=develop) to see Complete list of available events for Subscription.

Subscription is available to one or more events; requests must be submitted and approved for receiving events. The process for applying for subscription is described below. 

## Webhook Onboarding Process



<a href="#one">Initiate Request</a>

<a href="#two">Subscription Review and Setup</a>

<a href="#three">Onboarding Complete</a>

<h3 id="one">Initiate Request</h3>

Initiate the webhook onboarding request by supplying the following information.

<style>
.col-md-4 ul li {
    list-style: none;
}
</style>

<div class="row" style="text-align:center;" markdown=1>
<div class="col-md-4" markdown=1>

*   ![](assets/images/your-company-basic-information.png)
    
    #### Add Company Information
    
    Add basic company information here

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/basic-webhook-information1.png)
    
    #### Add Webhook Information
    
    Add basic webhook information here

</div>
<div class="col-md-4" markdown=1>

*   ![](assets/images/card-developer-request-info2.png)
    
    #### Add Card Developer Request Information

    
    Add notification email(s) here
    
</div>
</div>
<div class="row" style="text-align:center;" markdown=1>
![](assets/images/webhook-is-created.png)
</div>

**Client Type** Digital Provider or Individual Financial Institution selection. Digital Provider will serve multiple financial institutions or clients. Financial Institution subscribing to individual financial institution events.

**Company ID / Client ID** Fiserv assigned Client ID an 8-digit identifier, i.e. 12345678

**Client Logo** Fiserv assigned Client Logo or Digital Provider Expanded Logo; Unique 4-character alphanumeric identifier that Fiserv assigns i.e. FIID

**Webhook URL** A webhook URL is a user-defined HTTP endpoint that is provided by the Client that can receive the event requests and process them.

**Health check URL** Optional field. A health check URL is an HTTP endpoint that is used to monitor the health of an application. URL is provided to test/ping to determine if the URL is up and running.

**Notification Email** Email(s) that will receive notifications as part of the subscription to the webhook.

**PCI Compliant (Card Format)** Selection of card number (PAN) format to be included in Events. Choices: PAN in clear, PAN Token, or PAN Masked

**SSN Format** Selection of social security number format to be included in Events. Choices: Masked or social security number in clear

**Status (Webhook enablement)** Selection of individual webhook enablement.  Button to enable or disable the webhook.

<h3 id="two">Subscription Review and Setup</h3>

<div class="row" style="text-align:center;" markdown=1>
![](assets/images/webhook.png)
 </div>


After submitting your subscription request, Fiserv team will review and approve. Once accepted, the webhook subscription will be set up based on the information supplied. Notification email(s) provided will be used for future communication on this subscription. Notification email will be sent when application request is approved, rejected, or if there is any issue with Webhook URL or health check URL.

<h3 id="three">Onboarding Complete</h3>

After successful approval and setup, this confirmation email will be sent to the email(s) provided: 

<div class="row" style="text-align:center;" markdown=1>
    <div style="width:20%; margin: auto;">
![](assets/images/webhook-new.png)
</div>
</div>


<div class="row" style="text-align:center;" markdown=1>
<img src="./assets/images/webhook-new.png"  width="400"/>
</div>
<img src="https://media.giphy.com/media/cFkiFMDg3iFoI/giphy.gif" width="300" />


**Additional Information**
Subscribed events will be sent to the configured webhook URL.

After initial onboarding, the attributes shown below may be altered by the client at any time.

  •	  **Status (Is webhook enabled)** Indicates whether a webhook URL endpoint is enabled.

  •	  **Notification Email** Email(s) to receive notifications related to webhook subscription.

  •	  **Webhook Events** Subscribe or unsubscribe to available events.

Events that are pending for approval cannot be modified while in review process.

[Contact Us](https://www.fiserv.com/en/about-fiserv/contact-us.html) to edit or update any additional details.


