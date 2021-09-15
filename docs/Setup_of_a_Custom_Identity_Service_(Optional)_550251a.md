<!-- loio550251abaf49432bbaa65147b65a1f39 -->

# Setup of a Custom Identity Service \(Optional\)

Optionally, you can set up a custom identity service as an alternative to SAP ID, which is the default identity provider of SAP BTP.

The default platform identity provider and application identity provider of SAP BTP is SAP ID service. Trust to SAP ID service in your subaccount is pre-configured in the Neo and the Cloud Foundry environments by default, so you can start using it without further configuration. Optionally, you can add additional trust settings or set the default trust to inactive, for example, if you prefer to use another identity provider.

Setup of a custom identity service is optional, but you must set it up to ease sign on of your developers if they want to use SAP Web IDE as a UI development tool. If your developers want to work with SAP Business Application Studio, you can use SAP ID service as identity provider or, optionally, a custom identity provider.

We describe a custom trust configuration using the example of SAP Cloud Identity Services - Identity Authentication. The Identity Authentication service is a cloud solution for identity lifecycle management for SAP BTP applications. You can set up SAP BTP as a service provider, and Identity Authentication service as an identity provider. For the integration, you must set the trust on both sides. For more information about the Identity Authentication service, see [Overview](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html) and [Initial Setup](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/31af7da133874e199a7df1d42905241b.html).

-   **[Establish Trust Automatically](Establish_Trust_Automatically_b9f4b0d.md "If you want to use a custom identity provider instead of the SAP ID service, you must set up trust between the Cloud Foundry account
		and the Identity Authentication service.")**  
If you want to use a custom identity provider instead of the SAP ID service, you must set up trust between the Cloud Foundry account and the Identity Authentication service.
-   **[Manual Trust Setup \(Optional\)](Manual_Trust_Setup_(Optional)_36214a9.md "If you want to use Identity Authentication service as custom identity provider, you need to set up trust between the Cloud Foundry account
		and the Identity Authentication service.")**  
If you want to use Identity Authentication service as custom identity provider, you need to set up trust between the Cloud Foundry account and the Identity Authentication service.
-   **[Creating Identity Provider Users and Groups](Creating_Identity_Provider_Users_and_Groups_a9bd926.md "You create identity provider users and groups in the Identity Authentication service.")**  
You create identity provider users and groups in the Identity Authentication service.

