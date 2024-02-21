<!-- loio12e9990684f8484097106fe79f6b4261 -->

# Creating a Communication Arrangement to Enable Replication Flows in SAP Datasphere

Create a communication arrangement based the integration scenario `SAP_COM_0532` to enable replication flows in SAP Datasphere.



<a name="loio12e9990684f8484097106fe79f6b4261__prereq_yx3_bdf_zzb"/>

## Prerequisites

You have already created a communication arrangement based on a communication scenario with object privileges so that the communication user in the ABAP system can access the service binding of the SQL service \(see [Creating a Communication Scenario with Object Privileges](creating-a-communication-scenario-with-object-privileges-990eb54.md) and [Creating a Communication Arrangement for Exposing the SQL Service](creating-a-communication-arrangement-for-exposing-the-sql-service-167b9ba.md)\).



## Context

You need the integration scenario `SAP_COM_0532` if you want to use replication flows in SAP Datasphere to subscribe to CDS view entities from an ABAP system and consume data from these views. With a communication arrangement based on `SAP_COM_0532` and with a communication arrangement for exposing the SQL service, you can now consume data from public CDS view entities released by SAP and from **custom** CDS view entities that are exposed using an ABAP SQL service.



## Procedure

1.  Create a communication arrangement based on the integration scenario `SAP_COM_0532`.

2.  In the communication arrangement, enter the communication system and communication user that you created for the service binding \(see *Prerequisites*\).


**Related Information**  


[Integrating SQL Services Using SAP Datasphere](../50-administration-and-ops/integrating-sql-services-using-sap-datasphere-2bacacd.md "You need the integration scenario SAP_COM_0532 if you want to create a replication flow in SAP Datasphere to subscribe to CDS view entities from an ABAP system and consume data from these views. With a communication arrangement based on SAP_COM_0532 combined with a communication arrangement for exposing the SQL service, you can consume data from custom CDS view entities that are exposed using the SQL service.")

