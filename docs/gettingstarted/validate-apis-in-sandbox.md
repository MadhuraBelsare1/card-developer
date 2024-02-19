### Validate APIs in the Sandbox
The following steps must be completed prior to generating an API call in the sandbox environment as the process for testing APIs requires access to API Key. 

  *  **Company API Keys** created by the Company Administrator are **accessible** by invited Company Developers.
  *  **Personal API Key** created automatically upon the Workspace creation is **accessible** only by the Workspace Creator (also known as the Workspace Owner).

#### Validate an API:
![](assets/images/exclaimation.png)    Important! 

  *  The Sandbox APIs *emulate* the behavior of production APIs and support only *pre-defined* request and response data. 
  *  You must only use the test case requests documented in the API Developer Portal **Sandbox doc** for each domain. Any other requests will result in an error.
  *  The Sandbox test requests may include optional fields not necessarily used in production. You must use exactly the requests given in the test case documents.
 

![](assets/images/validate-note-1.png)

 

**Step 1** Navigate to **Company App** tab in the portal. Select the specific company app created by the Company Administrator

  *  Once you select the app, you are able to retrieve the API key and Secret key. The keys are used to generate an access token.
  *  From the Details tab, determine what APIs are included for validation.
**Step 2** Navigate to the portal **APIs** tab. This contains a catalog of available APIs

  *  Select an API product from the list.
     *  Download the OpenAPI specification file (YAML) format to review the URLs, structure, and data definitions.
**Step 3** Navigate to the relative **API Docs** menu.

In this sections users can: 

  *  Download the **OpenAPI specification file (YAML)** format to review the URLs, structure, and data definitions.
  *  From the **Sandbox page**, view the API test cases and error handling.
Ex.

![](assets/images/validate-1.png)

 

**Step 4** Generate an [Access Token](?path=/docs/gettingstarted/access-tokens.md) for the sandbox. Once logged in, Company Admins have access to portal pages through the navigation menu explaining how to generate a token.

**Step 5** Include these required headers in all requests to the Sandbox. The value of the Authorization token varies. The value of the x-fapi-financial-id header is always '12345678' for the Sandbox.

  *  Authorization: Bearer --access token--
  *  x-fapi-financial-id: 12345678

**Step 6** Generate an API call into the **Sandbox Environment**.

 ![](assets/images/validate-note-2.png)


