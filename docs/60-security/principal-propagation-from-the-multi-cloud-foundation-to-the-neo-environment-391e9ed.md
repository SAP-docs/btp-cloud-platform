<!-- loio391e9ed92ff448e0b4bacac69f853516 -->

# Principal Propagation from the Multi-Cloud Foundation to the Neo Environment

Enable an application in your multi-environment subaccount \(for the multi-cloud foundation\) to access an OAuth-protected application in a subaccount in the Neo environment without user login \(and user interaction\) in the second application. For this scenario to work, the two subaccounts need to be in mutual trust, and in trust with the same identity provider. The first application will propagate its logged-in user to the second application using an OAuth2SAMLBearer destination.



The graphic below illustrates the overall setup of the scenario.

![](images/Principal_Propagation_from_CF_to_Neo_4df21ce.png)



<a name="loio391e9ed92ff448e0b4bacac69f853516__prereq"/>

## Prerequisites

-   You have a user account with *Administrator* role in both SAP BTP subaccounts. See [Managing Member Authorizations in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/a1ab5c4cc117455392cd0a512c7f890d.html "SAP BTP includes predefined platform roles that support the typical tasks performed by users when interacting with the platform. In addition, subaccount administrators can combine various scopes into a custom platform role that addresses their individual requirements.") :arrow_upper_right:.

-   You have a *custom* local service provider configuration \(this means in *cloud cockpit* \> *Security* \> *Trust* \> *Local Service Provider* \> ** you have chosen *Configuration Type* \> *Custom*\) in your subaccount in the Neo environment. See [Configure the Local Service Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/dc618538d97610148155d97dcd123c24.html#loiodcdfe339f94947bc96508daa686cc56d "Your SAP BTP subaccount is the local service provider in the SAML communication. Configure signing keys, certificates, and other trust settings.") :arrow_upper_right:.
-   Both accounts have a trust configuration to the same identity provider. See:
    -   [Configure Trust to the SAML Identity Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/dc618538d97610148155d97dcd123c24.html#loiob6cfc4bb4bff4ace90afc71b0962fcb5 "") :arrow_upper_right: \(for the Neo environment\)
    -   [Establish Trust with Any SAML 2.0 Identity Provider in a Subaccount](../50-administration-and-ops/establish-trust-and-federation-with-uaa-using-any-saml-identity-provider-2ce3938.md#loio8a213ea1a8664e6b96c0593e71339e0e) \(for the multi-cloud foundation\)

-   The application in the Neo environment is protected using OAuth 2.0. See [OAuth 2.0 Service](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/e526ca3998954d62833ffd5a19ec4523.html "Use OAuth 2.0 service on SAP BTP to protect applications in the Neo environment using the OAuth 2.0 protocol.") :arrow_upper_right:.
-   The application in the multi-environment subaccount is bound to an instance of the following services:
    -   *Destination Service*. See [Create and Bind a Destination Service Instance](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/9fdad3cad92e4b63b73d5772014b380e.html).
    -   *xsuaa*

-   You have deployed both applications, each in the corresponding subaccount.

> ### Note:  
> All configuration steps described in this tutorial are done using the cloud cockpit.



<a name="loio391e9ed92ff448e0b4bacac69f853516__section_tbq_kzx_rcb"/>

## Contents

-   [Create Trust Between the Subaccounts](principal-propagation-from-the-multi-cloud-foundation-to-the-neo-environment-391e9ed.md#loio5ff035ce421c4d6c80f0cff028c7df1a)
-   [Create an OAuth Client](principal-propagation-from-the-multi-cloud-foundation-to-the-neo-environment-391e9ed.md#loiofb9a98644f674d7481e179f97ae26c72)
-   [Create a Destination](principal-propagation-from-the-multi-cloud-foundation-to-the-neo-environment-391e9ed.md#loio3b8d026b714240ff89ae73cf250af799)

<a name="loio5ff035ce421c4d6c80f0cff028c7df1a"/>

<!-- loio5ff035ce421c4d6c80f0cff028c7df1a -->

## Create Trust Between the Subaccounts

Exchange keys and certificates between the subaccounts, and configure trust between them. This will enable the subaccounts to communicate using HTTP destinations.



## Procedure

1.  In the cloud cockpit, log on with the Administrator user.

2.  Save locally the identifying X509 certificate of the subaccount in the Cloud Foundry environment.

    1.  In SAP BTP cockpit, navigate to the subaccount in the Cloud Foundry environment.

    2.  Navigate to *Connectivity* \> *Destinations*.

    3.  Choose *Download Trust* and save the X509 certificate identifying this subaccount.


3.  In the subaccount in the Neo environment, create trust to the subaccount in the Cloud Foundry environment.

    1.  Navigate to the subaccount in the Neo environment.

    2.  Navigate to *Security* \> *Trust* \> *Application Identity Provider*.

    3.  Choose *Add Trusted Identity Provider* and configure the new trust configuration settings:

        -   In the *Name* field, enter the following:

            `<your Cloud Foundry domain host>/<Cloud Foundry subaccount ID>`

            > ### Tip:  
            > You can view the **Cloud Foundry domain host** in *cockpit* \> *<your global account\>* \> *<your subaccount\>* \> *<your space\>* \> *Routes*.

            ![](images/CF_Domain_8747d4c.png)

            > ### Tip:  
            > You can view the **subaccount ID** in *cockpit* \> *<your global account\>* \> *<your subaccount\>* \> *Overview*.

            ![](images/CF_Subaccount_Overview_396929b.png)

        -   In the *Signing Certificate* field, enter the X509 certificate of the Cloud Foundry account.

            > ### Note:  
            > Make sure you remove the `BEGIN CERTIFICATE` and `END CERTIFICATE` parts.

        -   Mark the *Only for IDP-initiated SSO* option.

    4.  Save the new trust configuration.



<a name="loiofb9a98644f674d7481e179f97ae26c72"/>

<!-- loiofb9a98644f674d7481e179f97ae26c72 -->

## Create an OAuth Client

You need an OAuth client to get an access token for the OAuth-protected resources in the application in the Neo environment.



<a name="loiofb9a98644f674d7481e179f97ae26c72__context_mlr_kfn_fsb"/>

## Context

For more information about working with OAuth clients, see [Create an OAuth Client](principal-propagation-from-the-multi-cloud-foundation-to-the-neo-environment-391e9ed.md#loiofb9a98644f674d7481e179f97ae26c72).



## Procedure

1.  In the cockpit, navigate to the subaccount in the Neo environment.

2.  Navigate to *Security* \> *OAuth* \> *Clients*, and choose *Register New Client*.

3.  Create an OAuth client with the following configuration settings:

    -   *Name* - the OAuth client name. You will need to provide this name as value of the *Token Service User* property of the destination below.
    -   *Authorization Grant* - choose the *Authorization Code* option.
    -   Mark the *Confidential* option, and provide a secret \(password\).

4.  Save the client.

    > ### Note:  
    > When creating the required **OAuthSAMLBearer destination** later, you will need the following information from the OAuth client:
    > 
    > -   *ID*
    > -   *Secret*


<a name="loio3b8d026b714240ff89ae73cf250af799"/>

<!-- loio3b8d026b714240ff89ae73cf250af799 -->

## Create a Destination



<a name="loio3b8d026b714240ff89ae73cf250af799__context_d1h_yyv_m1b"/>

## Context

Connect the two subaccounts by describing the connection properties in a destination. For more information, see [Modeling Destinations](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/37bddb411fa9496d9db9699371c99138.html "You can connect your applications to another source by describing the source connection properties in a destination. Later on, you can access that destination from your application.") :arrow_upper_right:.



<a name="loio3b8d026b714240ff89ae73cf250af799__steps_xlw_tjx_rcb"/>

## Procedure

1.  Choose the subaccount in the Cloud Foundry environment, and navigate to *Connectivity* \> *Destinations*.

2.  Choose *New Destination*.

3.  In the new destination, provide the following information:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Name
    
    </td>
    <td valign="top">
    
    Technical name of the destination. It can be used later on to get an instance of that destination. It must be unique for the global account.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Description
    
    </td>
    <td valign="top">
    
    Free-text description.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Type
    
    </td>
    <td valign="top">
    
    HTTP
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    URL
    
    </td>
    <td valign="top">
    
    The URL of the protected resource in the Neo environment.

    Example: `https://myneoapp.hana.ondemand.com/myprotectedresource/`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Authentication
    
    </td>
    <td valign="top">
    
    OAuth2SAMLBearerAssertion
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Proxy Type
    
    </td>
    <td valign="top">
    
    Internet
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Audience
    
    </td>
    <td valign="top">
    
    The value of the local service provider name in the subaccount in the Neo environment.

    Copy the value from *cockpit* \> *<your Neo subaccount\>* \> *Security* \> *Trust* \> *Local Service Provider* \> *Local Service Provider Name*.

    ![](images/NeoLocalProvider_7f8b61b.png)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Client Key
    
    </td>
    <td valign="top">
    
    The ID of the OAuth client for the application in the Neo environment.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service URL
    
    </td>
    <td valign="top">
    
    Copy the value of *Token Endpoint* from the following place: *cockpit* \> *<your Neo subaccount\>* \> *Security* \> *OAuth* \> *Branding*.

    ![](images/OAuthTokenEndpoint_b08846c.png)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service User
    
    </td>
    <td valign="top">
    
    The ID of the OAuth client for the application in the Neo environment.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service Password
    
    </td>
    <td valign="top">
    
    The secret from the OAuth client.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    System User
    
    </td>
    <td valign="top">
    
    Empty.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    authnContextClassRef
    
    </td>
    <td valign="top">
    
    *urn:oasis:names:tc:SAML:2.0:ac:classes:PreviousSession* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    nameIdFormat
    
    </td>
    <td valign="top">
    
    *urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified* if the user ID will be propagated to the Neo application or *nameIdFormat = urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress* if the user email will be propagated to the Neo application.
    
    </td>
    </tr>
    </table>
    
    ![](images/CFtoNeoDestination_7c9ac1d.png)

4.  Save the changes.


