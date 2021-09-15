<!-- loio7c6aa87459764b179aeccadccd4f91f3 -->

# Manually Establish Trust and Federation Between UAA and Identity Authentication

Use your SAP Cloud Identity Services - Identity Authentication tenant as an identity provider or a proxy to your own identity provider hosting your business users. Exchange SAML metadata to establish trust with the Identity Authentication tenant and then register your subaccount with the tenant. To complete federation, maintain the federation attributes of the user groups.



<a name="loio7c6aa87459764b179aeccadccd4f91f3__context_rjk_cgw_xmb"/>

## Context

> ### Note:  
> Instead of manually exchanging SAML metadata, we recommend that you use the automatic method based on the OpenID Connect \(OIDC\) protocol.
> 
> For more information, see [Establish Trust and Federation Between UAA and Identity Authentication](Establish_Trust_and_Federation_Between_UAA_and_Identity_Authentication_161f8f0.md#loio161f8f0cfac64c4fa2d973bc5f08a894).

 <a name="loio7c6aa87459764b179aeccadccd4f91f3 loioaedb8eed952b41c4b87c50b92bf651e4__loioaedb8eed952b41c4b87c50b92bf651e4"/>

<!-- loioaedb8eed952b41c4b87c50b92bf651e4 -->

# Establish Trust with an SAML 2.0 Identity Provider in a Subaccount

You want to use an SAML 2.0 identity provider, for example, SAP Cloud Identity Services - Identity Authentication. This is where the business users for SAP BTP are stored.



<a name="loioaedb8eed952b41c4b87c50b92bf651e4__prereq_dvg_xgj_p1b"/>

## Prerequisites

-   You have subaccount administrator permissionsor you are a security administrator \(cloud management tools feature set A\) of this account. For more information, see the related link.

-   You have downloaded the SAML 2.0 metadata file from the SAP Cloud Identity Services - Identity Authentication using the URL `https://<Identity_Authentication_tenant>.accounts.ondemand.com/saml2/metadata`.

    > ### Example:  
    > `https://my-ias-tenant.accounts.ondemand.com/saml2/metadata`

    For more information, see [Tenant SAML 2.0 Configuration in the SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/e81a19b0067f4646982d7200a8dab3ca.html).




## Context

You must establish a trust relationship with an SAML 2.0 identity provider in your subaccount in SAP BTP. The following procedure describes how you establish trust in the SAP Cloud Identity Services - Identity Authentication.



## Procedure

1.  In the SAP BTP cockpit, go to your subaccount\(see [Navigate to Orgs and Spaces](Navigate_to_Orgs_and_Spaces_5bf8735.md)\) and choose *Security* \> *Trust Configuration*.

2.  Choose *New Trust Configuration*.

3.  Enter a name and a description that make it clear that the trust configuration refers to the identity provider.

    > ### Note:  
    > Make sure that the users who are supposed to log on to this identity provider understand the name of the trust configuration.

4.  Download the relevant metadata \(see prerequisites\) and save it in an XML file.

5.  Choose the *Upload* button to insert the SAML 2.0 metadata.

6.  To validate the metadata, choose *Parse*. This will fill the *Subject* and *Issuer* fields with the relevant data from the SAP Cloud Identity Services - Identity Authentication - your SAML 2.0 identity provider.

    The name of the new trust configuration now shows the value `<Identity_Authentication_tenant>.accounts.ondemand.com`. It represents the custom identity provider SAP Cloud Identity Services - Identity Authentication.

    This also fills the fields for the single sign-on URLs and the single logout URLs.

7.  Save your changes.

8.  \(Optional, cloud management tools feature set A\) If you do not need SAP ID service, set it to inactive.

    You have successfully configured trust in the SAP Cloud Identity Services - Identity Authentication, which is your SAML 2.0 identity provider.

9.  To get the SAML metadata of your subaccount, choose the *SAML Metadata* button. You create an XML file with the SAML metadata of your subaccount. Its name is `saml-<subdomain>-sp.xml`. Use this file to import the SAML metadata into your identity provider.


**Related Information**  


[Managing Security Administrators in Your Subaccount \[Feature Set A\]](Managing_Security_Administrators_in_Your_Subaccount_Feature_Set_A_6752c4b.md "Running on the cloud management tools feature set A: When you create a subaccount, SAP BTP automatically grants your user the role for the administration of business users and their authorizations in the subaccount. Having this role, you can also add or remove other users who will then also be user and role administrators of this subaccount.")

 <a name="loio7c6aa87459764b179aeccadccd4f91f3 loio347cc6991eda439ea7d87ef1311913bf__loio347cc6991eda439ea7d87ef1311913bf"/>

<!-- loio347cc6991eda439ea7d87ef1311913bf -->

# Register SAP BTP Subaccount in the SAML 2.0 Identity Provider

An SAML service provider interacts with an SAML 2.0 identity provider to authenticate users signing in by means of a single sign-on \(SSO\) mechanism. In this scenario the User Account and Authentication \(UAA\) service acts as a service provider representing a single subaccount. To establish trust between an identity provider and a subaccount, you must register your subaccount by providing the SAML details for web-based authentication in the identity provider itself. The identity provider we use here is the SAP Cloud Identity Services - Identity Authentication.



## Context

Administrators must configure trust on both sides, in the service provider and in the SAML identity provider. This description covers the side of the identity provider \(SAP Cloud Identity Services - Identity Authentication\). The trust configuration on the side of the SAP Cloud Identity Services - Identity Authentication must contain the following items:

-   Metadata for web-based authentication or the relevant configuration information

    If available, the metadata contains the configuration information, including the signing certificate and the required URLs. You can create the metadata file of your subaccount using the *SAML Metadata* button in *Security* \> *Trust Configuration* of your subaccount.

-   Use e-mail as the unique name ID attribute, and map the user attribute `Groups` to the assertion attribute ***Groups*** \(case-sensitive\). This assertion attribute is required for the assignment of roles.

    This makes sure that there is a trust relationship between the SAP Cloud Identity Services - Identity Authentication and the subaccount.


We illustrate the process of configuring trust in the service provider by describing how administrators use the administration console of Identity Authentication to register the subaccount.

To establish trust from a tenant of SAP Cloud Identity Services - Identity Authentication to a subaccount, assign a metadata file and define attribute details. The SAML 2.0 assertion includes these attributes. With the UAA as SAML 2.0 service provider, they are used for automatic assignment of UAA authorizations based on information maintained in the identity provider.



<a name="loio347cc6991eda439ea7d87ef1311913bf__steps_mwt_fc2_sy"/>

## Procedure

1.  Open the administration console of SAP Cloud Identity Services - Identity Authentication.

    `https://<Identity_Authentication_tenant>.accounts.ondemand.com/admin`

2.  To go to the service provider configuration, choose *Applications & Resources* \> *Applications* in the menu or the *Applications* tile.

    > ### Note:  
    > In the administration console, you find the service providers in *Applications*.

3.  To add a new SAML service provider, create a new application by using the *+ Add* button.

4.  Choose a name for the application that clearly identifies it as your new service provider. Save your changes.

    Users see this name in the logon screen when the authentication is requested by the UAA service. Seeing the name, they know which application they currently access after authentication.

5.  Choose *SAML 2.0 Configuration* and import the relevant metadata XML file. Save your changes.

    > ### Note:  
    > Use the `saml-<subdomain>-sp.xml` metadata file of your subaccount. You can create the file using the *SAML Metadata* button in *Security* \> *Trust Configuration* of your subaccount.

    If the contents of the metadata XML file are valid, the parsing process extracts the information required to populate the remaining fields of the SAML configuration. It provides the name, the URLs of the assertion consumer service and single logout endpoints, and the signing certificate.

6.  Choose *Default Name ID Format* and select *E-Mail* as a unique attribute. Save your changes.

7.  Choose *Assertion Attributes*, use *+Add* to add a multi-value user attribute, and enter ***Groups*** \(case-sensitive\) as assertion attribute name for the *Groups* user attribute. Save your changes.


