<!-- loio3b27703e7ad24982931db245f23d6bcf -->

# Analyzing the Performance of SQL Statements Running on Your ABAP Environment

Learn how to use SQL statement and trace analysis in the ABAP environment.

Data retrieval and modification through SQL statements are the main functions of the SAP HANA database in your ABAP environment. When you develop new applications or operate them productively, you need to analyze the performance of SQL statements executed by your applications on the database.

When analyzing statement performance, you typically encounter one of the following scenarios:

-   You’re focused solely on the performance of SQL statements within your application. You don't need to consider other SQL activities on your database.

    -   To trace SQL statements, you have the following options:

        You may prefer the lightweight option integrated into ABAP Development Tools for Eclipse \(ADT\) if you are in a developer role. For more information, see [Tracing SQL Statements for Developers](tracing-sql-statements-for-developers-b72f289.md).

        Administrators can use an option with more functions available on the Fiori launchpad. For more information, see [Tracing SQL Activities for Administrators](tracing-sql-activities-for-administrators-28c007c.md).

    -   To deepen your performance analysis of SQL statements, you can obtain HANA executed plans in two ways:

        You can switch on the HANA plan trace for the statement hash of a specific SQL statement. For more information, see [Tracing HANA Executed Plans Using the Capture Request Statistics App](tracing-hana-executed-plans-using-the-capture-request-statistics-app-c38357c.md).

        You can also use ABAP Development Tools for Eclipse \(ADT\) to get HANA executed plans of SQL statements issued by SAP Fiori apps. For more information, see [Tracing HANA Executed Plans Using the ABAP Cross Trace in ADT](tracing-hana-executed-plans-using-the-abap-cross-trace-in-adt-2056152.md).


-   You want to view the performance of SQL statements along with other SQL activities on your database.

    Start with the `SQL Statement Analysis` app that you can find on the SAP Fiori Launchpad. For more information, see [SQL Statement Analysis](https://help.sap.com/viewer/b273a660af4e4948a49a316ea2438f24/Cloud/en-US/2d3e9aff21194e81bbb781384b60b02c.html#loio2d3e9aff21194e81bbb781384b60b02c "Use the SQL Statement Analysis app to analyze the performance and resource consumption of SQL statements within a selectable time range.") :arrow_upper_right:.


