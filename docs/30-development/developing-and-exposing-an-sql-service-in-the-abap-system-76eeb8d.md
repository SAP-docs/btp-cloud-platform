<!-- loio76eeb8dfa5da40afa641cd1a60fbc839 -->

# Developing and Exposing an SQL Service in the ABAP System

Before you can access database tables from external ODBC-based tools, you must start with some preparatory steps such as developing and exposing an SQL service in the ABAP system.



<a name="loio76eeb8dfa5da40afa641cd1a60fbc839__section_wpc_cyv_nsb"/>

## Context

When you want to enable the access to ABAP-managed data from external ODBC clients, you must start with some preparatory steps. These steps include the creation of CDS view entities for the tables for which you want to access, a service definition, and an SQL-typed service binding. Optionally, you can also create your own test tables. Test tables are used in this documentation as examples.



<a name="loio76eeb8dfa5da40afa641cd1a60fbc839__section_qmd_xry_lsb"/>

## Privileged Access with a Communication User

For accessing database tables using a communication user, you must also create a communication scenario and a communication system in ABAP Development Tools. An administrator creates a corresponding communication arrangement and user. The assumption in this documentation is that the communication user gets privileged data access.

