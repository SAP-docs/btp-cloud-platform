<!-- loioabf7105063f345edad7588cf58d53118 -->

# Develop a Remote-Enabled Function Module \(RFM\)

Develop RFMs in ABAP Development Tools \(ADT\).

You can develop RFMs in ABAP Development Tools \(ADT\) for Eclipse. For more information, see [Creating an ABAP Function Module](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/4ec6a4ea6e391014adc9fffe4e204223.html?version=Cloud).

In this tool, you create the respective RFM as you are used to in an on-premise system. Objects that are required to consume the RFM remotely are created automatically, such as authorization default values and the respective inbound service.

> ### Note:  
> To enable automatic object creation for an RFM in ADT, choose *Properties* and select `RFC` as *<Processing Type\>*. The default processing type is `Normal`. When activating an RFM of type `Normal`, no objects are generated.

For detailed information on consuming an RFM in an inbound communication scenario, see [Set Up the Cloud Connector for Inbound RFC from On-Premise Systems \(Deprecated\)](set-up-the-cloud-connector-for-inbound-rfc-from-on-premise-systems-deprecated-2ec368e.md).



<a name="loioabf7105063f345edad7588cf58d53118__section_h2r_sqf_m4b"/>

## RFC Metadata Integration \(Communication Scenario SAP\_COM\_0636\)

Instead of using classic RFC via CPI-C, you can also use RFC via WebSocket with SAP Java Connector \(JCo\) or other RFC connectors.

Optionally, you can configure these external RFC connectors to use a dedicated user to retrieve the metadata.

> ### Note:  
> This scenario also applies for calls routed through the Cloud Connector.

Communication scenario `SAP_COM_0636` lets you separate metadata access for RFC calls by RFC client libraries from the actual RFC application call.

It provides access to the following function modules:

-   *RFC\_METADATA\_GET*
-   *RFC\_FUNCTION\_SEARCH*
-   *RFC\_GET\_FUNCTION\_INTERFACE*
-   *DDIF\_FIELDINFO\_GET*

> ### Note:  
> When using WebSocket RFC, you must use a host name that follows the pattern `<myTenantHost>.abap.hana.ondemand.com`.

**Related Information**  


[Communication Scenarios Managed by SAP](communication-scenarios-managed-by-sap-c15c71a.md "SAP provides ready-to-use communication scenarios. These scenarios can contain inbound and outbound services.")

