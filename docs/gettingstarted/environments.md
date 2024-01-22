### Environments

#### Validation Environment
The Card Developer Portal contains a sandbox and production environment for each API. The sandbox environment is the developer external testing ground. Clients can mimic the production environment and create simulated responses based on Fiserv-supplied test cases and data. The sandbox environment is identical to production but points to a simulated API environment for API responses.

The terms, My Apps or Company Apps, does not directly refer to software applications. No coding or actual call requests are handled from the portal.

**Note:** Although the portal does communicate with the Card Developer gateway to enable key authentication, developers cannot directly call APIs from the portal. Use other development applications, (e.g., Postman or proprietary software) to make call requests.

 

#### Sandbox
The Company Administrator adds Company Apps for company projects used by one or multiple developers. Registered developers can view Company Apps to obtain the required details and credentials. Requests in the sandbox do not have access to real data or the production environment. After testing and validation is complete, the Company Administrator can request the app with Fiserv APIs be moved to production.

Each App created generates a unique security keys specifically for the sandbox. A sandbox digital certificate is required for web apps and is available for download with the Company Apps section.

Any app created within the My Apps tab will not be made available to other company developers and cannot be promoted to production. Apps created in My Apps cannot be moved to Company Apps and can only be used with apps in the sandbox environment

**Also see:** [Validate APIs in The Sandbox](?path=/docs/gettingstarted/validate-apis-sandbox)

 
#### Production
Company apps are promoted to production by the **Company Administrator** and after the completion and approval of the Fiserv implementation process. After the apps are officially deployed in production, a production-related X.509 digital certificate is made available, and API secret keys are available in the portal.

 

#### API Versioning
Card Developer APIs currently use the URL path to point to the API version.
