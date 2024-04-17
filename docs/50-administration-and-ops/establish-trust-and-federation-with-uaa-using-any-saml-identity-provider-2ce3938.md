<!-- loio2ce3938c66d94479848bff3090999027 -->

# Establish Trust and Federation with UAA Using Any SAML Identity Provider

To establish trust, configure the trust configuration of the SAML 2.0 identity provider in your subaccount using the SAP BTP cockpit. Next, register your subaccount in User Account and Authentication service using the administration console of your SAML 2.0 identity provider. To complete federation, maintain the federation attributes of the SAML 2.0 user groups. This makes sure that you can assign authorizations to user groups.

<a name="loio8a213ea1a8664e6b96c0593e71339e0e"/>

<!-- loio8a213ea1a8664e6b96c0593e71339e0e -->

## Establish Trust with Any SAML 2.0 Identity Provider in a Subaccount

You want to use an SAML 2.0 identity provider. This is where the business users for SAP BTP are stored.



<a name="loio8a213ea1a8664e6b96c0593e71339e0e__prereq_dvg_xgj_p1b"/>

## Prerequisites

-   You have subaccount administrator permissionsor you are a security administrator \(cloud management tools feature set A\) of this account. For more information, see the related link.

-   You have downloaded the SAML 2.0 metadata file from your SAML 2.0 identity provider using the relevant URL. For more information, see the documentation of your identity provider.




## Context

You must establish a trust relationship with an SAML 2.0 identity provider in your subaccount in SAP BTP. The following procedure tries to guide you though the trust configuration in your SAML 2.0 identity provider.



## Procedure

1.  Go to your subaccount\(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\) and choose *Security* \> *Trust Configuration* \> ** in the SAP BTP cockpit.

2.  Choose *New Trust Configuration*.

3.  Enter a name and a description that make it clear that the trust configuration refers to your identity provider.

    > ### Note:  
    > Make sure that the users who are supposed to log on to this identity provider understand the name of the trust configuration.

4.  To get the relevant metadata, get to the metadata of your identity provider.

5.  Copy the SAML 2.0 metadata and paste it into the *Metadata* field.

6.  To validate the metadata, choose *Parse*. Take care that the *Subject* and *Issuer* fields are filled with the relevant data from your SAML 2.0 identity provider.

    The name of the new trust configuration now shows the value of your identity provider. It represents your custom identity provider.

    Check whether the fields for the single sign-on URLs and the single logout URLs are filled.

7.  Save your changes.

8.  \(Optional, cloud management tools feature set A\) If you do not need SAP ID service, set it to inactive.

    You have successfully configured trust in your SAML 2.0 identity provider.

9.  To get the SAML metadata of your subaccount, choose the *SAML Metadata* button. You create an XML file with the SAML metadata of your subaccount. Its name is `saml-<subdomain>-sp.xml`. Use this file to import the SAML metadata into your identity provider.


**Related Information**  


[Managing Security Administrators in Your Subaccount \[Feature Set A\]](managing-security-administrators-in-your-subaccount-feature-set-a-6752c4b.md "Running on the cloud management tools feature set A: When you create a subaccount, SAP BTP automatically grants your user the role for the administration of business users and their authorizations in the subaccount. Having this role, you can also add or remove other users who will then also be user and role administrators of this subaccount.")

<a name="loio2bf08c7e91794ddfa0702a353be4c61d"/>

<!-- loio2bf08c7e91794ddfa0702a353be4c61d -->

## Register SAP BTP Subaccount in Any SAML 2.0 Identity Provider

An SAML service provider interacts with an SAML 2.0 identity provider to authenticate users signing in by means of a single sign-on \(SSO\) mechanism. In this scenario, the User Account and Authentication \(UAA\) service acts as a service provider representing a single subaccount. To establish trust between an identity provider and a subaccount, you must register your subaccount by providing the SAML details for web-based authentication in the identity provider itself.



## Context

Administrators must configure trust on both sides, in the service provider and in the SAML identity provider. This description tries to guide you through the configuration of your identity provider. The trust configuration on the side of the SAM 2.0 identity provider must contain the following items:

-   Metadata for web-based authentication or the relevant configuration information

    If available, the metadata contains the configuration information, including the signing certificate and the required URLs. You can create the metadata file of your subaccount using the *SAML Metadata* button in *Security* \> *Trust Configuration* of your subaccount.

-   Use e-mail as the unique name ID attribute, and map the user attribute `Groups` to the assertion attribute `Groups` \(capitalized\). This attribute is required for the assignment of roles.

    This makes sure that there is a trust relationship between your SAM 2.0 identity provider and the subaccount.


Your administrators use the administration console of your SAML 2.0 identity provider to register the subaccount.

To establish trust from a tenant of your identity provider to a subaccount, assign a metadata file and define attribute details. The SAML 2.0 assertion includes these attributes. With the UAA as SAML 2.0 service provider, they are used for automatic assignment of UAA authorizations based on information maintained in the identity provider.



<a name="loio2bf08c7e91794ddfa0702a353be4c61d__steps_mwt_fc2_sy"/>

## Procedure

1.  Open the administration console of your SAML 2.0 identity provider.

2.  Go to the configuration of your SAML 2.0 identity provider.

3.  Add a new SAML service provider as described in the documentation of your identity provider.

4.  \(If applicable\) Choose a name for your identity provider that clearly identifies it as your new service provider. Save your changes.

    Users see this name in the logon screen when the authentication is requested by the UAA service. Seeing the name, they know which application they currently access after authentication.

5.  Choose the SAML 2.0 configuration and import the relevant metadata XML file. Save your changes.

    > ### Note:  
    > Use the `saml-<subdomain>-sp.xml` metadata file of your subaccount. You can create the file using the *SAML Metadata* button in *Security* \> *Trust Configuration* of your subaccount.

    Take care that the fields of the SAML configuration are filled. The metadata provides information, such as the name, the URLs of the assertion consumer service and single logout endpoints, and the signing certificate.

6.  Choose or create the name ID attribute and select E-mail as a unique attribute. Save your changes.

7.  Choose or create a user attribute, and enter `Groups` \(capitalized\) as attribute name for the *Groups* user attribute. Save your changes.


**Related Information**  


[Settings for Default SAML Federation Attributes of Identity Providers for Business Users](establish-trust-and-federation-with-uaa-using-any-saml-identity-provider-2ce3938.md#loio6d073332bc5743fdb7f7f06bde499ab7 "This table shows the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a subaccount.")

<a name="loio6d073332bc5743fdb7f7f06bde499ab7"/>

<!-- loio6d073332bc5743fdb7f7f06bde499ab7 -->

## Settings for Default SAML Federation Attributes of Identity Providers for Business Users

This table shows the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a subaccount.



Since there are multiple identity providers you can use, we display the parameters and values of SAP Cloud Identity Services - Identity Authentication. Use the information in this table as a reference for the configuration of your identity provider.

**Settings of Identity Authentication for SAML 2.0 Trust**


<table>
<tr>
<th valign="top">

Section in the User Interface

</th>
<th valign="top">

Description

</th>
<th valign="top">

Recommended Value

</th>
</tr>
<tr>
<td valign="top">

*SAML 2.0 Configuration* 

</td>
<td valign="top">

Configures the trust with a service provider using an uploaded metadata file.

</td>
<td valign="top">

Upload the metadata file from the SAP Authorization and Trust Management service.

</td>
</tr>
<tr>
<td valign="top">

*Default Name ID Format* 

</td>
<td valign="top">

Configures the attribute that the identity provider uses to identify the users. The attribute is sent as the name ID for the authenticated user in SAML assertions.

Possible settings:

-   *User ID*

-   *E-Mail*

-   *Display Name*

-   *Login Name*

-   *Employee Number*




</td>
<td valign="top">

*E-Mail*

> ### Note:  
> We recommend that you use exactly this name ID format.



</td>
</tr>
<tr>
<td valign="top">

*Attributes* 

</td>
<td valign="top">

To assign authorizations indirectly, provide the user groups in the assertion attribute `Groups` \(capitalized\).

You can change the default names of the assertion attributes that the application uses to recognize the user attributes. You can use multiple assertion attributes for the same user attribute.

Some possible settings:

-   *Groups*

-   *first\_name*

-   *last\_name*

-   *email*


You can choose from a number of user attributes and add them.

</td>
<td valign="top">

Select the *Groups* user attribute and enter `Groups` as assertion attribute. You must set this attribute to enable that the assignment of role collection to user groups. For more information, see the related link.

> ### Caution:  
> Use exactly this spelling:
> 
> `Groups`



</td>
</tr>
</table>

> ### Example:  

In the following, you see what John Doe's SAML 2.0 assertion looks like if *Default Name ID Format* was set to *E-Mail* and *Assertion Attribute* to *Groups*.

> ### Sample Code:  
> ```
> <Assertion xmlns="urn:oasis:names:tc:SAML:2.0:assertion" xmlns:ns2="http://www.w3.org/2000/09/xmldsig#" xmlns:ns3="http://www.w3.org/2001/04/xmlenc#" ID="A-de4246c0-397e-4df0-baf0-cde399d55422" IssueInstant="2017-10-23T08:52:39.494Z" Version="2.0">
>       <Issuer>company-security.accounts.ondemand.com</Issuer>
>       <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
>              ...
>       </ds:Signature>
>       <Subject>
>              <NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress">john.doe@example.com</NameID>
>              <SubjectConfirmation Method="urn:oasis:names:tc:SAML:2.0:cm:bearer">
>                     <SubjectConfirmationData InResponseTo="a3h3d679ae07c8cj2ih97d22i7d79a0" NotOnOrAfter="2017-10-23T09:02:39.494Z" Recipient="https://authentication.example.hana.ondemand.com/saml/SSO/alias/company-prod-example"/>
>              </SubjectConfirmation>
>       </Subject>
>       <Conditions NotBefore="2017-10-23T08:47:39.494Z" NotOnOrAfter="2017-10-23T09:02:39.494Z">
>              <AudienceRestriction>
>                     <Audience>aws-live-eu10</Audience>
>              </AudienceRestriction>
>       </Conditions>
>       <AuthnStatement AuthnInstant="2017-10-23T08:52:39.494Z" SessionIndex="S-SP-83d68a13-25fe-44b8-a139-649ca3e99363" SessionNotOnOrAfter="2017-10-23T20:52:39.494Z">
>       ..
>       </AuthnStatement>
>       <AttributeStatement>
>     	<Attribute Name="Groups">
> 			<AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="xs:string">iot-acme-monitoring</AttributeValue>
> 			<AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="xs:string">new-group-01</AttributeValue>
> 			<AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="xs:string">new-group-02</AttributeValue>
> 		</Attribute>
>     	<Attribute Name="email">
> 			<AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="xs:string">john.doe@example.com</AttributeValue>
> 		</Attribute>
>       </AttributeStatement>
> </Assertion>
> ```

**Related Information**  


[Map Role Collections to User Groups](map-role-collections-to-user-groups-51acfc8.md "You want to assign a role collection to a user group provided by an identity provider that has a custom trust configuration in SAP BTP. In this case, the assignment is a mapping of a user group to a role collection. Your identity provider provides the user groups using the attribute called Groups. Each value of the attribute is mapped to a role collection as described in this procedure.")

