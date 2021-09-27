<!-- loiofddd26347b3e4c5397a31bc3ed507028 -->

# Enable the SAP Event Mesh Service for Your Subaccount in SAP BTP



<a name="loiofddd26347b3e4c5397a31bc3ed507028__section_msh_5gl_d4b"/>

## Prerequisites

-   Уou have created the `SAP S/4HANA Cloud Extensibility` service instance in the Cloud Foundry or Kyma environment. See:

    -   [Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Cloud_Foundry_Environment_531a909.md)

    -   [Create an SAP S/4HANA Extensibility Service Instance in the Kyma Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Kyma_Environment_55d876e.md)

-   You have configured event topics for the channel inside SAP S/4HANA Cloud tenant. See [Configure Event Topics in SAP S/4HANA Cloud](Configure_Event_Topics_in_SAP_S4HANA_Cloud_f5bbc57.md).




<a name="loiofddd26347b3e4c5397a31bc3ed507028__section_bzw_1dj_qnb"/>

## Overview

To enable the SAP Event Mesh for your subaccount in SAP BTP, you have to create an instance of the SAP Event Mesh service with service plan `default`. This instance will specify the details of the namespace that you created in SAP Event Mesh for the SAP S/4HANA Cloud Extensibility service instance with the `messaging` plan. This way, you are setting up a contract between SAP Event Mesh and the Cloud Foundry, or the Kyma environment, and connect them to enable seamless event flow from the given SAP S/4HANA Cloud tenant.

Depending on the SAP BTP environment, to create an SAP Event Mesh service instance, you have to choose one of these:

-   [Create an SAP Event Mesh Service Instance in the Cloud Foundry Environment](Create_an_SAP_Event_Mesh_Service_Instance_in_the_Cloud_Foundry_Environment_c2d4d87.md)

-   [Create an SAP Event Mesh Service Instance in the Kyma Environment](Create_an_SAP_Event_Mesh_Service_Instance_in_the_Kyma_Environment_3de02d2.md)


Define the details of your message client in SAP Event Mesh as parameters in a dedicated JSON file. To map the message client to the client defined in the SAP S/4HANA Cloud JSON file, in the SAP Event Mesh JSON file, you must include the `subscribeFilter` parameter which specifies the `sap/S4HANAOD/{emClientId}` namespace you created for the SAP S/4 HANA Cloud Extensibility instance of the `messaging` plan. For more information about the structure of the JSON file, see [Define SAP Event Mesh Service Descriptor JSON File](Define_SAP_Event_Mesh_Service_Descriptor_JSON_File_5722fc4.md).



<a name="loiofddd26347b3e4c5397a31bc3ed507028__section_w3s_zcl_d4b"/>

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

1. Create an SAP Event Mesh service instance with service plan `default`.



</td>
<td>

-   [Create an SAP Event Mesh Service Instance in the Cloud Foundry Environment](Create_an_SAP_Event_Mesh_Service_Instance_in_the_Cloud_Foundry_Environment_c2d4d87.md)

-   [Create an SAP Event Mesh Service Instance in the Kyma Environment](Create_an_SAP_Event_Mesh_Service_Instance_in_the_Kyma_Environment_3de02d2.md)




</td>
</tr>
<tr>
<td>

2. Define a dedicated JSON file that you add either when creating the SAP Event Mesh service instance, or after that.



</td>
<td>

 [Define SAP Event Mesh Service Descriptor JSON File](Define_SAP_Event_Mesh_Service_Descriptor_JSON_File_5722fc4.md) 



</td>
</tr>
<tr>
<td>

3. Create a queue in the message client that refers to the SAP Event Mesh service instance and then subscribe the topic of the namespace of the SAP S/4HANA Cloud Extensibility service to that queue.



</td>
<td>

 [Create Queues and Subscribe to Them](Create_Queues_and_Subscribe_to_Them_e54e609.md) 



</td>
</tr>
</table>

-   **[Create an SAP Event Mesh Service Instance in the Cloud Foundry Environment](Create_an_SAP_Event_Mesh_Service_Instance_in_the_Cloud_Foundry_Environment_c2d4d87.md "Use this procedure to enable the SAP Event
                                        Mesh service for the
		subaccount where your extension application will reside.")**  
Use this procedure to enable the SAP Event Mesh service for the subaccount where your extension application will reside.
-   **[Create an SAP Event Mesh Service Instance in the Kyma Environment](Create_an_SAP_Event_Mesh_Service_Instance_in_the_Kyma_Environment_3de02d2.md "Use this procedure to enable the SAP Event
                                        Mesh service for the
		subaccount where your extension application will reside.")**  
Use this procedure to enable the SAP Event Mesh service for the subaccount where your extension application will reside.
-   **[Define SAP Event Mesh Service Descriptor JSON File](Define_SAP_Event_Mesh_Service_Descriptor_JSON_File_5722fc4.md "The SAP Event
                                        Mesh service descriptor defines details of a
        message client and needs to be provided when provisioning new SAP Event
                                        Mesh service
        instances with service plan default.")**  
The SAP Event Mesh service descriptor defines details of a message client and needs to be provided when provisioning new SAP Event Mesh service instances with service plan `default`.
-   **[Create Queues and Subscribe to Them](Create_Queues_and_Subscribe_to_Them_e54e609.md "")**  


