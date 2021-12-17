<!-- loio3b27703e7ad24982931db245f23d6bcf -->

# Analyzing the Performance of SQL Statements Running on Your ABAP Environment

Learn how you can use SQL EXPLAIN and SQL trace analysis in the ABAP environment.

Data retrieval and modification via SQL statements is the main business of the SAP HANA database in your ABAP Environment. When you develop new applications, or when you operate applications productively, you want to analyze the performance of the SQL statements executed by your applications on the database.

When you analyze statement performance, you typically have one of the following scenarios:

-   You are only interested in the performance of SQL statements of your application regardless of other SQL activity on your database.

    For this, you can use the SQL trace analysis in the technical monitoring cockpit to display and analyze SQL traces you have run with your ABAP Development Tools.

-   You want to see the performance of SQL statements alongside the rest of the SQL activity on your database. The right starting point for this is the SQL statement analysis of the technical monitoring cockpit.


For each of the scenarios, we show you how to proceed here.



<a name="loio3b27703e7ad24982931db245f23d6bcf__section_bsb_jkr_spb"/>

## Prerequisites

For using SQL EXPLAIN and SQL trace analysis, you need a business role based on the business role template `SAP_BR_DEVELOPER`.

