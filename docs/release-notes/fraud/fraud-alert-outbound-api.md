# Fraud Alert Outbound API
The Alert Notify operation is a vendor hosted operation used for Fiserv to send fraud alerts to the notification vendor when there is potential fraudulent activity.

This API is the initial operation required to perform other Card Risk Mitigation: Fraud Alert operations. You must use your own target host endpoints for testing.

To test the API, take these steps.

If you do not receive the Sandbox alert, verify if you have the required Fiserv Root CA and Intermediate CA certificates placed in the server trust-store. The Root CA and Intermediate CA certificates can be downloaded from the Keys tab of the developer application from the Card Developer portal.

1. Log in to the Cards API Portal.
2. Select **Approvals** > **Company Apps**. The list of existing company applications already subscribed displays.
3. Select the **Add App** + button. The Add Company App page displays.

![](assets/images/add-company-app-page.png)

4. Enter this required information:
   
 * **App Name**—Name of the application.
   
 * **App Type**—Type of the application.
   
5. Select the check box for Sandbox Card Risk Mitigation: Fraud Alert API. The Fraud Alert API - additional fields section displays.

![](assets/images/fraud-alert-api-additional-fields-section.png)

6. Enter these details:

 * **Hostname** or **IP address**—Hostname or IP address where the outbound fraud alert API from Fiserv is to be pushed. Only HTTPS protocol is supported.
   
 * **Port**—Enter port number.
   
 * **URI**—Enter the resource path.
   
 * **Endpoint URL**—Based on the above information, the Endpoint URL to receive test Fraud Alerts from Fiserv is configured.
   
7. Select **Test**. The following Sandbox alert is pushed from Fiserv to the endpoints configured in step 6.

8. Select **Create App**. The application details are saved along with specific security keys and listed under Company Apps.
 
9. Set up the required response for the alert notification service. You can download the Outboud OpenAPI specification file (YAML) format available on the portal to review the URLs, structure, and data definitions.
10. Go to **Approvals** >**Company Apps** to begin the process of moving to production. The list of products display.
11. Select the Fraud Alert APIs that are tested, validated and ready for production from the Products list. The API Key and Secret key details along with the digital certificates required for authorization display under the Keys tab.

![](assets/images/api-key-and-secretkey-details.png)

12. Select the Edit tab to edit the endpoint details, if required.
13. Select the Promote to Production tab. The Promote Company App page displays.

![](assets/images/promote-company-app-page.png)

14. Select the **Card Risk Mitigation**: **Fraud Alert API** check box. The **Fraud Alert API - additional fields** section displays.
15. Enter these production details:
    
 * **Hostname** or **IP address**—Hostname or IP address where the outbound fraud alert API from Fiserv is to be pushed. Only HTTPS protocol is supported.
  
 * **Port**—Enter port number.
  
 * **URI**—Enter the resource path.
   
 * **Endpoint URL**—Based on the above information, the Endpoint where you will receive the production Fraud Alerts from Fiserv is configured and sent to Fiserv.
   
16. Read and check the agreement boxes to accept the terms and conditions.
17. Select **Create App**. The server endpoints set for production are sent to Fiserv for approval and further processing.
    
When the promote to production process is complete, an email is released to your Company Administrator with a link to download the production digital certificate. A production version of the app (with approved APIs) is listed on the Company Apps page with production keys. Ensure
all developers working with the app have access to the production certificate.
