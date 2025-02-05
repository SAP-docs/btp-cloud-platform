<!-- loio4082fe1b66164eeb8aa41192166526af -->

# Accessing ABAP-Managed Data Using SQL Services for Data Integration Scenarios

As a developer in the ABAP environment, you can expose CDS view entities in an ABAP system for external consumption using SQL services.

Using the open database connectivity \(ODBC\) as a standard API for accessing databases, you can use SQL statements in external analytical tools to access the data of these CDS view entities from your ABAP system and formulate ad-hoc SQL queries on your data. You can also use the exposed CDS view entities from SQL services to set up data replication for further processing of the data and combining it with data from other data sources.



<a name="loio4082fe1b66164eeb8aa41192166526af__section_jmw_lw4_vzb"/>

## Why SQL Services?

There are situations where you would like to have external SQL read access to CDS objects owned by the ABAP system. Direct SQL read access to the underlying SAP HANA database of an ABAP system isn't recommended because, for example, ABAP-level security concepts are bypassed and typecasts might not be performed as expected \(see also SAP Note [2511210](https://me.sap.com/notes/2511210)\).

Security concerns and other aspects such as authentication and authorization don't arise if you treat the ABAP system itself as a database by accessing the ABAP system directly using the SQL service exposure. In this case, authentication and authorization are done using an ABAP user. Full ABAP SQL semantics apply and even buffering on application server level can be used as well as ABAP-level access control and read access logging.

Compared to the OData interface, the SQL service exposure has the advantage that it allows for unrestricted SQL access to all exposed ABAP CDS view entities. Data from different entities can be joined in an ad-hoc fashion and data can be aggregated for analytical queries.



<a name="loio4082fe1b66164eeb8aa41192166526af__section_klk_3jn_c1c"/>

## Data Integration Patterns and Scenarios

Data access patterns for ABAP-managed data can be categorized into data federation and data replication, as well as privileged access and business user access. Data federation allows for live access to the source system without replicating the data, while data replication involves replicating the data to a second system for local execution. Privileged access enables communication between an SQL-based client and the ABAP system using a communication user. \(The communication user is a non-restricted technical power user or represents a technical system.\) Business user access applies access controls to limit data access based on authorizations of the business user.

Examples of data consumption scenarios include data consumption using external ODBC clients like Microsoft Excel and LibreOffice, which can work with both privileged and business user access. Another example is data consumption using SAP Datasphere, where data is replicated from an ABAP system to SAP Datasphere for analytical scenarios.



<a name="loio4082fe1b66164eeb8aa41192166526af__section_vhm_zn2_ldc"/>

## More Information

For more information and a detailed end-to-end setup description, see the ABAP integration and connectivity guide on SAP Help Portal:

[Data Integration](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/data-integration) \(concept and architecture overview\)

[Data Integration](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/data-integration-84537caeb611420b9f3435efce209ef7) \(developer guide\)

