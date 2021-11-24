<!-- loioc95327fbed6c4efeb1855f12f826301d -->

# Integrating On-Premise Systems

Set up the Cloud Connector to enable communication from the ABAP environment to your on-premise systems using Remote Function Calls \(RFC\) and HTTP calls.



<a name="loioc95327fbed6c4efeb1855f12f826301d__section_uhr_zpb_smb"/>

## Concept

For each subaccount, both a default Connectivity and Destination service instance are set up automatically in the SAP provider account. Using these default instances, you only need to configure the required destinations on subaccount level to enable communication to your on-premise systems.

In this default scenario, you must connect the Cloud Connector to and configure trust for your Cloud Foundry subaccount as described in [SAP BTP Connectivity: Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).

> ### Restriction:  
> This scenario requires a Cloud Connector as of version 2.12.3.

The host name of the Cloud Connector is not needed because the Cloud Connector itself connects **to the Cloud**, but it is **never connected from the Cloud**.

> ### Note:  
> For more information on the deprecated scenario that uses the Connectivity service in the Neo environment, see [Create a Communication Arrangement for Cloud Connector Integration \(Deprecated\)](Create_a_Communication_Arrangement_for_Cloud_Connector_Integration_(Deprecated)_16c9c3d.md).

After you have completed the setup, a connection from the ABAP environment tenant to an on-premise system is established in the following order \(the picture below shows the default scenario\):

1.  The ABAP environment tenant fetches the destination from the Destination service instance.
2.  The ABAP environment tenant requests to open the tunnel connection through the Connectivity service.
3.  The Connectivity service tells the Cloud Connector to open the connection to this specific ABAP environment tenant using the admin connection.
4.  The Cloud Connector opens a tunnel connection to the ABAP environment tenant using its public tenant URL.
5.  After the tunnel is established, it can be used for actual data connection using RFC and HTTP\(S\) protocols.



<a name="loioc95327fbed6c4efeb1855f12f826301d__section_szl_1qb_smb"/>

## Next Steps

To set up your actual data connections between your ABAP environment and on-premise systems, you must configure the required destinations. See [Setting Up Destinations to Enable On-Premise Connectivity](Setting_Up_Destinations_to_Enable_On-Premise_Connectivity_9b6510e.md).

