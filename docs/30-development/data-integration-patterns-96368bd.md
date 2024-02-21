<!-- loio96368bd086ff4f79933b078a6cf7feaa -->

# Data Integration Patterns

When you set up access to ABAP-managed data using SQL services, you can set up privileged or business user-based data access. As consumption scenarios, there's data federation and replication.

When you set up access to ABAP-managed data to be consumed using SQL services, the following dimensions can be distinguished:

-   Data federation vs. data replication

-   Privileged access vs. business user access


These dimensions also have interdependencies.



<a name="loio96368bd086ff4f79933b078a6cf7feaa__section_vgq_bht_szb"/>

## Data Federation vs. Data Replication

With data federation, data remains in its source system and all requests are forwarded to the source system and executed on the original data. Data federation is used in scenarios where live access to the source system is required, for example, to access the most recent data without a time lag, or to rely on data access control mechanisms inside the source system.

With data replication, data is replicated to a second system and requests are executed locally on the replicated data like, for example, in a data warehouse. Data replication is used where it's more efficient to transfer \(business\) data from a source to a target system before the data is accessed within that target system.

For more information about the differences between data federation and data replication, see also [Develop Integration Services](https://help.sap.com/docs/abap-cloud/abap-cloud/communication-management-for-integration-services?locale=en-US) in the ABAP Cloud documentation.



<a name="loio96368bd086ff4f79933b078a6cf7feaa__section_cdx_chy_gsb"/>

## Privileged Access vs. Business User Access



### Privileged Access

With privileged access, the communication between an SQL-based client and the ABAP system is set up for a communication user. Access controls aren't applied on the ABAP side, which means that the communication user can access all data from the CDS view entities for which the communication user is authorized.

Exposure of CDS entities is controlled by service definitions and SQL service bindings. Authorizations are controlled on the level of service bindings or individual CDS view entities. The communication on the ABAP side is configured using communication scenarios and communication arrangements.

In the example used in this documentation, the communication user has read access to all data \(order data from all regions\).



### Business User Access

With business user access, communication is established for a business user. Access controls for the exposed CDS view entities are active and the business user can only access data from the exposed CDS view entities filtered by the business user’s authorizations.

Exposure of CDS entities is controlled by service definitions and SQL service bindings. Authorizations are controlled on the level of service bindings and the authorizations that are referenced in access controls. Authorizations are assigned using IAM apps, restriction types, and business catalogs.

In the example in this documentation, a restriction type is used to limit the access of the business user to order data from one region only.



<a name="loio96368bd086ff4f79933b078a6cf7feaa__section_pzw_k3t_szb"/>

## Dependencies Between Dimensions

The following table shows how these dimensions can be combined:


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

Data Federation

</th>
<th valign="top">

Data Replication

</th>
</tr>
<tr>
<td valign="top">

Privileged Access

</td>
<td valign="top">

Supported

</td>
<td valign="top">

Supported

</td>
</tr>
<tr>
<td valign="top">

Business User Access

</td>
<td valign="top">

Supported

</td>
<td valign="top">

Not supported

</td>
</tr>
</table>



<a name="loio96368bd086ff4f79933b078a6cf7feaa__section_v2f_tmm_c1c"/>

## Examples

In the documentation here, you can find examples of different data access patterns: For example, the data consumption using the external ODBC clients Microsoft Excel and LibreOffice are data federation scenarios that work with privileged and business user access. Data replication is currently only supported using SAP Datasphere as replication middleware.

**Related Information**  


[Data Consumption Using External ODBC Clients](data-consumption-using-external-odbc-clients-0237571.md "As a developer in the ABAP environment, you can access CDS view entities in an ABAP system using SQL and the open database connectivity (ODBC), a standard API for accessing databases. As a result, you can use SQL statements in external analytical tools to access data in database tables (via CDS view entities) that reside in the ABAP environment.")

[Data Consumption Using SAP Datasphere](data-consumption-using-sap-datasphere-ec312dd.md "You can consume ABAP-managed data using SAP clients such as SAP Datasphere.")

