<!-- loio353c7e5643e54ad7b2eba1486944468c -->

# Creating a Replication Flow for SQL Service Exposure

In SAP Datasphere, define a replication flow for CDS view entities using the SQL service exposure.



## Context

With defining a source of the replication flow, you specify the connection, the folder, and the replication objects \(CDS view entities\).



## Procedure

1.  To create a replication flow, follow the instructions of the SAP Datasphere documentation \(see [Creating a Replication Flow](https://help.sap.com/docs/SAP_DATASPHERE/c8a54ee704e94e15926551293243fd1d/25e2bd7a70d44ac5b05e844f9e913471.html)\).

2.  As a source connection, choose the communication system that you have created before for connecting SAP Datasphere to your ABAP environment \(see also [Creating a Communication Arrangement to Enable Replication Flows in SAP Datasphere](creating-a-communication-arrangement-to-enable-replication-flows-in-sap-datasphere-12e9990.md)\).

3.  As a source container, choose `SQL_SERVICE`.

    > ### Note:  
    > The `SQL_SERVICE` contains the SQL services that have been enabled for replication.

4.  As source objects, choose the CDS view entity that you want to use for initial and delta replication.

    If an alias was provided, the alias name is shown.

    You can choose among the custom CDS view entities that comply to the overall rules for data replication \(see [Additional Prerequisites and Constraints for Replication](additional-prerequisites-and-constraints-for-replication-fd76550.md)\). CDS view entities that support delta replication must have been annotated using `@DataIntegration.deltaReplication.intended: true`. All other CDS view entities support only full replication.

5.  Choose a target system.

6.  As a load type, select *Initial and Delta*.


