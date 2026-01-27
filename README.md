# Amplify Fusion/Engage OAuth 2.0 Client Provisioning For Okta

This Amplify Fusion project contains an integration and associated connector that handle Amplify Engage credential provisioning requests. It enables self-service onboarding for Engage subscribers consuming OAuth 2.0-secured APIs managed by Fusion, allowing them to retrieve their OAuth 2.0 credentials without manual administrator involvement.

The integration leverages Okta's Dynamic Client Registration (DCR) capabilities to automatically create and configure OAuth clients at subscription time.

You should have access to your Okta tenant and you should have Fusion integrated with Engage as described [here](https://docs.axway.com/bundle/amplify_integration/page/docs/manager_module/manage_marketplace/index.html).

You should also validate that you can call your API with Okta OAuth 2.0 from Postman using a manually created Okta test client and that client id is added to a Fusion Test App in Manager.

For testing you can reference these documents:
* [Amplify Integration - Use Okta for OAuth API Authentication](https://gist.github.com/lbrenman/b34f143aa6edca868db74396c7092b48)

Instructions
* [Import](https://docs.axway.com/bundle/amplify_integration/page/docs/manager_module/manage_the_environments/index.html#export-or-import-a-project) the project zip file into your tenant

* [Override](https://docs.axway.com/bundle/amplify_integration/page/docs/designer_module/designer_module_artifacts/connections/index.html#configure-an-override-connection) the Keycloak API connector in Manager and enter the appropriate values for your Okta tenant details and your API Key.

* Link the integration to your Identity Provider in Fusion -> Manager Identity Provider as follows:
  * Open the Credential Provisioning integration, `cred-prov-flow-okta` in the imported project
  * Click the Credential Provision trigger artifact and select your Identity Provider and click Save
    > Note that if you get an error selecting your Identity provider you can delete the Credential Provisioning component and re-add it and then select the Identity provider
  * In Fusion Manager, Open the Identity provider and select the Credential Provisioning integration you just updated in the Link Integration picker and select the desired data plane and click Save

* Now you can select OAuth 2.0 for any of your Fusion APIs and create a Governance Rule that uses the Identity Provider and activate your API

* Since we'll be testing the OAuth 2.0 API from Engage, you'll need to configure CORS properly for your API as shown below:

  ![Imgur](https://i.imgur.com/5VQ8KRQ.png)

* When you activate your API it will be discovered in Engage and you can create product based on it

* When Engage users discover the product and associated API, they can subscribe and register an application. Then when the user requests a credential, the credential provisioning integration will trigger and the credentials sent to Engage for the user to use the OAuth 2.0 Fusion API.

Note that with Okta, the client credentials OAuth flow is not supported from browsers so you will need to retrieve your client_id and client_secret from the Engage credential and use it in Curl or Postman.

You can use the Authorization Code flow (with PKCE) from Engage in the browser.

Instructions [here](https://github.com/lbrenman/Fusion-Keycloak-DCR-for-Engage) are for Keycloak but may be useful until these docs are complete