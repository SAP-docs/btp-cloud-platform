<!-- loio7a9d90b705734858aca99b4c9f0e369f -->

# Developing SQL Queries on CDS Objects Exposed as SQL Service

You can develop your own SQL queries on objects exposed using an ABAP SQL service.

For example, in some cases, you want to use SQL client software applications to interact with the ABAP system using the ODBC driver and using your own defined SQL queries. In other cases, you want to access data using the ODBC driver with programs written in programming languages such as Python or Node.js.

In all these cases, you can access CDS view entities in an ABAP system using SQL via Open Database Connectivity \(ODBC\). However, you need to know more details on the supported SQL dialect of the ABAP SQL service to be able to define your SQL queries appropriately. This dialect is what is outlined in this documentation.

> ### Note:  
> If you use standard tools with an ODBC client like MS Excel or LibreOffice, the tools themselves assemble the SQL queries executed over the ODBC driver. The tools assume some kind of ANSI SQL compatibility and can derive details about the supported SQL dialect from ODBC `SQLGetInfo()` attributes.

