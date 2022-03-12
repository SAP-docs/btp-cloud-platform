<!-- loio52a055025b364fb891069fb7b12b3fc9 -->

# Example: Loading and Transforming Data Using Microsoft Excel

After creating a DSN, you can use this DSN in an ODBC client tool of your choice. Learn how you can use Microsoft Excel for loading and transforming data as an example.



## Procedure

1.  Start Microsoft Excel.

2.  In the menu, choose *Data* \> *Get Data* \> *From Other Sources* \> *From ODBC*.

3.  In the following popup, enter the DSN.

4.  **Communication user only:** In the *Database* section of the popup, you're prompted for user and password to log on to the ABAP system. Enter the user and password that you remember from when you created the communication system \(see [Creating a Communication System and a Communication User](creating-a-communication-system-and-a-communication-user-28881fb.md)\).

5.  **Business user only:** In the *Database* section of the popup, you're prompted for user and password. You can enter any user or password; authentication is not checked at this point.

6.  Choose *Connect*.

    **Business user only:** When a connection is opened by Excel, a browser window with a logon dialog for the ABAP system appears. Depending on your system configuration, the browser logon might ask your for your credentials \(user and password\). Enter your business user name and password for the ABAP system.

    The navigator appears and shows all exposed objects in the SQL schema that you've chosen to expose, that is, in the example used here, the SQL schema `ZOrders`.

7.  To display a preview of the data content in Excel, choose one of the CDS entities.

8.  Choose either *Load* to load the data into an Excel sheet or choose *Transform Data* to switch to Power Query in Excel.

    When you load the data into an Excel sheet, you can always refresh the data if needed.

9.  To execute a free-style SQL query on the exposed entities, choose *Data* \> *Get Data* \> *From Other Sources* \> *From ODBC* again from the menu in Excel and then choose *Advanced Options*.

10. In the new control, you can enter a `SELECT` statement.

    In the `SELECT` statement, you must prefix all view names by your schema name \(in the example used here, `ZOrders`\). Apart from these necessary prefixes, you can use an ANSI-like SQL syntax. The result set shows up in an Excel preview window.


