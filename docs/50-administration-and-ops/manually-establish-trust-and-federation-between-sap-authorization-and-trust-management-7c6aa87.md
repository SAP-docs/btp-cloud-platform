<!-- loio7c6aa87459764b179aeccadccd4f91f3 -->

# Manually Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services

Use your SAP Cloud Identity Services tenant as an identity provider or a proxy to your own identity provider hosting your business users. Exchange SAML metadata to establish trust with the SAP Cloud Identity Services tenant and then register your subaccount with the tenant. To complete federation, maintain the federation attributes of the user groups.



<a name="loio7c6aa87459764b179aeccadccd4f91f3__context_rjk_cgw_xmb"/>

## Context

> ### Note:  
> Instead of manually exchanging SAML metadata, we recommend that you use the automatic method based on the OpenID Connect \(OIDC\) protocol.
> 
> For more information, see [Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](establish-trust-and-federation-between-sap-authorization-and-trust-management-service-a-161f8f0.md).

<a name="loioaedb8eed952b41c4b87c50b92bf651e4"/>

<!-- loioaedb8eed952b41c4b87c50b92bf651e4 -->

## Establish Trust with an SAML 2.0 Identity Provider in a Subaccount

You want to use an SAML 2.0 identity provider, for example, SAP Cloud Identity Services. The identity provider authenticates business users for SAP BTP.



<a name="loioaedb8eed952b41c4b87c50b92bf651e4__prereq_dvg_xgj_p1b"/>

## Prerequisites

-   You have subaccount administrator permissions.

-   You have downloaded the SAML 2.0 metadata file from the SAP Cloud Identity Services tenant using the URL <code>https://<i class="varname">&lt;sap_cloud_identity_services_tenant&gt;</i>.accounts.ondemand.com/saml2/metadata</code>.

    > ### Example:  
    > `https://my-ias-tenant.accounts.ondemand.com/saml2/metadata`

    For more information, see [Tenant SAML 2.0 Configuration in the SAP Cloud Identity Services](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/e81a19b0067f4646982d7200a8dab3ca.html).




## Context

The following procedure describes how to establish trust with an SAP Cloud Identity Services tenant.

> ### Restriction:  
> You've already created a trust configuration with a custom identity provider for applications. In this case, you can't add a trust configuration with the same SAP Cloud Identity Services tenant using another protocol.
> 
> > ### Example:  
> > If there's already a trust configuration with OpenID Connect, you can't create one using the SAML protocol.

> ### Restriction:  
> Consider the upper limits for trust configurations in the subaccount. See [Limits for the Subaccount](../60-security/limits-for-technical-artifacts-of-the-sap-authorization-and-trust-management-service-6d3ef52.md#loio6d3ef5260f4a4232ad43542ab1441694__section_ddk_bhf_fzb).

> ### Restriction:  
> We recommend a single trust configuration per subaccount with SAP Cloud Identity Services using the OpenID Connect \(OIDC\) protocol. If this isn't sufficient, you may use a trust configuration with SAML 2.0.
> 
> Nevertheless, we recommend migrating existing SAML 2.0 trusts according to the documentation [Migration from SAML Trust to OpenID Connect Trust with SAP Cloud Identity Services](migration-from-saml-trust-to-openid-connect-trust-with-sap-cloud-identity-services-d097ce2.md).



## Procedure

1.  In the SAP BTP cockpit, go to your subaccount\(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration*.

2.  Choose *New SAML Trust Configuration*.

3.  Enter a name and a description that make it clear to which identity provider that the trust configuration refers.

    > ### Note:  
    > Make sure that the users who are supposed to log on to this identity provider understand the name of the trust configuration.

4.  Download the relevant metadata \(see prerequisites\) and save it in an XML file.

5.  Choose the *Upload* button to insert the SAML 2.0 metadata.

6.  To validate the metadata, choose *Parse*. The system fills the *Subject* and *Issuer* fields with the relevant data from the SAP Cloud Identity Services - your SAML 2.0 identity provider. You see the fields when you choose *Show Details*.

    The name of the new trust configuration now shows the value <code><i class="varname">&lt;sap_cloud_identity_services_tenant&gt;</i>.accounts.ondemand.com</code>. It represents the custom identity provider SAP Cloud Identity Services.

    This action also fills the fields for the single sign-on URLs and the single logout URLs.

7.  Save your changes.

8.  To get the SAML metadata of your subaccount, choose *Download SAML Metadata*.

    You download an XML file with the SAML metadata of your subaccount. Its name is <code>saml-<i class="varname">&lt;subdomain&gt;</i>-sp.xml</code>. Use this file to import the SAML metadata into your identity provider.




<a name="loioaedb8eed952b41c4b87c50b92bf651e4__postreq_wqn_tdb_f1c"/>

## Next Steps

Register your SAP BTP subaccount in the SAML 2.0 Identity Provider

<a name="loio347cc6991eda439ea7d87ef1311913bf"/>

<!-- loio347cc6991eda439ea7d87ef1311913bf -->

## Register SAP BTP Subaccount in the SAML 2.0 Identity Provider

An SAML service provider interacts with an SAML 2.0 identity provider to authenticate users signing in by means of a single sign-on \(SSO\) mechanism. In this scenario, the SAP Authorization and Trust Management service \(XSUAA\) acts as a service provider representing a single subaccount. To establish trust between an identity provider and a subaccount, you must register your subaccount by providing the SAML metadata to the identity provider. The identity provider is SAP Cloud Identity Services.



## Context

Administrators must configure trust on both sides, in the service provider and in the identity provider. This description covers the side of the identity provider \(SAP Cloud Identity Services\). The trust configuration on the side of the SAP Cloud Identity Services must contain the following items:

-   Metadata for web-based authentication or the relevant configuration information

    The metadata contains the configuration information, including the signing certificate and the required URLs. Create the metadata file of your subaccount using the *Download SAML Metadata* button in *Security* \> *Trust Configuration* of your subaccount.

-   Use e-mail as the unique name ID attribute, and map the user attribute `Groups` to the assertion attribute `Groups` \(case-sensitive\). This assertion attribute is required for the assignment of roles.


We illustrate the process of configuring trust in the service provider by describing how administrators use the administration console of SAP Cloud Identity Services to register the subaccount.

To establish trust from a tenant of SAP Cloud Identity Services to a subaccount, assign a metadata file and define attribute details. The SAML 2.0 assertion includes these attributes. With the SAP Authorization and Trust Management service as SAML 2.0 service provider, they're used for automatic assignment of SAP Authorization and Trust Management service authorizations based on information maintained in the identity provider.



<a name="loio347cc6991eda439ea7d87ef1311913bf__steps_mwt_fc2_sy"/>

## Procedure

1.  Open the administration console of SAP Cloud Identity Services.

    <code>https://<i class="varname">&lt;sap_cloud_identity_services_tenant&gt;</i>.accounts.ondemand.com/admin</code>

2.  Choose *Applications & Resources* \> *Applications* in the menu or the *Applications* tile.

3.  To add a new SAML service provider, choose *Create*.

4.  Enter the required data and choose *\+ Create*.

    -   Enter a name for the application that clearly identifies it as your new service provider.

        Users see this name in the logon screen when the authentication is requested by the SAP Authorization and Trust Management service. Seeing the name, they know which application they currently access after authentication.

    -   Choose *SAML 2.0* as the protocol type.


5.  Choose *Trust* \> *SAML 2.0 Configuration*.

6.  Under *Define from Metadata*, upload the relevant metadata XML file and choose *Save*.

    > ### Note:  
    > Use the <code>saml-<i class="varname">&lt;subdomain&gt;</i>-sp.xml</code> metadata file of your subaccount. You can create the file using the *Download SAML Metadata* button in *Security* \> *Trust Configuration* of your subaccount.

    If the contents of the metadata XML file are valid, the parsing process extracts the information required to populate the remaining fields of the SAML configuration. It provides the name, the URLs of the assertion consumer service and single logout endpoints, and the signing certificate.

7.  Choose *Default Name ID Format* and select *E-Mail* as a unique attribute. Save your changes.

8.  Choose *Attributes*, use *Add* to add an attribute named `Groups`with a source `Identity Provider` and the value `Groups` \(case-sensitive\). Save your changes.

    > ### Note:  
    > Be aware that the X.509 certificates exposed in the SAML 2.0 metadata have specific validities. This applies to both SAML service providers and SAML identity providers. Authentication may fail with an error once the X.509 certificates expire.
    > 
    > Ensure that the SAML 2.0 metadata is updated before the X.509 certificate expiry dates.
    > 
    > Sign the certificate with a new signing key. For more information, see [Rotate Signing Keys of SAML Token](rotate-signing-keys-of-saml-token-052e9b4.md).


