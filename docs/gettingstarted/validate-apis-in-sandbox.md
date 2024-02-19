### Validate APIs in the Sandbox
The following steps must be completed prior to generating an API call from the Company App in the sandbox environment as the process for testing APIs requires access to API Key. 

  * **Automatically created API Keys -** A Sandbox API Key is created automatically upon the Workspace creation. The automatically created Sandbox API Key is visible only to the Workspace Creator, also known as the Workspace Owner, until other Company Developers are invited to the Card Developer Workspace.
  * **Manually created API Keys -** The Company Administrator can manually create one or more Sandbox API Keys in the Card Developer Workspace for each integration project or Company App. The manually created Sandbox API Keys are also visible to all the Company Developers invited to the Card Developer Workspace.


  
#### Validate an API:
![](assets/images/exclaimation.png)    Important! 

  *  The Sandbox APIs *emulate* the behavior of production APIs and support only *pre-defined* request and response data. 
  *  You must only use the test case requests documented in the **Sandbox** section for each API domain (Please refer to left navigation pane). Any other requests will result in an error.
  *  The Sandbox test requests may include optional fields not necessarily used in production. You must use exactly the requests given in the test case.
 

![](assets/images/validate-note-1.png)

 

**Step 1** Navigate to **Credentials** tab in the Developer Studio Workspace. Locate the API Key created for the Company App by the Company Administrator 

  *  CLick the **View** button to dispaly and retrieve the API key data and Secret. The API key data and Secret are used to generate an access token.
  *  From View screen also note what APIs are included for validation.
    
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


