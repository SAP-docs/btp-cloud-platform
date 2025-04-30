<!-- loioc95327fbed6c4efeb1855f12f826301d -->

# Integrating On-Premise Systems

Set up the Cloud Connector to enable communication from the ABAP environment to your on-premise systems using Remote Function Calls \(RFC\) and HTTP calls.



<a name="loioc95327fbed6c4efeb1855f12f826301d__section_uhr_zpb_smb"/>

## Concept

For each subaccount, a Connectivity service instance is set up automatically in the SAP provider account. To use this instance, activate the Cloud Connector in your communication system.

In this scenario, you must connect the Cloud Connector to and configure trust for your Cloud Foundry subaccount as described in [SAP BTP Connectivity: Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).

> ### Restriction:  
> This scenario requires a Cloud Connector as of version 2.12.3 or higher.

> ### Note:  
> For more information on the deprecated scenario that uses the Connectivity service in the Neo environment, see [Create a Communication Arrangement for Cloud Connector Integration \(Deprecated\)](create-a-communication-arrangement-for-cloud-connector-integration-deprecated-16c9c3d.md).

After you have completed the setup, a connection from the ABAP environment tenant to an on-premise system is established in the following order:

1.  The ABAP environment tenant requests to open the tunnel connection through the Connectivity service.
2.  The Connectivity service tells the Cloud Connector to open the connection to this specific ABAP environment tenant using the admin connection.
3.  The Cloud Connector opens a tunnel connection to the ABAP environment tenant using its public tenant URL.
4.  After the tunnel is established, it can be used for actual data connection using RFC and HTTP\(S\) protocols.



<a name="loioc95327fbed6c4efeb1855f12f826301d__section_szl_1qb_smb"/>

## Next Steps

To set up your actual data connections between your ABAP environment and on-premise systems, you must enable the required Cloud Connector in your communication system. See [Enable On-Premise Connectivity](enable-on-premise-connectivity-9b6510e.md).



<a name="loioc95327fbed6c4efeb1855f12f826301d__section_j4g_yzq_swb"/>

## Troubleshooting

In case of issues using the Cloud Connector, see [Cloud Connector Troubleshooting](https://ga.support.sap.com/dtp/viewer/#/tree/2183/actions/27936:28765:28777) for a troubleshooting guide.

