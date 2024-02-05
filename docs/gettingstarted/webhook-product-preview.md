## Event Streaming – Webhook

### What Is a Webhook?
A webhook is a way for web applications to communicate with each other in real-time and facilitate application to application communication whenever a certain event happens. Unlike the traditional request-response model, where a server must continually check or “poll” another server for a specific piece of data, a webhook delivers data automatically as soon as it becomes available. This real-time data transfer capability means that systems can react real-time to events, which improves processes and ensures timely data delivery. Events will be generated for non-monetary changes on Fiserv Card Services. Push notifications are sent to the provided subscribers endpoint. Events are available for subscription after successful contract/onboarding with Fiserv for the Event Streaming – Webhook product has been completed. 

### Event Streaming – Webhook Events Available for Subscription
  •	Card Activation - This event is generated when a card is activated.

  •	Card Expiration Date - This event is generated when a card expiration date is updated due to card replacement or card renewal.

  •	Card Limits - This event is generated when a card limit is updated.

  •	Card PIN Offset - This event is generated when PIN offset is updated.

  •	Demographics – Events are generated when there is a change on the Card Address, Card Contact Information, Cardholder Information, or Card Security Information.

  •	Card Add – This event is generated when a card is added.

  •	Card Reissue – This event is generated when a card is reissued.

  •	Card Status – This event is generated when a card status is updated.

TODO: How do we ensure that as Events are Added this section is updated? – Specifically for Feb – Disputes and Shipping to be added?

Subscription is available to one or more events; Requests must be submitted and approved for receiving events. The process for applying for subscription is described below. 

### Webhook Onboarding Process
1. Initiate Request
2. Request Review
3. Approval and Setup
4. Onboarding Complete

<ins>Initiate Request</ins>
Initiate the webhook onboarding request by supplying the following information.

**Client Type** Digital Provider or Individual Financial Institution selection. Digital Provider will serve multiple financial institutions or clients. Financial Institution subscribing to individual financial institution events.

**Company ID / Client ID** Fiserv assigned Client ID an 8-digit identifier, i.e. 12345678

**Client Logo** Fiserv assigned Client Logo or Digital Provider Expanded Logo; Unique 4-character alphanumeric identifier that Fiserv assigns i.e. FIID

**Webhook URL** A webhook URL is a user-defined HTTP endpoint that is provided by the Client that can receive the event requests and process them.

**Health check URL** Optional field. A health check URL is an HTTP endpoint that is used to monitor the health of an application. URL is provided to test/ping to determine if the URL is up and running.

**Notification Email** Email(s) that will receive notifications as part of the subscription to the webhook.

**PCI Compliant (Card Format)** Selection of card number (PAN) format to be included in Events. Choices: PAN in clear, PAN Token, or PAN Masked

**SSN Format** Selection of social security number format to be included in Events. Choices: Masked or social security number in clear

**Status (Webhook enablement)** Selection of individual webhook enablement.  Button to enable or disable the webhook.
<ins>Subscription Review and Setup</ins>

After submitting your subscription request, Fiserv team will review and approve. Once accepted, the webhook subscription will be set up based on the information supplied. Notification email(s) provided will be used for future communication on this subscription. Notification email will be sent when application request is approved, rejected, or if there is any issue with Webhook URL or health check URL.

<ins>Onboarding Complete</ins>
After successful approval and setup, a confirmation email will be sent to the email(s) provided. 

**Additional Information**
Subscribed events will be sent to the configured webhook URL.

After initial onboarding, the attributes shown below may be altered by the client at any time.

  •	Status (Is webhook enabled) Indicates whether a webhook URL endpoint is enabled.

  •	Notification Email Email(s) to receive notifications related to webhook subscription.

  •	Webhook Events Subscribe or unsubscribe to available events.

Events that are pending for approval cannot be modified while in review process.

Contact Us to edit or update any additional details.

TODO:
Insertion of wireframes screen shots applicable to each section 
Separate Technical Section will include the Schemas and Samples for each Event.
