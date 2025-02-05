<!-- loio2bacacd8e9e9450e8fb2aafd9dca1f75 -->

# Integrating SQL Services Using SAP Datasphere

You need the integration scenario `SAP_COM_0532` if you want to create a replication flow in SAP Datasphere to subscribe to CDS view entities from an ABAP system and consume data from these views. With a communication arrangement based on`SAP_COM_0532` combined with a communication arrangement for exposing the SQL service, you can consume data from custom CDS view entities that are exposed using the SQL service.

The connection that you establish for this scenario is shared by all SAP Datasphere users, and SAP Datasphere controls the usage of the connection and accessed data assets through its integrated policy management agent.

SAP Datasphere connects to the CDC \(Change Data Capture\) functionality for CDS view entities that records changes of exposed CDS view entities. This component allows multiple consumers to subscribe to a CDS view entity to get the CDS data including the option for delta recording and delta consumption.

SAP Datasphere either adds another subscription to an existing CDS extraction process \(if the CDS view entity is already processed by another subscriber\) or creates a new extraction process and adds a subscription \(if the CDS view entity is configured for extraction the first time\), followed by the consumption of the data.



<a name="loio2bacacd8e9e9450e8fb2aafd9dca1f75__section_k1h_w1m_zzb"/>

## Prerequisites

-   You have entered the user and password for your user \(typically a technical user\) and have selected *SAP ABAP* as the connection type for the connection to the SAP system in the *Connections* area.

-   The user in the SAP system that you use to complete the configuration steps should have administrator privileges or at least Business Catalog ID `SAP_CORE_BC_COM` for access to *Communication Management*.

-   You are familiar with the steps required to expose CDS view entities. For more information, see [Data Consumption Using SAP Datasphere](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/data-consumption-using-sap-datasphere).




<a name="loio2bacacd8e9e9450e8fb2aafd9dca1f75__section_emz_w1m_zzb"/>

## Procedure

1.  Create a communication user in the *Maintain Communication Users* app. You will later need this user name and password to establish the connection in SAP Datasphere.

2.  Create a communication system in the *Communication Systems* app and select the checkbox *Inbound only*.

    **Background information:** A communication system is important for outbound services, as it is used to register a destination for the communication system in the ABAP system. In the given scenario, requests always originate from the external system, so selecting the checkbox *Inbound only* is sufficient.

3.  For a production scenario, switch on *OAuth 2.0 Identity Provider*, enter a provider name and upload a signing certificate. Note that this step is not relevant if you are creating a test scenario.

4.  Add the communication user that you created in step 1 with authentication method *User Name and Password* to *Users for Inbound Communication*.

5.  Create a communication arrangement for communication scenario `SAP_COM_0532` in the*Communication Arrangement* app and enter the name of the communication system that you created in step 2. Note that you do not need to specify an authorization group ID.

6.  In SAP Datasphere, choose *Connections*. On the *Local Connections* tab, choose the *Create* button.

7.  Enter the necessary information. Choose the connection type *SAP ABAP*. In the *Protocol* field, select the value *Web Socket RFC*. In the *SAP Logon Connection Type* field, select the value *Application Server*. In the *Use Cloud Connector* field, ensure the value *False* is selected. Use the inbound user data from step 4.

8.  Test the connection by choosing the *Validate* button. Ensure that the status is *OK* before proceeding.

9.  Create a communication arrangement based on a communication scenario with object privileges so that the communication user created in step 1 can access the exposed CDS view entities. For more information, see [Creating a Communication Arrangement for Exposing the SQL Service](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/creating-replication-flow-for-sql-service-exposure).


You can now create a replication flow in SAP Datasphere to consume data from CDS view entities.

