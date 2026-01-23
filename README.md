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


WORK IN PROGRESS - MORE INSTRUCTIONS COMING SOON