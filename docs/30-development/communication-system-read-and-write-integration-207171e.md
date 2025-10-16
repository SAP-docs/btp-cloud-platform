<!-- loio207171e0d1c44871b59289733b935d0d -->

# Communication System - Read and Write Integration



This service enables you to:

-   Read and write communication systems

-   Read and write assigned inbound users, outbound users and communication arrangements


This service is published on the SAP Business Accelerator Hub. For more information about APIs, see the *Related Information* section.

This is an OData version 4 service. This version aims to improve processing time and resource consumption of clients and servers. This includes a lightweight JSON format that reduces the size of every response.



<a name="loio207171e0d1c44871b59289733b935d0d__section_TechnicalDetails_CommunicationSystem_RW"/>

## Technical Details


<table>
<tr>
<th valign="top">

Service Group \(incl. Namespace if It Exists\)

</th>
<th valign="top">

Repository ID

</th>
<th valign="top">

Service Name \(incl. Namespace if It Exists\)

</th>
<th valign="top">

Version

</th>
</tr>
<tr>
<td valign="top">

`aps_com_cs_a4c_odata`

</td>
<td valign="top">

`srvd_a2x`

</td>
<td valign="top">

`aps_com_cs_a4c_odata`

</td>
<td valign="top">

`0001`

</td>
</tr>
</table>



<a name="loio207171e0d1c44871b59289733b935d0d__section_ServiceStructureCommunicationSystemRW"/>

## Service Structure

**Service Header \(optional\)**

The service header contains information about the service.

**Entities**

The entities contain the business data of the service.

****


<table>
<tr>
<th valign="top">

Entity

</th>
<th valign="top">

Description

</th>
<th valign="top">

Constants

</th>
<th valign="top">

Necessity

</th>
</tr>
<tr>
<td valign="top">

CommunicationSystems

</td>
<td valign="top">

Contains communication system data

</td>
<td valign="top">

Contains the following attributes and values:

-   Type

    -   customer\_managed

    -   provider\_managed

-   CipherSuites

    -   TLS\_1\_0\_to\_1\_2

    -   TLS\_1\_0\_to\_1\_3
    -   TLS\_1\_2\_only

    -   TLS\_1\_2\_to\_1\_3


    Please note that these values can also be empty.

-   IsCipherSuiteDefault

    -   TLS\_1\_0\_to\_1\_2

    -   TLS\_1\_0\_to\_1\_3
    -   TLS\_1\_2\_only

    -   TLS\_1\_2\_to\_1\_3


    Please note that these values can also be empty.

-   OAuth2IdentityProviderUserLogonType
    -   user\_uuid

    -   user\_name

-   SAMLBearerAssertionProviderUserLogonType
    -   user\_uuid

    -   user\_name




</td>
<td valign="top">

Mandatory

</td>
</tr>
<tr>
<td valign="top">

InboundUsers

</td>
<td valign="top">

Contains references to the communication user ID

</td>
<td valign="top">

Contains the following attributes and values:

-   OAuth2GrantType

    -   authorization\_code

    -   saml2-bearer
    -   ropc
    -   client\_credentials


-   OAuth2RefreshTokenExpiryUnit

    -   days

    -   months

    -   years


-   AuthenticationMethod

    -   x509

    -   basic
    -   none
    -   oauth2
    -   oauth2\_mtls
    -   sso2
    -   oauth1




</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

OutboundUsers

</td>
<td valign="top">

Contains outbound user data

</td>
<td valign="top">

Contains the following attributes and values:

-   OAuth2ClientAuthenticationMethod

    -   basic

    -   mtls
    -   jwt

-   AuthenticationMethod
    -   x509

    -   basic
    -   none
    -   oauth2
    -   oauth2\_mtls
    -   sso2
    -   oauth1




</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

BusinessPartners

</td>
<td valign="top">

Contains references to the business partner IDs

</td>
<td valign="top">

 

</td>
<td valign="top">

Optional

</td>
</tr>
</table>



<a name="loio207171e0d1c44871b59289733b935d0d__section_AdditionalInformation_CommunicationSystemRW"/>

## Additional Information



> ### Note:  
> For more information about Communication Management, see the *Related Information* section.

**Related Information**  


[Communication Arrangements - Entity](communication-arrangements-entity-26253af.md)

[**APIs on SAP Business Accelerator Hub**](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/1e60f14bdc224c2c975c8fa8bcfd7f3f.html?version=latest)

[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

