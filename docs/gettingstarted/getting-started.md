# Overview
This document is an introduction and quick access, how-to guide when learning to use the Fiserv Developer Studio©: Card Developer©. Companies can use the Fiserv Card Developer API solutions for company-branded digital applications to embed services and capabilities for their customers. You can create, update, and control the financial services provided by Fiserv APIs for your clients under your company branding.


* [New client information](?path=/docs/gettingstarted/getting-started-when-new.md)
* [Exisiting client information](?path=/docs/gettingstarted/getting-started-when-migerating.md)


## Developer Studio Highlights
Card Developer includes the following features:
*	Create Account—Used to create an account, in the Card Developer Workspace. Located in the top menu area prior to signing into Studio Developer.
*	API explorer—An interactive research tools for technical information, key management, and credentials. Located in the lower half of the left-side panel.
*	Create Workspace—Clients create Card Developer Workspace(s). The Card Developer Workspace contains the API keys/Credentials of the Client's company. You can create more workspace types for other purposes.
*	Add API Keys—Clients add API keys to the workspace. The API key and Secret are used to obtain an access token. You must register with Fiserv as a client before you can create API keys for Production environment. Then you must get the API keys approved for Fiserv Production environment. See also, New clients.
  
*Note: We used to refer to the previous API Card Developer portal simply as “app”.*

The following graphics show you a visual representation the highlights outlined above. 

![](assets/images/getStarted/CardDev-top.png)

![](assets/images/getStarted/Add-an-API-key-button.png)

In the Card Developer Workspace, Clients can establish two roles with differing capabilities. The two 
roles are as follows:
**Company Administrator**—The Card Developer Workspace creator is the default Company 
Administrator. The Company Administrator is the designated organization representative with all 
administrative privileges:

* Manage the Card Developer Workspace.
* Invite Company Developers.
* Designate secondary Company Administrators. 
* Delete a Card Developer Workspace.

**Company Developer**—This role type is a subset of the Company Administrators account type with the 
following privileges:

* Can view and use Sandbox API Keys created by Company Administrator
* Get access to the Company Production API Keys created by the Company Administrator.
* Can test API Keys in the Sandbox environment.
* View/read privileges to the Company API products and features.

### Limitations
* The Card Developer Workspace is not a server endpoint and API keys cannot be staged or tested 
directly on the Card Developer Workspace. 
* Developers must use an independent method, such as Curl or Postman, pointed at the Sandbox 
endpoints to test API keys.

### Sandbox environment
The sandbox environment is a safe testing ground that isolates code for developers. Clients can mimic 
the production environment and create simulated responses. The simulated responses are based on test 
cases and data. The sandbox environment is identical to production but points to a simulated API 
environment for API responses.

# Workspace and API keys
This section describes how to set up and use a Card Developer Workspace. 

## New clients
As a new client, you must first create a new account and use those credentials to sign into Developer 
Studio to create a workspace.

### Create a new account
1. In the upper-right corner, select **Create account**.
   
   ![](assets/images/getStarted/Create-account.png)

3. Enter your information in the **Create account pop-up step 1 of 2**.
   
   ![](assets/images/getStarted/Create-account-popup.png)

5. Check your work email and **copy the Temporary password**.
   
   ![](assets/images/getStarted/New-account-email-temp-password.png)
   
7. Paste the Temporary password in the **Create account step 2 of 2** pop-up.
   
   ![](assets/images/getStarted/Create-account-proof.png)

### Create new workspaces
This section assumes that you are continuing from the previous section, **Create a new account**. The 
Developer Studio top page options have updated. See graphic below.

![](assets/images/getStarted/Studio-top-page-options.png)

1 In the upper-right section, select **workspaces**.

[](assets/images/getStarted/workspaces_button.png)

A  pop-up appears.
2. Select **Add** a new workspace. 

![](assets/images/getStarted/workspaces_Add-new-workspace.png)

A pop-up appears

![](assets/images/getStarted/workspaces_create-new-pop-up.png)

*Note: When you create a workspace, the steps are the same whether you are creating a workspace as a 
new or existing Fiserv Client.*

3. Enter your** workspace name** and **description**.
4. From Product choices, select **Card Developer** as **Product**.
5. Review the option selected and click **Create**.
**Congratulations!** Your new workspace is ready to use.
6. (_Optional_) If you want more than one workspace, repeat step 2 through step 4. There is no limit on 
the number of workspaces. 

### Create new API keys
The following steps are for Company Administrators who want to create API keys. 
7. From the Workspaces menu bar, select **Credentials**.
8. Select** Add API key**.

![](assets/images/getStarted/workspace-tab-Credentials+new-content.png)

A pop-up appears.

![](assets/images/getStarted/Add-API-key.png)

9. Select **Sandbox**. 
*Note: During your test period, Sandbox is the only functional option available.*

The following  pop-up appears:

![](assets/images/getStarted/Add-API-key-Name-endpoints.png)

10. Enter your **API key name**.
11. Select the **API features** and **endpoints** you want to test with the Sandbox. 
12. Select **Add Key**.

A success pop-up appears with your information.

![](assets/images/getStarted/API-success-with-coy-options.png)

13. (_Optional_) Use the copy options and paste your keys and Host URL into a text file for later use.
14. Check your work email for the subject line, “Developer Studio from Fiserv - Credentials Added to 
Workspace”. It contains information about your API key and a link to your Developer Studio

## Existing clients
If you have existing API keys and Company Developers, you can migrate your API Keys (apps) to the Card 
Developer Workspace.

##Migrate existing API keys and Company Developers
When the Company Administrator creates a Card Developer Workspace, the Company Administrator 
must use the same email address used previously to create a new account on Developer Studio. 

### Create new account and a workspace
1. In the upper-right corner, select **Create account**.
   
   ![](assets/images/getStarted/Create-account.png)

2. Enter your information in the **Create account pop-up step 1 of 2**.
   
   ![](assets/images/getStarted/Create-account-popup.png)

3. **Check your work email** for your Fiserv Temporary password.
4.  **Copy** the Temporary password.
   
   ![](assets/images/getStarted/New-account-email-temp-password.png)
   
5. Paste the Temporary password in the **Create account step 2 of 2** pop-up.
   
   ![](assets/images/getStarted/Create-account-proof.png)
   
# Appendix
## Card Developer terms

The Fiserv Card Developer API environment defines the following terms as: 

* Trusted endpoints—Fiserv API suites supports communication between two trusted endpoints.
* Server—One or more endpoint Servers residing at Fiserv datacenters. These servers integrate 
with the financial back end. 
* Client—An application built by any registered company, such as Digital Providers, Account 
Processors, Application Service Providers (ASP) or a Financial Institution. 
* Two-way communication—Mutually authenticated HTTPS traffic for transport security. Clients 
must obtain time-limited tokens to make requests. 
* Card Developer Workspace—Fiserv’s previous API Card Developer portal concept terminology 
was referred to as “Company”.

## Workspace highlights

The following images highlight Company Administrator common requests and actions.
Review and create the Card Developer Workspace
Once you set up and are working in a Workspace mode, Workspace page contains the following tabs:

* Summary
* Credentials
* Members
* Settings
