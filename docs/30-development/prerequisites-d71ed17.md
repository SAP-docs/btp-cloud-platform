<!-- loiod71ed17fe0294eceb5e5327585cdfac1 -->

# Prerequisites

Check whether you meet all prerequisites for using the SQL service.



Make sure that the following general requirements are met:

-   You have a developer user in SAP BTP, ABAP environment.
-   You have ABAP Development Tools \(ADT\) installed.
-   You have an ABAP Cloud project configured in ADT and connected to the ABAP system.

To be able to run the ODBC driver for ABAP, the following prerequisites must be met:

-   Make sure that you use a 64-bit application as an ODBC client because the ODBC driver for ABAP is only available as a 64-bit driver.
-   **Linux only**: A 64-bit Linux version is required because the ODBC driver for ABAP is a 64-bit ODBC driver. To define ODBC data source names \(DSN\) for the ODBC driver for ABAP on Linux, you must install the unixODBC software package on your Linux system. This software package also provides some simple command-line tools to test an ODBC connection and to execute SQL queries.
-   **Microsoft Windows only**: The ODBC driver requires a C/C++-runtime \(VCredist\). Make sure that the latest version of the VCredist package is installed. For more information about VCredist, see SAP Note [1553465](https://me.sap.com/notes/1553465).
-   If you want to use the open-source software package LibreOffice as an external ODBC client, make sure that you have LibreOffice installed.
-   **Business user with browser logon only:** If you want to use the access scenario for business users with browser logon, you need at least ODBC driver version 01, patch level 2.

**Related Information**  


[Access Scenarios](access-scenarios-96368bd.md "When you set up access to ABAP-managed data from ODBC-based clients, you can set up privileged or business user-based data access.")

