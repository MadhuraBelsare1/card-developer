# Before You Start
### Developer Studio for Card Developers
A company of any type or size can offer company-branded digital applications that embed the range of services and capabilities presented by Fiserv using the Fiserv APIs.  The end user customer can create, update, and control the financial services provided by Fiserv. The user experience belongs to the company.  It is a Company application powered by Fiserv.

Clients can use APIs to interact with Fiserv products. Communication is supported between two trusted endpoints. In this document, the following terms are defined as:

* **Server** - One or more endpoint Servers residing at Fiserv datacenters.  These servers integrate with the financial back-end and transaction authorization systems.

* **Client** - An application built by any registered company, such as Digital Providers, Account Processors, Application Service Providers (ASP) or a Financial Institution.

Two-way communication employs mutually authenticated HTTPS traffic for transport security.  Clients must also obtain time-limited tokens to make requests.

The Developer Studio for Card Developers, also known as the Card Developer Workspace, provides the information you need to use the Fiserv APIs, consult the interactive "API explorer" section in the left navigation pane to access deep technical information for each API. Also, Card Developer Workspace is used to manage the Fiserv API Keys/Credentials acquired for the Company's App.

* **Create Account** - Clients create the necessary credentials on Developer Studio. This is the initial step in the process. These credentials are used to log into Developer Studio and create a Workspace.

* **Create Workspace** - Clients create Card Developer workspace (please note that Developer Studio provides other workspace types for other purposes). The Card Developer workspace contains the API Keys/Credentials of the Client's company. A Sandbox API key is created automatically upon the workspace creation.

* **Add API Keys** - Clients add API Keys to the workspace. The API Key and Secret, used to obtain an access token, are viewable upon creation. Please note that API Keys for Fiserv Certification environment and/or Production environment need to be approved. Also, Clients need to register with Fiserv before gaining the ability to create API Keys for Fiserv Certification and/or Production environment. Please see: [Registration](?path=docs/gettingstarted/registration.md).


Clients can establish two roles, with differing capabilities in the Card Developer workspace.  These are as follows.

* **Company Administrator** - Designated organization representative with all administrative privileges to manage the Card Developer workspace, invite company developers and also designate secondary company administrator. A client establishes the Administrator when creating the Card Developer workspace (the creator of the Card Developer workspace is the Administrator).  The Administrator can delete the Card Developer workspace. Also see: [Company Administrator](?path=docs/gettingstarted/company-administrator.md). 

* **Company Developer** - Once added, a Company Developer can add new Sandbox API Keys, visible to other Developers in the Company to use in the Company App(s). The Company Developer can test API Keys in the Sandbox environment at any time. Company Developers also get access to the Company Certification and/or Production API Keys created by the Company Administrator. Also see: [Company Developer](?path=docs/gettingstarted/company-developer.md).

The Card Developer workspace is not a server endpoint and API Keys cannot be staged or tested directly on the Card Developer workspace. Developers must use an independent method, such as Curl or Postman, pointed at the Sandbox or Production endpoints to test API Keys.


## Validation Environment
The sandbox environment is the developer external testing ground. Clients can mimic the production environment and create simulated responses. The simulated responses are based on test cases and data from Fiserv. The sandbox environment is identical to production but points to a simulated API environment for API responses.

**ALSO SEE:** [Environments](?path=docs/gettingstarted/environments.md)


## Note to Company Administrators

### Migration of Existing API Keys and Company Developers

If you already have API Keys and Company Developers, your existing API Keys and Company Developers can be migrated to the Card Developer Workspace. The system will prompt for your decision to whether migrate the existing API Keys and Company Developers or not.

#### How Existing API Keys and Company Developers Migrated

When the Company Administrator creates a Card Developer Workspace, the system checks if the Company has existing API Keys and Company Developers. The system checks for existig API Keys and Company Developers using the Company Administrator email address. Thus if migration of the existing API Kays and Company Developers is desired, the Company Administrator needs to use the same email address used previously. 
The migrated Company Developers are invited automatically to join the Card Developer Workspace.

### Existing API Keys and Company Developers Migration Flow

#### Company Administrator creates a Card Developer Workspace

![migrated-workspace.png](assets/images/migrated-workspace.png)

#### Company Administrator creates a Card Developer Workspace

![migrated-workspace.png](assets/images/migrated-workspace.png)

#### Company Administrator can choose whether to migrate the existing API Keys or not

![migrated-workspace2.png](assets/images/migrated-workspace2.png)

#### Company Administrator chooses to migrate the existing API Keys

![migrated-workspace3.png](assets/images/migrated-workspace3.png)

#### Company Administrator is asked to review and create the Card Developer Workspace

![migrated-workspace4.png](assets/images/migrated-workspace4.png)

#### Company Administrator can see the migrated API Keys

![migrated-workspace5.png](assets/images/migrated-workspace5.png)

#### Company Administrator can see the migrated Company Developers

![migrated-workspace6.png](assets/images/migrated-workspace6.png)
