### Environments

#### Validation Environment
Fiserv provides a sandbox, and production environment for each API. The sandbox environment is the developer external testing ground. Clients can mimic the production environment and create simulated responses based on Fiserv-supplied test cases and data. The sandbox environment is identical to the production but points to a simulated API environment for API responses. 

**Note:** Although the Developer Studio Workspace does communicate with the Card Developer gateway to enable key authentication, developers cannot directly call APIs from the Developer Studio Workspace. Use other development applications, (e.g., Postman or proprietary software) to make call requests.

 

#### Sandbox
The Company Administrator adds Company API Keys for company projects used by the Company Developers. Invited Developers can view Company API Keys to obtain the required details and credentials. Requests in the sandbox do not have access to real data or the production environment. After testing and validation is complete, the Company Administrator can create production API Keys.

Each API key created generates a unique set of credentials specifically for the sandbox. A sandbox digital certificate is required and is available for download. Please see: [Certificates](?path=/docs/gettingstarted/certificates.md)

Please note that the Sandbox API Key created automatically when a Developer Studio Workspace is created is visible only to the Workspace Creator (also known as the Workspace Owner). API keys added after the Developer Studio Workspace is created are visible to all the Company Developers invited to the workspace.   

**Also see:** [Validate APIs in The Sandbox](?path=/docs/gettingstarted/validate-apis-in-sandbox.md)

 
#### Production
Production API keys can be created by the **Company Administrator**. Each Production API Key supports a set of APIs. The Production APIs supported by the API Production Key are subject to approval by Fiserv. The approval of the Production APIs is dependent on the subscription agreement developed during the initial client registration process.
After the API Keys are officially deployed in production, a production-related X.509 digital certificate is made available, and API secret keys are available in the Developer Studio Workspace.

 

#### API Versioning
Card Developer APIs currently use the URL path to point to the API version.

