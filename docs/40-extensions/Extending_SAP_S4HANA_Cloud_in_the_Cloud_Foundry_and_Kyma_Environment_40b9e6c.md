<!-- loio40b9e6c3cc43498b92472da13e88c7bf -->

# Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment

Extend SAP S/4HANA Cloud with extension applications running on the cloud platform using automated integration configuration.



<a name="loio40b9e6c3cc43498b92472da13e88c7bf__section_ptj_pmf_nhb"/>

## Overview

> ### Note:  
> EU Access is not available for SAP S/4HANA Cloud Extensibility service, and the integration is not supported for SAP S/4HANA Cloud tenants that require EU Access.

The extension capabilities of SAP BTP offer a standard way for extending SAP S/4HANA Cloud and developing event-driven extensions and applications.

You can extend SAP S/4HANA Cloud without disrupting its performance and core processes. When building extension applications, you can also benefit from the automation of the integration between the cloud platform and SAP S/4HANA Cloud.

The following graphic provides a high-level overview of the integration between the cloud platform and SAP S/4HANA Cloud:

![](images/SAPCPExtensionFactory_11bf994.png)



<a name="loio40b9e6c3cc43498b92472da13e88c7bf__section_tsg_vmf_nhb"/>

## Process Flow

To integrate the cloud platform and SAP S/4HANA Cloud so that you can build extension applications, you need to:

<a name="loio40b9e6c3cc43498b92472da13e88c7bf__table_cyp_dpr_y3b"/>Integrating SAP BTP and SAP S/4HANA Cloud


<table>
<tr>
<th>

Process Step



</th>
<th>

Related Documentation



</th>
</tr>
<tr>
<td>

1. Connect the SAP S/4HANA Cloud system you want to extend with the corresponding global account in SAP BTP.

During the pairing process you create an integration token which is then used by the SAP S/4HANA Cloud system tenant administrator to configure the integration on the SAP S/4HANA Cloud system side.



</td>
<td>

 [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](Register_an_SAP_S4HANA_Cloud_System_in_a_Global_Account_in_SAP_BTP_28171b6.md) 



</td>
</tr>
<tr>
<td>

2. Make the SAP S/4HANA Cloud system accessible in the SAP BTP subaccounts in which you want to build your extension applications.

To do so, you configure the entitlements and assign the corresponding quota and service plans to the subaccounts where the extension applications will reside for the system you registered in the previous step.



</td>
<td>

 [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](Configure_the_Entitlements_for_the_SAP_S4HANA_Cloud_Extensibility_Service_65ad330.md) 



</td>
</tr>
<tr>
<td>

3. Configure the communication flow.

You have the following options:

-   Consume the SAP S/4HANA Cloud APIs \(inbound connection\) or consume APIs exposed by the extension application from SAP S/4 HANA Cloud \(outbound connection\)

    To do so, you create a service instance of the *SAP S/4HANA Cloud Extensibility* service using the *api-access* service plan.

    During the service instance creation an HTTP destination on a subaccount level is automatically generated in this subaccount. It contains all instance binding properties which are sufficient to establish connection to the SAP S/4HANA Cloud system. When creating the service instance, you configure the communication arrangement and the authentication type for the connection. The following authentication scenarios for SAP S/4HANA Cloud are supported:

    -   Basic Authentication \(inbound and outbound connections\)
    -   OAuth 2.0 SAML Bearer Assertion \(inbound connections\)
    -   OAuth 2.0 Client Credentials \(outbound Connections\)
    -   No Authentication \(outbound connections\)
    Both predefined and custom communication scenarios are supported.

-   Enable the consumption of SAP S/4HANA Cloud events.

    If you want to create event-based extensions for SAP S/4HANA Cloud using the SAP Event Mesh, you have to create a service instance of the *SAP S/4HANA Cloud Extensibility* service using the *messaging* service plan.

-   A combination of both



</td>
<td>

-   [Creating a Service Instance to Consume the SAP S/4HANA Cloud APIs](Create_a_Service_Instance_to_Consume_the_SAP_S4HANA_Cloud_APIs_a735641.md)

-   [Enable the Consumption of SAP S/4HANA Cloud Events](Enable_the_Consumption_of_SAP_S4HANA_Cloud_Events_d476ff0.md)




</td>
</tr>
</table>

-   **[Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](Register_an_SAP_S4HANA_Cloud_System_in_a_Global_Account_in_SAP_BTP_28171b6.md "To connect an SAP S/4HANA Cloud system with a global account in SAP BTP, you need to register the
		system in the corresponding global account. ")**  
To connect an SAP S/4HANA Cloud system with a global account in SAP BTP, you need to register the system in the corresponding global account.
-   **[Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](Configure_the_Entitlements_for_the_SAP_S4HANA_Cloud_Extensibility_Service_65ad330.md "Configure the required entitlements to make the APIs of the registered SAP S/4HANA Cloud
		system accessible in your subaccount in which your extension applications will
		reside.")**  
Configure the required entitlements to make the APIs of the registered SAP S/4HANA Cloud system accessible in your subaccount in which your extension applications will reside.
-   **[Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](Create_a_Service_Instance_to_Consume_the_SAP_S4HANA_Cloud_APIs_a735641.md " To enable the integration of your extension applications with the SAP S/4HANA Cloud
		system you have registered in the SAP BTP global account, and
		to configure the communication flow, you create a service instance of the SAP S/4HANA Cloud
		Extensibility service.")**  
 To enable the integration of your extension applications with the SAP S/4HANA Cloud system you have registered in the SAP BTP global account, and to configure the communication flow, you create a service instance of the SAP S/4HANA Cloud Extensibility service.
-   **[Enable the Consumption of SAP S/4HANA Cloud Events](Enable_the_Consumption_of_SAP_S4HANA_Cloud_Events_d476ff0.md "To create event-based extensions for SAP S/4HANA Cloud you need to set up the messaging
		between the SAP S/4HANA Cloud system and the SAP Event
                                        Mesh.")**  
To create event-based extensions for SAP S/4HANA Cloud you need to set up the messaging between the SAP S/4HANA Cloud system and the SAP Event Mesh.
-   **[Supported Service Plans for SAP S/4HANA Cloud](Supported_Service_Plans_for_SAP_S4HANA_Cloud_925c00a.md "The following service plans are available for subaccounts in SAP BTP paired with
		an SAP S4/HANA Cloud tenant.")**  
The following service plans are available for subaccounts in SAP BTP paired with an SAP S4/HANA Cloud tenant.
-   **[Auditing and Logging Information](Auditing_and_Logging_Information_b250a8d.md "Here you can find a list of the events that are logged by SAP S/4HANA Cloud
            Extensibility service. To retrieve the audit logs stored for SAP S/4HANA
            Cloud Extensibility create a support ticket in component BC-NEO-EXT-S4C.")**  
Here you can find a list of the events that are logged by SAP S/4HANA Cloud Extensibility service. To retrieve the audit logs stored for SAP S/4HANA Cloud Extensibility create a support ticket in component BC-NEO-EXT-S4C.

**Related Information**  


[Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html)

