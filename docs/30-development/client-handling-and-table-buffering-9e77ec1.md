<!-- loio9e77ec1115a74c2191266cae0499fed5 -->

# Client Handling and Table Buffering



The SQL dialect of the ABAP SQL service is processed by the ABAP SQL engine. As a result, ABAP session variables like the session client are automatically set. On CDS view entities, this ensures that only data from the logon client of the current user is visible. The ABAP SQL engine can also use other ABAP application server-specific mechanisms like table buffering and not all SQL statements need to be routed to the underlying SAP HANA database.

