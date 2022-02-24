<!-- loioeca3915ad0994566bc1bb1de37dbd04c -->

# Creating an ODBC Data Source on Windows \(Privileged Access\)

The *ODBC Data Sources \(64 bit\)* tool is part of a standard Windows installation. In this tool, you can create ODBC data sources and assign a data source name \(DSN\) to a newly created data source.



## Procedure

1.  Launch the Windows ODBC data source administrator tool.

2.  Choose the *User DSN* or *System DSN* tab, choose *Add*, choose the ODBC driver for ABAP as ODBC driver, and choose *Finish*.

    The DSN setup dialog of the ODBC driver for ABAP starts.

3.  In this dialog, choose a DSN and fill in the driver-specific parameters that are described in more detail in SAP Note [3076454](https://launchpad.support.sap.com/#/notes/3076454).

    > ### Note:  
    > You can derive the host name and the service path from the service URL that you wrote down when you created the communication arrangement.
    > 
    > The user name \(for example, `SQL_CLIENT_USER`\) that you created in the communication system is automatically the alias name for the generated ABAP user name. Therefore, switch the user type to alias.


