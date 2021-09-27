<!-- loio13c0366d40aa42dfb94939bdb711f472 -->

# Set Up the Connectivity Between Event Mesh and the SAP S/4HANA Cloud Tenant



<a name="loio13c0366d40aa42dfb94939bdb711f472__section_cjq_hc3_qnb"/>

## Overview

To configure the connectivity between the SAP S/4HANA Cloud tenant and SAP Event Mesh and to enable the exchange of credentials between the two systems, you first need to create an *SAP S/4HANA Cloud Extensibility* service instance with service plan `messaging`. For more information about the `messaging` service plan, see [Supported Service Plans for SAP S/4HANA Cloud](Supported_Service_Plans_for_SAP_S4HANA_Cloud_925c00a.md).

When creating this service instance, you create the required configurations in both the SAP S/4HANA Cloud tenant and theEvent Mesh system associated with the subaccount in SAP BTP, so that events can flow. Depending on the SAP BTP environment, to create an `SAP S/4HANA Cloud Extensibility` service instance, you have to choose one of the following options:

-   [Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Cloud_Foundry_Environment_531a909.md)

-   [Create an SAP S/4HANA Extensibility Service Instance in the Kyma Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Kyma_Environment_55d876e.md)


After you have created the `SAP S/4HANA Cloud Extensibility` service instance, either in the Cloud Foundry or Kyma environment, you need to configure event topics for the channel inside the SAP S/4HANA Cloud tenant, and then you need to create an SAP Event Mesh service instance, respectively in the Cloud Foundry or Kyma environment, for the application to consume SAP S/4HANA Cloud events. You do this in a dedicated JSON file that you add either when creating the service instance, or after that. To construct this JSON file, see [Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON File](Define_SAP_S4HANA_Cloud_Extensibility_Service_Descriptor_JSON_File_2d50d91.md).



<a name="loio13c0366d40aa42dfb94939bdb711f472__section_w3s_zcl_d4b"/>

## Process Flow


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

1. Create an `SAP S/4HANA Cloud Extensibility` service instance with service plan `messaging`.



</td>
<td>

-   [Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Cloud_Foundry_Environment_531a909.md)

-   [Create an SAP S/4HANA Extensibility Service Instance in the Kyma Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Kyma_Environment_55d876e.md)




</td>
</tr>
<tr>
<td>

2. Define a dedicated JSON file that you add either when creating the `SAP S/4HANA Cloud Extensibility` service instance, or after that.



</td>
<td>

 [Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON File](Define_SAP_S4HANA_Cloud_Extensibility_Service_Descriptor_JSON_File_2d50d91.md) 



</td>
</tr>
<tr>
<td>

3. Configure event topics for the channel inside SAP S/4HANA Cloud tenant.



</td>
<td>

 [Configure Event Topics in SAP S/4HANA Cloud](Configure_Event_Topics_in_SAP_S4HANA_Cloud_f5bbc57.md) 



</td>
</tr>
</table>

-   **[Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Cloud_Foundry_Environment_531a909.md "Use this procedure to configure the communication between SAP S/4HANA Cloud and SAP Event
                                        Mesh.")**  
Use this procedure to configure the communication between SAP S/4HANA Cloud and SAP Event Mesh.
-   **[Create an SAP S/4HANA Extensibility Service Instance in the Kyma Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Kyma_Environment_55d876e.md "Use this procedure to configure the communication between SAP S/4HANA Cloud and SAP Event
                                        Mesh
		in the Kyma environment.")**  
Use this procedure to configure the communication between SAP S/4HANA Cloud and SAP Event Mesh in the Kyma environment.
-   **[Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON File](Define_SAP_S4HANA_Cloud_Extensibility_Service_Descriptor_JSON_File_2d50d91.md "The SAP S/4HANA Cloud Extensibility service descriptor defines details of a messagе
		client and needs to be provided when provisioning new SAP S/4HANA Cloud Extensibility
		service instances with service plan messaging.")**  
The SAP S/4HANA Cloud Extensibility service descriptor defines details of a messagе client and needs to be provided when provisioning new SAP S/4HANA Cloud Extensibility service instances with service plan `messaging`.
-   **[Configure Event Topics in SAP S/4HANA Cloud](Configure_Event_Topics_in_SAP_S4HANA_Cloud_f5bbc57.md "Configure event topics for the channel inside the SAP S/4HANA Cloud tenant.")**  
Configure event topics for the channel inside the SAP S/4HANA Cloud tenant.

