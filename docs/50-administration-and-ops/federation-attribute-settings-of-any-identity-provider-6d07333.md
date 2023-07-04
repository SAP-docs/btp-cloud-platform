<!-- loio6d073332bc5743fdb7f7f06bde499ab7 -->

# Federation Attribute Settings of Any Identity Provider

This table is supposed to display the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a new subaccount.



Since there are multiple identity providers you can use, we display the parameters and values of SAP Cloud Identity Services - Identity Authentication. Use the information in this table as a reference for the configuration of your identity provider.

**Settings of Identity Authentication for SAML 2.0 Trust**


<table>
<tr>
<th valign="top">

UI Element



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

Upload the metadata file from the UAA service.



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

 *Select Assertion Attributes* 



</td>
<td valign="top">

To define the user authorizations in the UAA service, provide the user groups in the assertion attribute `Groups` \(capitalized\). This assertion attribute is required for the assignment of roles in the UAA service.

You can change the default names of the assertion attributes that the application uses to recognize the user attributes. You can use multiple assertion attributes for the same user attribute.

Some possible settings:

-   *Groups*

-   *first\_name*

-   *last\_name*

-   *email*


You can choose from a number of user attributes and add them.



</td>
<td valign="top">

Select the *Groups* user attribute and enter `Groups` as assertion attribute. You must set this attribute to enable that the assignment from role collection to user groups has an effect. For more information, see the related link.

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


[Map Role Collections to User Groups](map-role-collections-to-user-groups-51acfc8.md "You want to assign a role collection to a user group provided by an identity provider that has a custom trust configuration in SAP BTP. In this case, the assignment is a mapping of a user group to a role collection. Your identity provider provides the user groups using the assertion attribute called Groups. Each value of the attribute is mapped to a role collection as described in this procedure.")

