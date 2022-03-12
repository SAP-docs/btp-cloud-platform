<!-- loio96368bd086ff4f79933b078a6cf7feaa -->

# Access Scenarios

When you set up access to ABAP-managed data from ODBC-based clients, you can set up privileged or business user-based data access.



<a name="loio96368bd086ff4f79933b078a6cf7feaa__section_cdx_chy_gsb"/>

## Privileged Data Access

With privileged data acess, the communication between an ODBC-based client and the ABAP system is set up with a communication user. Access controls are not applied on the ABAP side, which means that the technical user can access all data from the CDS view entities for which the user is authorized.

Exposure of CDS entities is controlled by service definitions and SQL service bindings. Authorizations are controlled on the level of service bindings or individual CDS view entities. The communication on the ABAP side is configured using communication scenarios and communication arrangements.

In the example in this documentation, the communication user has read access to all data \(order data from all regions\).



<a name="loio96368bd086ff4f79933b078a6cf7feaa__section_fjd_dhy_gsb"/>

## Business User Access

With this data access, communication is established with a business user. Access controls for the exposed CDS view entities are active and the business user can only access data from the exposed CDS view entities filtered by the user’s authorizations.

Exposure of CDS entities is controlled by service definitions and SQL service bindings. Authorizations are controlled on the level of service bindings and the authorizations that are referenced in access controls. Authorizations are assigned using IAM apps, restriction types, and business catalogs.

In the example in this documentation, a restriction type is used to limit the access of the business user to order data from one region only.

