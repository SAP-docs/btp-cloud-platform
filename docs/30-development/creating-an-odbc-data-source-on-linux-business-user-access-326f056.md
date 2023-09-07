<!-- loio326f0560dd434b9ca26331ac19275049 -->

# Creating an ODBC Data Source on Linux \(Business User Access\)

With the settings described here, you create an ODBC data source and DSN for a business user. To enable a business user to log on to the ABAP system with user name and password, you configure the browser-based logon method in the ODBC DSN.



## Context

The unixODBC software package provides an ODBC driver manager that can read from multiple configuration files. You can create configuration files that define the location of the ODBC driver and DSNs.

In the example used in this documentation, you need the ODBC data source for a business user that is provided data access to the ABAP system.



<a name="loio326f0560dd434b9ca26331ac19275049__steps_pyl_l5f_hsb"/>

## Procedure

1.  List the locations of the configuration files by executing the command `odbcinst -j`.

    You get a result such as the following, for example:

    > ### Sample Code:  
    > ```
    > > odbcinst -j
    > 
    > unixODBC 2.3.6
    > DRIVERS............: /etc/unixODBC/odbcinst.ini
    > SYSTEM DATA SOURCES: /etc/unixODBC/odbc. [MYDSN]>
    > FILE DATA SOURCES..: /etc/unixODBC/ODBCDataSources
    > USER DATA SOURCES..: /home/myuser/.odbc.ini
    > SQLULEN Size.......: 8
    > SQLLEN Size........: 8
    > SQLSETPOSIROW Size.: 8
    > 
    > ```

2.  To define both the driver and a user-specific DSN, create the file `/home/myuser/.odbc.ini`.

    You can create a system-wide driver definition and DSN in a similar way.

3.  In the `/home/myuser/.odbc.ini` file, insert the DSN-specific connection parameters for the ODBC driver for ABAP as described in SAP Note [3076454](https://me.sap.com/notes/3076454). In addition, you configure the browser-logon method using `AuthenticationType` and `AuthenticationURL`.

    For example, these parameters can look as follows:

    > ### Sample Code:  
    > ```
    > [MYDSN]
    > ; this is a comment
    > Driver=/home/<myuser>/ODBC_driver_for_ABAP/ODBC_driver_for_ABAP.so
    > HOST=<hostname>
    > PORT=443
    > CLIENT=100
    > LANGUAGE=EN
    > SERVICEPATH=/sap/bc/sql/sql1/sap/zdata
    > TrustAll=true
    > CryptoLibrary=/home/<myuser>/ODBC_driver_for_ABAP/libsapcrypto.so
    > AuthenticationType=Browser
    > AuthenticationURL=https://<uihost>/sap/bc/sec/reentrance
    > UID=dummy
    > PWD=dummy
    > 
    > ```

    In this example, the driver definition was included in the `.odbc.ini` file using the driver keyword. In the example, for the sake of simplicity, no PSE file was created and the `TrustAll=True` property was used instead. The entries UID=dummy and PWD=dummy were added so that you are not forced to enter a user and password in the browser that are required by the unixODBC tool `iusql` for testing, but are not needed by the ODBC driver.

4.  Use the unixODBC tools `isql` or `iusql` to test the ODBC connection.

    If everything is configured correctly, you can see the following in the `iusql` tool, for example:

    > ### Sample Code:  
    > ```
    > > iusql MYDSN -v
    > 
    > +---------------------------------------+
    > | Connected!                            |
    > |                                       |
    > | sql-statement                         |
    > | help [tablename]                      |
    > | quit                                  |
    > |                                       |
    > +---------------------------------------+
    > SQL>
    > ```


