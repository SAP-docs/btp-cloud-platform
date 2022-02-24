<!-- loiod63fc2e78bae4405a09a4e7f7ea9f819 -->

# Creating an ODBC Data Source on Linux \(Privileged Access\)

With the settings described here, you create an ODBC data source and DSN for a communication user.



<a name="loiod63fc2e78bae4405a09a4e7f7ea9f819__context_c4w_rt5_msb"/>

## Context

The unixODBC software package provides an ODBC driver manager that can read from multiple configuration files. You can create configuration files that define the location of the ODBC driver and DSNs.



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

3.  In the `/home/myuser/.odbc.ini` file, insert the DSN-specific connection parameters for the ODBC driver for ABAP as described in SAP Note [3076454](https://launchpad.support.sap.com/#/notes/3076454).

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
    > SERVICEPATH=/sap/bc/sql/sql1/sap/S_PRIVILEGED
    > TrustAll=true
    > CryptoLibrary=/home/<myuser>/ODBC_driver_for_ABAP/libsapcrypto.so
    > UidType=alias
    > ```

    In this example, the driver definition was included in the `.odbc.ini` file using the driver keyword. As connect user for the test system, you can use the user `SQL_CLIENT_USER` that you created as an alias user in the ABAP environment. It's also possible to store the UID/PWD properties in the`.odbc.ini` file. However, we don't recommend the use of a file for security reasons. In the example, for the sake of simplicity, no PSE file was created and the `TrustAll=True` property was used instead.

4.  Use the unixODBC tools `isql` or `iusql` to test the ODBC connection.

    If everything is configured correctly, you can see the following in the `iusql` tool, for example:

    > ### Sample Code:  
    > ```
    > > iusql MYDSN SQL_CLIENT_USER <password> -v
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


