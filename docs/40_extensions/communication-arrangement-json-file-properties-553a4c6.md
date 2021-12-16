<!-- loio553a4c6b98be4c1ba7d1dfa0e9df8669 -->

# Communication Arrangement JSON File - Properties

Use the service JSON descriptor to define the communication arrangement and the authentication type for the SAP S4/HANA Cloud API access.



<a name="loio553a4c6b98be4c1ba7d1dfa0e9df8669__section_x5z_mn2_53b"/>

## Context

To construct the JSON file for the SAP S/4HANA Cloud APIs you want to use, you can use these parameters. To access the specific documentation of these APIs, see [SAP S/4HANA Cloud APIs at SAP API Business Hub](https://api.sap.com/package/SAPS4HANACloud?section=Artifacts).

The information that you need to construct the JSON file is available in the Display Communication Scenario application in the corresponding SAP S/4HANA Cloud system. It contains information such as scenario details and properties, and supported inbound and outbound authentication methods. See [Display Communication Scenarios](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/latest/en-US/baa798b6a1024d229ca3f51bde6f24f9.html).

For specific sample JSON files, see [Communication Arrangement JSON File - Examples](communication-arrangement-json-file-examples-80a7613.md).



<a name="loio553a4c6b98be4c1ba7d1dfa0e9df8669__section_u15_q2y_khb"/>

## Properties




<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `systemName` 



</td>
<td valign="top">

The name of the system you have registered in SAP BTP global account.

> ### Note:  
> The system must be in status *Registered*.

**Rules/Guidelines**

-   Required: Yes




</td>
</tr>
<tr>
<td valign="top">

 `communicationArrangement` 



</td>
<td valign="top">

Represents a communication arrangement in SAP S/4HANA Cloud.

**Rules/Guidelines**

-   Required: Yes




</td>
</tr>
<tr>
<td valign="top">

 `communicationArrangementName` 



</td>
<td valign="top">

A `communicationArrangement` property.

Meaningful name of the communication arrangement that will be created for the SAP S/4HANA Cloud tenant.

**Rules/Guidelines**

-   Allowed characters: \[a-zA-Z0-9\_-\]

-   Max length: 80

-   Required: Yes




</td>
</tr>
<tr>
<td valign="top">

 `scenarioId` 



</td>
<td valign="top">

A `communicationArrangement` property.

The ID of the SAP S/4HANA Cloud communication scenario.

**Rules/Guidelines**

-   Required: Yes

-   Allowed characters: \[A-Z0-9\_\]

-   Pattern: ***SAP\_COM\_<number\>***




</td>
</tr>
<tr>
<td valign="top">

 `inboundAuthentication` 



</td>
<td valign="top">

A `communicationArrangement` property.

The authentication type for the SAP S/4HANA Cloud API access.

> ### Note:  
> Currently, the following authentication methods are supported:
> 
> -   Basic Authentication
> 
> -   SAML Bearer Assertion Authentication
> 
>     > ### Note:  
>     > The generated X.509 certificate that is used to configure the trust between the cloud platform and SAP S/4HANA Cloud system expires two years after you have created the instance.

**Rules/Guidelines**

-   Required: Yes, if there is no `outboundAuthentication` defined

-   Allowed values: `OAuth2SAMLBearerAssertion`, `BasicAuthentication`




</td>
</tr>
<tr>
<td valign="top">

 `outboundAuthentication` 



</td>
<td valign="top">

A `communicationArrangement` property.

The type of the authentication used by SAP S/4HANA Cloud to call SAP BTP APIs.

> ### Note:  
> Currently, the following authentication methods are supported:
> 
> -   Basic Authentication
> 
> -   OAuth 2.0 Client Credentials
> 
> -   No Authentication

**Rules/Guidelines**

-   Required: Yes, if there is no `inboundAuthentication` defined

-   Allowed values: `BasicAuthentication`, `OAuth2ClientCredentials`, `NoAuthentication`




</td>
</tr>
<tr>
<td valign="top">

 `communicationSystem` 



</td>
<td valign="top">

A `communicationArrangement` property.

This represents the *Communication System* view of the communication arrangement.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `communicationSystemHostname` 



</td>
<td valign="top">

A `communicationSystem` property.

The URL of the remote system hosting the APIs that will be consumed in case the scenario contains outbound communication. For SAP S/4HANA Cloud extensions on SAP BTP, this is the URL of the extension application running on SAP BTP.

This is equivalent to *Technical Data* \> *General* \> *Host Name* in the*Communication System* view.

**Rules/Guidelines**

-   Required: Yes, if `communicationArrangement` is specified.




</td>
</tr>
<tr>
<td valign="top">

 `port` 



</td>
<td valign="top">

A `communicationSystem` property.

The port for outbound calls to the remote system hosting the APIs that will be consumed in case the scenario contains outbound communication.

**Rules/Guidelines**

-   Required: No

    If not specified, the default *443* port is used for the communication.

-   Type: String

-   Allowed values: positive integer \[*1*-*65535*\]




</td>
</tr>
<tr>
<td valign="top">

 `oAuthAuthEndpoint` 



</td>
<td valign="top">

A `communicationSystem` property.

The OAuth authorization endpoint of the remote OAuth service in case the communication scenario contains outbound communication. This is equivalent to *Technical Data* \> *OAuth 2.0 Settings* \> *Auth. Endpoint* in the*Communication System* view.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `oAuthTokenEndpoint` 



</td>
<td valign="top">

A `communicationSystem` property.

The OAuth token endpoint. This is equivalent to *Technical Data* \> *OAuth 2.0 Settings* \> *Token Endpoint* in the*Communication System* view.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `outboundCommunicationUser` 



</td>
<td valign="top">

A `communicationSystem` property.

The communication user used for outbound authentication. This is equivalent to an entry under the *Users for Outbound Communication* table in the *Communication System* view in the SAP S/4HANA Cloud system.

> ### Note:  
> Currently, only users with authentication method *User Name and Password* are supported.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `username` 



</td>
<td valign="top">

An `outboundCommunicationUser` property.

The username of the communication user.

**Rules/Guidelines**

-   Required: Yes, if the `outboundCommunicationUser` property is specified.




</td>
</tr>
<tr>
<td valign="top">

 `password` 



</td>
<td valign="top">

An `outboundCommunicationUser` property.

The password of the communication user.

**Rules/Guidelines**

-   Required: Yes, if the `outboundCommunicationUser` property is specified.




</td>
</tr>
<tr>
<td valign="top">

 `outboundServices` 



</td>
<td valign="top">

A `communicationArrangement` property.

A list of outbound service objects.

This is equivalent to the *Outbound Services* section in the SAP S/4HANA Cloud *Communication Arrangement* view.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `outboundService` 



</td>
<td valign="top">

An `outboundServices` object.

A specific outbound service object.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

An `outboundService` property.

The name of the outbound service. It must be an exact match of the name displayed in the SAP S/4HANA Cloud system.

**Rules/Guidelines**

-   Required: Yes, if the `outboundServices` property is specified.




</td>
</tr>
<tr>
<td valign="top">

 `urlPath` 



</td>
<td valign="top">

An `outboundService` property.

This is equivalent to the *Path* field in the SAP S/4HANA Cloud system. It is used to configure the API path in the outbound service URL.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `isServiceActive` 



</td>
<td valign="top">

An `outboundService` property.

This is equivalent to the *Service Status* checkbox in the SAP S/4HANA Cloud system. In some communication scenarios, some outbound services must be disabled. You can achieve that by setting this parameter to *false*.

**Rules/Guidelines**

-   Required: No

-   Default value: ***true***




</td>
</tr>
<tr>
<td valign="top">

 `attributes` 



</td>
<td valign="top">

An `outboundService` parameter.

A list of attribute objects.

This is equivalent to the *Additional Properties* section of the outbound service.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `attribute` 



</td>
<td valign="top">

An `attributes` object.

A specific attribute object. Represents an additional property in the outbound service.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

An `attribute` property.

The name of the additional property of the outbound service. It is equivalent to the *Technical Property Name* column in the *Additional Properties* section in the Display Communication Scenarios app in the SAP S/4HANA Cloud system. See [Display Communication Scenarios](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/latest/en-US/baa798b6a1024d229ca3f51bde6f24f9.html).

**Rules/Guidelines**

-   Required: Yes, if an `attribute` object is specified.




</td>
</tr>
<tr>
<td valign="top">

 `value` 



</td>
<td valign="top">

An `attribute` property.

Enter value for the additional property of the outbound service.

**Rules/Guidelines**

-   Required: Yes, if an `attribute` object is specified.




</td>
</tr>
<tr>
<td valign="top">

 `attributes` 



</td>
<td valign="top">

A `communicationArrangement` parameter.

A list of attribute objects.

This is equivalent to the *Additional Properties* section of the communication arrangement in SAP S/4HANA Cloud.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `attribute` 



</td>
<td valign="top">

An `attributes` object.

A specific attribute object. Represents an additional property in the communication arrangement.

**Rules/Guidelines**

-   Required: No




</td>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

An `attribute` property.

It is equivalent to the *Technical Property Name* section in the *Additional Properties* table in the Display Communication Scenarios application in the SAP S/4HANA Cloud system. See [Display Communication Scenarios](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/latest/en-US/baa798b6a1024d229ca3f51bde6f24f9.html).

**Rules/Guidelines**

-   Required: Yes, if an `attribute` object is specified for `communicationArrangement`.




</td>
</tr>
<tr>
<td valign="top">

 `value` 



</td>
<td valign="top">

An `attribute` property.

Enter a value for the additional property of the communication arrangement.

**Rules/Guidelines**

-   Required: Yes, if an `attribute` object is specified for `communicationArrangement`.




</td>
</tr>
</table>

**Related Information**  


[Communication Arrangement JSON File - Examples](communication-arrangement-json-file-examples-80a7613.md "The examples in this section will help you to create the service JSON descriptor used for defining the communication arrangement and the authentication type for the SAP S/4HANA Cloud API access.")

