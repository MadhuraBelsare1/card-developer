# Before You Start
### Developer Studio for Card Developers
A company of any type or size can offer company-branded digital applications that embed the range of services and capabilities presented by Fiserv using the Fiserv APIs.  The end user customer can create, update, and control the financial services provided by Fiserv, but the user experience belongs to your company.  It is your application powered by Fiserv.


Clients can use APIs to interact with Fiserv products. Communication is supported between two trusted endpoints. In this document, the following terms are defined as:

* **Server** - One or more endpoint Servers residing at Fiserv datacenters.  These servers integrate with the financial back-end and transaction authorization systems.

* **Client** - An application built by any registered company, such as Digital Providers, Account Processors, Application Service Providers (ASP) or a Financial Institution.

Two-way communication employs mutually authenticated HTTPS traffic for transport security.  Clients must also obtain time-limited tokens to make requests.

The Developer Studio for Card Developers, also known as the Card Developer Workspace, provides the information you need to use the Fiserv APIs, consult the interactive "API explorer" section in the left navigation pane to access deep technical information for each API. Also, Card Developer Workspace is used to manage the Fiserv API Keys/Credentials you which to acquire for your Company's App.

* **Create Account** - Clients create the necessary credentials on Developer Studio. This is the initial step in the process. These credentials are used to log into Developer Studio create a Workspace.

* **Create Workspace** - Clients create Card Developer workspace (please note that Developer Studio provides other workspace types for other purposes). The Card Developer workspace contains the API Keys/Credentials of the Client's company. A Sandbox API key is created automatically upon the workspace creation.

* **Add API Keys** - Clients add API Keys to the workspace. The API Key and Secret, used to obtain an access token, are viewable upon creation. Please note that API Keys for Fiserv Certification or Production environment needs to be approved. Also, Clients need to register with Fiserv before gaining the ability to create API Keys for Fiserv Certification or Production environment. Please see [Registration](https://qa-developer.fiserv.com/product/CardDeveloper/docs/?path=docs/gettingstarted/registration.md&branch=develop)


Clients of the Fiserv Portal can establish two roles, with differing capabilities.  These are as follows.

* **Company Administrator** - Designated organization representative with all administrative privileges to manage company assets, invite company developers and also designate secondary company administrator. A client establishes the Administrator when registering with Fiserv.  The Administrator promotes, demotes or deletes all Company Apps.  Also see: [Company Administrator](https://card-dit1-dsp.apimz.onefiserv.net:8079/all-products/getting-started/carddeveloperportal#:~:text=Apps.%C2%A0%20Also%20see%3A-,Company%20Administrator,-Company%20Developer%C2%A0)

* **Company Developer** - Once approved, a Developer can create new apps, visible at first only to the defeloper as My Apps.  The Developer can test these apps in the Sandbox environment at any time.  When ready, the Developer asks the Administrator to promote the app first to Company apps, and then to Production.  Developers also get access to the Company Apps. Also see: [Company Developer](https://card-dit1-dsp.apimz.onefiserv.net:8079/documentation/api-portal-card-developers/company-developer)


The Portal is not a server endpoint and apps cannot be staged or tested directly on the Portal. Developers must use an independent method, such as Curl or Postman, pointed at the Sandbox or Production endpoints to test apps.


## Validation Environment
The sandbox environment is the developer external testing ground. Clients can mimic the production environment and create simulated responses based on test cases and data from Fiserv. The sandbox environment is identical to production but points to a simulated API environment for API responses.

**ALSO SEE:** [Environments](https://card-dit1-dsp.apimz.onefiserv.net:8079/documentation/api-portal-card-developers/environments-0)


#### Note to API Developers

The Portal is also where clients register, create and manage their applications.  You can do the following, here at the Portal.

To set up an account on Fiserv Developer Studio, follow the steps below:
1.	From the top-right corner of the screen, click **Create Account**
2.	Populate the required fields and click **Next**
3.	Follow the instructions on the screen to set up your account based on integration requirements
4.	Sign on to your Fiserv Developer Studio account once it is activated


After successful registration, following credentials are sent via email:
- API Key
- Username/Password
- OrgId 
- AppId
- VendorId 
- ChannelId

Some of these credentials are required to send as header parameters under the EFXHeader parameter. For more information, refer to the <a href="?path=docs/api-ref-EFX-header.md" target="_blank" title="Click to open" >EFXHeader</a> section.

## Know Our Standard API structure 

This section describes a standard structure of request and response message of Banking Hub RESTful APIs. 

### Request Message

All API requests must contain the following components:

*	API Method: POST or PUT
*   Host URL:  https://{_url_}/v{_version_}/
*	Request Header
*	Request Body

For every API request, a response message is obtained that contains a response payload and status of the API request.
#### Request Header
Header parameters are common for all API requests of Banking Hub APIs. Header parameters are sent as a JSON object under EFXHeader header parameter.

For more information on EFXHeader and to view the list of all header parameters, <a href="?path=docs/api-ref-EFX-header.md" title="Click to view the list of EFX header parameters" > click here.</a>

Sample Header Example:
```
"EFXHeader": {
    "OrganizationId": "CTOrg",
    "TrnId": "f262cfa4-9da4-4a10-b48c-2e947ce3e66c",
    "VendorId": "112233",
    "Context": {
      "Channel": "WEB"
    }
    }
```

#### Request Body
Request body of an API that changes based on the type of transaction being processed. Request body contains the detailed information that is required to perform a particular transaction.

**Request Payload:** 

Following example shows the sample request payload for Get Account Hold API request.

```
{
  "AcctHoldSel": {
    "AcctHoldKeys": [
      {
        "AcctKeys": {
          "AcctId": "string",
          "AcctType": "string"
        },
        "AcctHoldIdent": "string"
      }
    ],
    "AcctKeys": [
      {
        "AcctId": "string",
        "AcctType": "string"
      }
    ]
  }
}
```


### Response Message


Upon a successful API request, a response payload is received. The response payload contains the status and the returned details of the requested API in key-value pairs. The default response format is JSON (JavaScript Object Notation). 


**Response Payload:**

Following example shows the sample response payload for **Get Account Hold** API request.

```
{
  "Status": {
    "Id": "string",
    "StatusCode": "string",
    "StatusDesc": "string",
    "Severity": "string",
    "SvcProviderName": "string",
    "ServerStatusCode": "string",
    "ServerStatusDesc": "string",
    "OvrdExceptionInd": true,
    "SubjectRole": "string",
    "SubjectElement": [
      {
        "Path": "string",
        "ServerPath": "string",
        "Value": "string"
      }
    ],
    "ContentHTML": "string",
    "AdditionalStatus": [
      {
        "StatusCode": "string",
        "StatusDesc": "string",
        "Severity": "string",
        "SvcProviderName": "string",
        "ServerStatusCode": "string",
        "ServerStatusDesc": "string",
        "OvrdExceptionInd": true,
        "SubjectElement": [
          {
            "Path": "string",
            "ServerPath": "string",
            "Value": "string"
          }
        ]
      }
    ]
  },
  "RecCtrlOut": {
    "SentRecCount": 0
  },
  "AcctHoldRec": [
    {
      "AcctHoldKeys": {
        "AcctKeys": {
          "AcctId": "string",
          "AcctType": "string"
        },
        "AcctHoldIdent": "string"
      },
      "AcctHoldInfo": {
        "AcctRef": {
          "AcctKeys": {
            "AcctId": "string",
            "AcctType": "string"
          }
        },
        "CurAmt": {
          "Amt": 0,
          "CurCode": {
            "CurCodeType": "string",
            "CurCodeValue": "string"
          }
        },
        "RelationshipMgr": [
          {
            "RelationshipMgrIdent": "string",
            "RelationshipRole": "string"
          }
        ],
        "ReportGroupCode": "string",
        "SecuredAcctRef": {
          "AcctKeys": {
            "AcctId": "string",
            "AcctType": "string"
          }
        },
        "MaxPledgeAmt": {
          "Amt": 0,
          "CurCode": {
            "CurCodeType": "string",
            "CurCodeValue": "string"
          }
        },
        "HoldReason": [],
        "ExpDt": "string",
        "EffDt": "string",
        "AcctHoldOption": "string",
        "AcctHoldIdent": "string",
        "PendingHoldAmt": {
          "Amt": 0,
          "CurCode": {
            "CurCodeType": "string",
            "CurCodeValue": "string"
          }
        },
        "PendingHoldDt": "string"
      },
      "AcctHoldStatus": {
        "AcctHoldStatusCode": "string",
        "EffDt": "string"
      }
    }
  ]
}
```

To view the API documentation of **Get Account Hold** API in API Explorer, [click here.](../api/?type=post&path=/accountHolds/secured)
   
