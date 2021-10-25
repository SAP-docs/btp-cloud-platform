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


