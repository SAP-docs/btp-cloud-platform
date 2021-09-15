<!-- loiob9f4b0dc967040c99c7c8268ce335cce -->

# Establish Trust Automatically

If you want to use a custom identity provider instead of the SAP ID service, you must set up trust between the Cloud Foundry account and the Identity Authentication service.



## Context

SAP ID service is the default identity provider for SAP BTP. If you have custom identity provider, you can use a function in SAP BTP cockpit to set up trust between your subaccount and the Identity Authentication service for SAP BTP automatically. The trust configuration is of type *OpenID Connect* . If you want to use SAML 2.0 instead, set up trust manually \(see [Manual Trust Setup \(Optional\)](Manual_Trust_Setup_(Optional)_36214a9.md)\).



## Procedure

1.  In the SAP BTP cockpit, go to the Cloud Foundry subaccount for your ABAP system.

2.  From the navigation area, choose *Security* \> *Trust Configuration*.

3.  Choose *Establish Trust*.

4.  In the following popup, select a identity provider from the dropdown list.

    Only identity providers that are associated with your customer ID are shown.

5.  Choose *Establish Trust*.

    Trust of type *OpenID Connect* between your subaccount and the identity provider is generated.

6.  Log on to the Identity Authentication service.

7.  From the navigation area, choose *Applications & Resources* \> *Applications*.

8.  Search for the application that has been created as part of the trust setup.

    The name of the application has the format *XSUAA\_*<Subaccount Name\>**, but you can change it if needed.

9.  Verify that the subject name identifier is set to *E-Mail*.


