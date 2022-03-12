<!-- loio76eeb8dfa5da40afa641cd1a60fbc839 -->

# Developing and Exposing an SQL Service in the ABAP System

Before you can access database tables from external ODBC-based tools, you must start with some preparatory steps such as developing and exposing an SQL service in the ABAP system.



<a name="loio76eeb8dfa5da40afa641cd1a60fbc839__section_wpc_cyv_nsb"/>

## Context

When you want to enable the access to ABAP-managed data from external ODBC clients, you must start with some preparatory steps. These steps include the creation of CDS view entities for the tables for which you want to access, a service definition, and an SQL-typed service binding. Optionally, you can also create your own test tables. Test tables are used in this documentation as examples.

Depending on your access scenario \(priviliged data access with a communication user or data access with a business user\), you must perform different additional steps.



<a name="loio76eeb8dfa5da40afa641cd1a60fbc839__section_qmd_xry_lsb"/>

## Privileged Access with a Communication User

For accessing database tables using a communication user, you must also create a communication scenario and a communication system in ABAP Development Tools. An administrator creates a corresponding communication arrangement and user. The assumption in this documentation is that the communication user gets privileged data access.



<a name="loio76eeb8dfa5da40afa641cd1a60fbc839__section_dy3_zry_lsb"/>

## Access with a Business User

For accessing database tables using a business user, this documentation also shows how to configure data access where access is limited to orders for a specific region. For this scenario, you must create an authorization object, access control, an IAM app, and a business catalog in ABAP Development Tools. An administrator creates a business role and assigns a business user.

**Related Information**  


[Access Scenarios](access-scenarios-96368bd.md "When you set up access to ABAP-managed data from ODBC-based clients, you can set up privileged or business user-based data access.")

