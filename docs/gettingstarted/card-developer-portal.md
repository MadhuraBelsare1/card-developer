### Card Developer Portal

A company of any type or size can offer company-branded digital applications that embed the range of services and capabilities presented by Fiserv using the Fiserv APIs.  The end user customer can create, update, and control the financial services provided by Fiserv, but the user experience belongs to your company.  It is your application powered by Fiserv.

Clients can use APIs to interact with Fiserv products. Communication is supported between two trusted endpoints. In this document, the following terms are defined as:

 * **Server** - One or more endpoint Servers residing at Fiserv datacenters.  These servers integrate with the financial back-end and transaction authorization systems.
 * **Client** - An application built by any registered company, such as Digital Providers, Account Processors, Application Service Providers (ASP) or a Financial Institution.
Two-way communication employs mutually authenticated HTTPS traffic for transport security.  Clients must also obtain time-limited tokens to make requests.

 

### Card Developer Portal
The API Portal for Card Developers, also known as the Card Developer Portal, provides the information you need to use the Fiserv APIs,  Click APIs to access deep technical information for each API.

The Portal is also where clients register, create and manage their applications.  You can do the following, here at the Portal.

**Register** - Clients create the necessary identity on the Portal.  The Portal creates an ID and a transport certificate.

**Create Apps** - Clients log into the Portal to create applications (apps) in the test Sandbox environment.  Each app gets an API Key and Secret, used to obtain an access token.

**Manage Apps** - Once created, an app can then be promoted into the Fiserv Production environment, or disabled at any time.
Clients of the Fiserv Portal can establish two roles, with differing capabilities.  These are as follows.

**Company Administrator** - Designated organization representative with all administrative privileges to manage company assets, invite company developers and also designate secondary company administrator. A client establishes the Administrator when registering with Fiserv.  The Administrator promotes, demotes or deletes all Company Apps.  Also see: [Company Administrator](https://card.developer.fiserv.com/all-products/getting-started/companyadministrator)

**Company Developer** - Once approved, a Developer can create new apps, visible at first only to the defeloper as My Apps.  The Developer can test these apps in the Sandbox environment at any time.  When ready, the Developer asks the Administrator to promote the app first to Company apps, and then to Production.  Developers also get access to the Company Apps. Also see: [Company Developer](https://card.developer.fiserv.com/all-products/getting-started/companydeveloper)

The Portal is not a server endpoint and apps cannot be staged or tested directly on the Portal. Developers must use an independent method, such as Curl or Postman, pointed at the Sandbox or Production endpoints to test apps.

 

#### Validation Environment
The sandbox environment is the developer external testing ground. Clients can mimic the production environment and create simulated responses based on test cases and data from Fiserv. The sandbox environment is identical to production but points to a simulated API environment for API responses.

**Also See**: [Environments](https://card.developer.fiserv.com/all-products/getting-started/environments)
