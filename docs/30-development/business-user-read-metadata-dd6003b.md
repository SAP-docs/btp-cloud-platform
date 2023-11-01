<!-- loiodd6003bacf9d487ba8a43118d9169e8e -->

# Business User - Read Metadata



Technical name: `QueryBusinessUserMetadataIn`

This service enables you to read metadata information from your external data source such as an identity management system for service Business User with this synchronous inbound service.

This service provides the search parameter `RoleCategory`, which restricts the result set of the metadata information of the service. The response includes the metadata information based on the given criteria. If errors occur, the log contains information about the severity code, the message number and message texts.

This service is available on the SAP Business Accelerator Hub, for more information see [APIs on SAP Business Accelerator Hub](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/latest/en-US/1e60f14bdc224c2c975c8fa8bcfd7f3f.html).



<a name="loiodd6003bacf9d487ba8a43118d9169e8e__section_gcn_jn5_qcb"/>

## Service Request

**Service Nodes**

The service nodes contain the service's business data.

****


<table>
<tr>
<th valign="top" colspan="2">

Node or Field

</th>
<th valign="top">

Description

</th>
<th valign="top">

Cardinality

</th>
</tr>
<tr>
<td valign="top" rowspan="2">

`BusinessPartnerRoleCategoryInterval`

Cardinality: 0..unbounded

</td>
<td valign="top">

`IntervalBoundaryTypeCode`

</td>
<td valign="top">

You can only use the following value:

-   1 - Equal




</td>
<td valign="top">

1..1

</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryBusinessPartnerRoleCategoryCode`

</td>
<td valign="top">

For example: `BUP003` 

</td>
<td valign="top">

0..1

</td>
</tr>
</table>



### Sample Payload

> ### Sample Code:  
> ```
> <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:aba="http://sap.com/xi/ABA">
>    <soapenv:Header/>
>    <soapenv:Body>
>       <aba:BusinessUserMetaDataQuery_sync>
>          <!--Zero or more repetitions:-->
>          <BusinessPartnerRoleCategoryInterval>
>             <IntervalBoundaryTypeCode>1</IntervalBoundaryTypeCode>
>             <LowerBoundaryBusinessPartnerRoleCategoryCode>BUP003</LowerBoundaryBusinessPartnerRoleCategoryCode>
>          </BusinessPartnerRoleCategoryInterval>
>       </aba:BusinessUserMetaDataQuery_sync>
>    </soapenv:Body>
> </soapenv:Envelope>
> 
> ```



<a name="loiodd6003bacf9d487ba8a43118d9169e8e__section_jg1_p45_qcb"/>

## Service Response

****


<table>
<tr>
<th valign="top" colspan="2">

Service Node

</th>
<th valign="top">

Description

</th>
<th valign="top">

Link to Details

</th>
</tr>
<tr>
<td valign="top" rowspan="2">

`BusinessUserMetaData`

</td>
<td valign="top">

`RoleCategoryDependentMetaData` 

</td>
<td valign="top">

This node contains all metadata, which depends on the role category of a business user, such as the role category with its role, external ID category with its external ID type or relationship category.

</td>
<td valign="top">

[RoleCategoryDependentMetaData](rolecategorydependentmetadata-bfaaf02.md)

</td>
</tr>
<tr>
<td valign="top">

`CodeList` 

</td>
<td valign="top">

This node provides the available code lists for SAP specific codes. For example country/region code, academic title.

</td>
<td valign="top">

[CodeList](codelist-c29cd1a.md)

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`Log` 

</td>
<td valign="top">

This nodes displays occurred messages.

</td>
<td valign="top">

[Log](log-8599598.md)

</td>
</tr>
</table>



### Error Codes

****


<table>
<tr>
<th valign="top">

Error Code

</th>
<th valign="top">

Message

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

112

</td>
<td valign="top">

Interval Boundary Type Code &1 is not supported for BusinessPartnerRoleCategoryInterval.

</td>
<td valign="top">

You can only use the following value:

-   1 - Equal




</td>
</tr>
<tr>
<td valign="top">

118

</td>
<td valign="top">

No data found by given search criteria.

</td>
<td valign="top">

To display all data, don't enter any value.

</td>
</tr>
</table>



<a name="loiodd6003bacf9d487ba8a43118d9169e8e__section_e4p_pbq_jlb"/>

## Authentication Method

You can use the following authentication methods: User ID/password \(Username Token\), X.509 certificate \(X509 Token\) or Single Sign On using SAML \(SAML Token\).



<a name="loiodd6003bacf9d487ba8a43118d9169e8e__section_x5f_w45_qcb"/>

## Constraints

Currently this SOAP service is only enabled for English.



<a name="loiodd6003bacf9d487ba8a43118d9169e8e__section_czf_fqf_zkb"/>

## Additional Information

If you have any issues, report an incident for component `CA-GTF-BUM`.

> ### Note:  
> For more information about the API, choose the *Details* tab on the SAP Business Accelerator Hub.

