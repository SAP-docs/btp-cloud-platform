<!-- loiof488fd4316d54179bec5513ea953c989 -->

# Example: Loading and Transforming Data Using LibreOffice

After the successful configuration of the ABAP system and the installation of the ODBC driver for ABAP, you can load and transform data from the exposed CDS view entities. You can use external tools such as LibreOffice on Linux, for example.



<a name="loiof488fd4316d54179bec5513ea953c989__context_j4x_3tw_psb"/>

## Context

> ### Note:  
> **Relevant for business user access using browser logon:** If you’re using unixODBC tools such as `isql` or `iusql` on command line as ODBC clients instead of LibreOffice, make sure that you work an environment such as XWindow where a browser window can open.



## Procedure

1.  Start LibreOffice.

2.  In LibreOffice Calc, choose *File* \> *New* \> *Database*.

3.  Choose the *Connect to an existing database* radio button, select *ODBC*, and choose *Next*.

4.  Enter the DSN that you inserted into your `.odbc.ini` file and choose *Next*.

5.  **Communication user only:** Enter a user name.

    **Communication user only:** You can test your connection after providing a password.

6.  Choose *Finish*.

    **Business user only:** When a connection is opened by LibreOffice, a browser window with a logon dialog for the ABAP system appears. Depending on your system configuration, the browser logon might ask your for your credentials \(user and password\). Enter your business user name and password for the ABAP system.

    LibreOffice now displays all exposed CDS view entities. You can choose these entities to get a data preview.

7.  To enter an SQL query string and retrieve the result, choose*Create Query in SQL View*.

    > ### Note:  
    > LibreOffice automatically double-quotes all identifiers in the SQL query. Therefore, you must use the mixed case names for the CDS entities that you defined in the ABAP back end.


