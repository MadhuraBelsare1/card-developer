# Before You Start
### Developer Studio for Card Developers
A company of any type or size can offer company-branded digital applications that embed the range of services and capabilities presented by Fiserv using the Fiserv APIs.  The end user customer can create, update, and control the financial services provided by Fiserv. The user experience belongs to the company.  It is a Company application powered by Fiserv.

Clients can use APIs to interact with Fiserv products. Communication is supported between two trusted endpoints. In this document, the following terms are defined as:

* **Server** - One or more endpoint Servers residing at Fiserv datacenters.  These servers integrate with the financial back-end and transaction authorization systems.

* **Client** - An application built by any registered company, such as Digital Providers, Account Processors, Application Service Providers (ASP) or a Financial Institution.

Two-way communication employs mutually authenticated HTTPS traffic for transport security.  Clients must also obtain time-limited tokens to make requests.

The Developer Studio for Card Developers, also known as the Card Developer Workspace, provides the information you need to use the Fiserv APIs, consult the interactive "API explorer" section in the left navigation pane to access deep technical information for each API. Also, Card Developer Workspace is used to manage the Fiserv API Keys/Credentials acquired for the Company's App.

* **Create Account** - Clients create the necessary credentials on Developer Studio. This is the initial step in the process. These credentials are used to log into Developer Studio and create a Workspace.

* **Create Workspace** - Clients create Card Developer Workspace for their Company (please note that Developer Studio provides other workspace types for other purposes). The Card Developer Workspace contains the API Keys/Credentials of the Client's company. A Sandbox API key is created automatically upon the workspace creation.

* **Add API Keys** - Clients add API Keys to the workspace (also previously known as APPs or APP keys). The API Key and Secret, used to obtain an access token, are viewable upon creation. Please note that API Keys for Fiserv Production environment need to be approved. Also, Clients need to register with Fiserv and have a contract before the API Keys for Fiserv Production environment can be approved. Please see: [Registration](?path=docs/gettingstarted/registration.md)


Clients can establish two roles, with differing capabilities in the Card Developer Workspace.  These are as follows.

* **Company Administrator** - Designated organization representative with all administrative privileges to manage the Card Developer Workspace, invite company developers and also designate secondary company administrator. A client establishes the Administrator when creating the Card Developer workspace (the creator of the Card Developer Workspace is the Administrator).  The Administrator can delete the Card Developer Workspace. Also see: [Company Administrator](?path=docs/gettingstarted/company-administrator.md)

* **Company Developer** - Once added, a Company Developer can add new Sandbox API Keys, visible to other Developers in the Company to use in the Company App(s). The Company Developer can test API Keys in the Sandbox environment at any time. Company Developers also get access to the Company Certification and/or Production API Keys created by the Company Administrator. Also see: [Company Developer](?path=docs/gettingstarted/company-developer.md)
  
The Card Developer Workspace is not a server endpoint and API Keys cannot be staged or tested directly on the Card Developer Workspace. Developers must use an independent method, such as Curl or Postman, pointed at the Sandbox or Production endpoints to test API Keys.


## Validation Environment
The sandbox environment is the developer external testing ground. Clients can mimic the production environment and create simulated responses. The simulated responses are based on test cases and data from Fiserv. The sandbox environment is identical to production but points to a simulated API environment for API responses. Also see: [Environments](?path=docs/gettingstarted/environments.md)


## Note to the Company Administrators

### Migration of Existing API Keys and Company Developers

If you already have API Keys and Company Developers, your existing API Keys and Company Developers can be migrated to the Card Developer Workspace. The system will prompt for your decision to whether migrate the existing API Keys and Company Developers or not.

#### How Existing API Keys and Company Developers Migrated

If you currently have API keys and Company Developers, you can migrate your existing API keys and Company Developers to the Card Developer Workspace.
When the Company Administrator creates a Card Developer Workspace, the Company Administrator must use the same email address used previously to create a new account on Developer Studio.  The system checks for an alpha-numeric match and is case sensitive. 
**Note:** The migrated Company Developers are automatically invited to join the Card Developer Workspace.


### Existing API Keys and Company Developers Migration Flow

#### Company Administrator creates a Card Developer Workspace

![migrated-workspace.png](assets/images/migrated-workspace.png)

#### Company Administrator can choose whether to migrate the existing API Keys or not

![migrated-workspace-2.png](assets/images/migrated-workspace-2.png)

#### Company Administrator chooses to migrate the existing API Keys

![migrated-workspace-3.png](assets/images/migrated-workspace-3.png)

#### Company Administrator is asked to review and create the Card Developer Workspace

![migrated-workspace-4.png](assets/images/migrated-workspace-4.png)

#### Company Administrator can see the migrated API Keys

![migrated-workspace-5.png](assets/images/migrated-workspace-5.png)

#### Company Administrator can see the migrated Company Developers

![migrated-workspace-6.png](assets/images/migrated-workspace-6.png)

