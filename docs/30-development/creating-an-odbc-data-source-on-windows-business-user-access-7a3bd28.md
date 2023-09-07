<!-- loio7a3bd28acbc84953943f0905798a0cb0 -->

# Creating an ODBC Data Source on Windows \(Business User Access\)

You create an ODBC data source and DSN for a business user. To enable a business user to log on to the ABAP system with user name and password, you configure the browser-based logon method in the ODBC DSN.



## Context

The *ODBC Data Sources \(64 bit\)* tool is part of a standard Windows installation. In this tool, you can create ODBC data sources and assign a data source name \(DSN\) to a newly created data source.

In the example used in this documentation, you need the ODBC data source for a business user that is provided data access to the ABAP system.



<a name="loio7a3bd28acbc84953943f0905798a0cb0__steps_a2s_5rf_hsb"/>

## Procedure

1.  Launch the Windows ODBC data source administrator tool.

2.  Choose the *User DSN* or *System DSN* tab, choose *Add*, choose the ODBC driver for ABAP as ODBC driver, and choose *Finish*.

    The DSN setup dialog of the ODBC driver for ABAP starts.

3.  In this dialog, choose a DSN and fill in the driver-specific parameters that are described in more detail in SAP Note [3076454](https://me.sap.com/notes/3076454).

    > ### Note:  
    > `ServicePath` must point to the SQL service that you created \(in the example used here, `ZData`\): `ServicePath=/sap/bc/sql/sql1/sap/zdata`.
    > 
    > Don't forget to configure the browser-logon method using `AuthenticationType` and `AuthenticationURL`:
    > 
    > `AuthenticationType=Browser`
    > 
    > `AuthenticationURL=https://<uihost>/sap/bc/sec/reentrance`


