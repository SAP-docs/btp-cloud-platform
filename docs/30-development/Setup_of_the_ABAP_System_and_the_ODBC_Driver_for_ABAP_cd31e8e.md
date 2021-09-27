<!-- loiocd31e8e9a85a4288aecf7e44dd7d5298 -->

# Setup of the ABAP System and the ODBC Driver for ABAP

To access CDS view entities in an ABAP system via ODBC, these entities first need to be properly exposed in the back-end system before accessing them using the ODBC driver for ABAP in an ODBC application. Therefore, some setup steps are required.

In ABAP Development Tools \(ADT\) and in the SAP Fiori launchpad of the ABAP environment, perform the following steps:

1.  Create CDS view entities for your tables \(ADT\).

2.  Create a service definition and an SQL-typed service binding \(ADT\).

3.  Create a communication scenario with object privileges \(ADT\).

4.  Create a communication system, a communication user, and a communication arrangement \(SAP Fiori apps\).


In addition, prepare the ODBC driver for ABAP for its use as follows:

1.  Install the ODBC driver for ABAP.

2.  Create an ODBC data source.


-   **[Prerequisites](Prerequisites_d71ed17.md "Check whether you meet all prerequisites for running the ODBC driver for ABAP.")**  
Check whether you meet all prerequisites for running the ODBC driver for ABAP.
-   **[Constraints](Constraints_e5e0073.md "")**  

-   **[Setup in the ABAP Back-End System](Setup_in_the_ABAP_Back-End_System_76eeb8d.md "Before you can access database tables from external ODBC-based tools, perform some required setup activities in the ABAP back-end
		system.")**  
Before you can access database tables from external ODBC-based tools, perform some required setup activities in the ABAP back-end system.
-   **[Installation and Configuration of the ODBC Driver for ABAP](Installation_and_Configuration_of_the_ODBC_Driver_for_ABAP_de86ce7.md "To be able to use an ODBC-based client to access data in the exposed CDS view entities of the ABAP environment, you must install the ODBC
		driver and create an ODBC data source.")**  
To be able to use an ODBC-based client to access data in the exposed CDS view entities of the ABAP environment, you must install the ODBC driver and create an ODBC data source.

