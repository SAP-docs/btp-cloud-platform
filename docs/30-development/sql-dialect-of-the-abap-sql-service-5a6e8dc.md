<!-- loio5a6e8dcbdfea4cc49a14854a62c2e06c -->

# SQL Dialect of the ABAP SQL Service

The SQL dialect of the ABAP SQL service is a modified ABAP SQL dialect executed by the ABAP SQL engine.



<a name="loio5a6e8dcbdfea4cc49a14854a62c2e06c__section_gtf_fjr_nwb"/>

## Basic Features

The SQL dialect of the ABAP SQL service shares many features with ABAP SQL, which is a subset of SQL realized using ABAP statements. In fact, the SQL dialect of the ABAP SQL service is a modified ABAP SQL dialect executed by the ABAP SQL engine. It works on ABAP-managed entities and profits from many ABAP server-specific features like automatic client handling, table buffering, and DCL handling.

However, in some respects, the SQL dialect of the ABAP SQL service is more like ANSI SQL or HANA SQL, the native SQL dialect of the SAP HANA database. For example, in ODBC, there are no ABAP host variables or internal tables, which exist in ABAP SQL. Parameter markers and type casts in the SQL dialect of the ABAP SQL service are handled similar to HANA SQL.

The SQL dialect of the ABAP SQL service is restricted to read-only SQL queries that don’t set locks on database level. No `INSERT`/`UPDATE`/`DELETE` statements and no `SELECT FOR UPDATE` are allowed on objects exposed in an SQL service. Therefore, the SQL service has no concept of database transactions and `COMMIT` or `ROLLBACK` statements aren’t needed.

In addition, there are also some features that are specific to the SQL dialect of the ABAP SQL service and that can’t be found in ABAP or HANA SQL. For example, to access objects, a schema name and an object name must be used. What’s also new is that the SQL service provides a set of system tables where metadata can be retrieved using SQL.



<a name="loio5a6e8dcbdfea4cc49a14854a62c2e06c__section_gvj_kpr_nwb"/>

## Documentation Scope and More Information

This documentation gives you a brief overview of the supported SQL features, highlighting some of the differences and similarities to HANA SQL and ABAP SQL. For more information about HANA SQL and ABAP SQL, see the following documentation:

[ABAP SQL](https://help.sap.com/doc/abapdocu_latest_index_htm/latest/en-US/index.htm?file=abenabap_sql.htm)

[SAP HANA SQL Reference Guide for SAP HANA Platform](https://help.sap.com/docs/SAP_HANA_PLATFORM/4fe29514fd584807ac9f2a04f6754767/b4b0eec1968f41a099c828a4a6c8ca0f.html?locale=en-US)

