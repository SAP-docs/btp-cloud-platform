<!-- loiodd6003bacf9d487ba8a43118d9169e8e -->

# Business User - Read Metadata



Technical name: `QueryBusinessUserMetadataIn`

This service enables you to read metadata information from your external data source such as an identity management system for service Business User with this synchronous inbound service.

This service provides the search parameter `RoleCategory`, which restricts the result set of the metadata information of the service. The response includes the metadata information based on the given criteria. If errors occur, the log contains information about the severity code, the message number and message texts.

This service is available on the SAP API Business Hub, for more information see [APIs on SAP API Business Hub](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/latest/en-US/1e60f14bdc224c2c975c8fa8bcfd7f3f.html).



<a name="loiodd6003bacf9d487ba8a43118d9169e8e__section_gcn_jn5_qcb"/>

## Service Request

**Service Nodes**

The service nodes contain the service's business data.

<a name="loiodd6003bacf9d487ba8a43118d9169e8e__table_qvr_l2b_v4b"/>


<table>
<tr>
<th colspan="2">

Node or Field



</th>
<th>

Description



</th>
<th>

Cardinality



</th>
</tr>
<tr>
<td rowspan="2">

`BusinessPartnerRoleCategoryInterval`

Cardinality: 0..unbounded



</td>
<td>

`IntervalBoundaryTypeCode`



</td>
<td>

You can only use the following value:

-   1 - Equal




</td>
<td>

1..1



</td>
</tr>
<tr>
<td>

`LowerBoundaryBusinessPartnerRoleCategoryCode`



</td>
<td>

For example: `BUP003` 



</td>
<td>

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

<a name="loiodd6003bacf9d487ba8a43118d9169e8e__table_gxy_245_qcb"/>


<table>
<tr>
<th colspan="2">

Service Node



</th>
<th>

Description



</th>
<th>

Link to Details



</th>
</tr>
<tr>
<td rowspan="2">

`BusinessUserMetaData`



</td>
<td>

 `RoleCategoryDependentMetaData` 



</td>
<td>

This node contains all metadata, which depends on the role category of a business user, such as the role category with its role, external ID category with its external ID type or relationship category.



</td>
<td>

[RoleCategoryDependentMetaData](RoleCategoryDependentMetaData_bfaaf02.md)



</td>
</tr>
<tr>
<td>

 `CodeList` 



</td>
<td>

This node provides the available code lists for SAP specific codes. For example country/region code, academic title.



</td>
<td>

[CodeList](CodeList_c29cd1a.md)



</td>
</tr>
<tr>
<td colspan="2">

 `Log` 



</td>
<td>

This nodes displays occurred messages.



</td>
<td>

[Log](Log_8599598.md)



</td>
</tr>
</table>



### Error Codes

<a name="loiodd6003bacf9d487ba8a43118d9169e8e__table_nnf_vtp_jlb"/>


<table>
<tr>
<th>

Error Code



</th>
<th>

Message



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

112



</td>
<td>

Interval Boundary Type Code &1 is not supported for BusinessPartnerRoleCategoryInterval.



</td>
<td>

You can only use the following value:

-   1 - Equal




</td>
</tr>
<tr>
<td>

118



</td>
<td>

No data found by given search criteria.



</td>
<td>

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
> For more information about the API, choose the *Details* tab on the SAP API Business Hub.

-   **[RoleCategoryDependentMetaData](RoleCategoryDependentMetaData_bfaaf02.md)**  

-   **[CodeList](CodeList_c29cd1a.md)**  

-   **[Log](Log_8599598.md)**  


