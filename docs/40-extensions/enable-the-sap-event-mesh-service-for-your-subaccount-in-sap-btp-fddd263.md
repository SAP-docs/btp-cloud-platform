<!-- loiofddd26347b3e4c5397a31bc3ed507028 -->

# Enable the SAP Event Mesh Service for Your Subaccount in SAP BTP



<a name="loiofddd26347b3e4c5397a31bc3ed507028__section_msh_5gl_d4b"/>

## Prerequisites

-   Уou have created the `SAP S/4HANA Cloud Extensibility` service instance in the Cloud Foundry or Kyma environment. See:

    -   [Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment](create-an-sap-s-4hana-extensibility-service-instance-in-the-cloud-foundry-environment-531a909.md)

    -   [Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment](create-an-sap-s-4hana-cloud-extensibility-service-instance-in-the-kyma-environment-55d876e.md)


-   You have configured event topics for the channel inside SAP S/4HANA Cloud tenant. See [Configure Event Topics in SAP S/4HANA Cloud](configure-event-topics-in-sap-s-4hana-cloud-f5bbc57.md).




<a name="loiofddd26347b3e4c5397a31bc3ed507028__section_bzw_1dj_qnb"/>

## Overview

To enable the SAP Event Mesh for your subaccount in SAP BTP, you have to create an instance of the SAP Event Mesh service with service plan `default`. This instance will specify the details of the namespace that you created in SAP Event Mesh for the SAP S/4HANA Cloud Extensibility service instance with the `messaging` plan. This way, you are setting up a contract between SAP Event Mesh and the Cloud Foundry, or the Kyma environment, and connect them to enable seamless event flow from the given SAP S/4HANA Cloud tenant.

Depending on the SAP BTP environment, to create an SAP Event Mesh service instance, you have to choose one of these:

-   [Create an SAP Event Mesh Service Instance in the Cloud Foundry Environment](create-an-sap-event-mesh-service-instance-in-the-cloud-foundry-environment-c2d4d87.md)

-   [Create an SAP Event Mesh Service Instance in the Kyma Environment](create-an-sap-event-mesh-service-instance-in-the-kyma-environment-3de02d2.md)


Define the details of your message client in SAP Event Mesh as parameters in a dedicated JSON file. To map the message client to the client defined in the SAP S/4HANA Cloud JSON file, in the SAP Event Mesh JSON file, you must include the `subscribeFilter` parameter which specifies the `sap/S4HANAOD/{emClientId}` namespace you created for the SAP S/4 HANA Cloud Extensibility instance of the `messaging` plan. For more information about the structure of the JSON file, see [Define SAP Event Mesh Service Descriptor JSON/YAML File](define-sap-event-mesh-service-descriptor-json-yaml-file-5722fc4.md).



<a name="loiofddd26347b3e4c5397a31bc3ed507028__section_w3s_zcl_d4b"/>

## Process Flow


<table>
<tr>
<th valign="top">

Process Step

</th>
<th valign="top">

Related Documentation

</th>
</tr>
<tr>
<td valign="top">

1. Create an SAP Event Mesh service instance with service plan `default`.

</td>
<td valign="top">

-   [Create an SAP Event Mesh Service Instance in the Cloud Foundry Environment](create-an-sap-event-mesh-service-instance-in-the-cloud-foundry-environment-c2d4d87.md)

-   [Create an SAP Event Mesh Service Instance in the Kyma Environment](create-an-sap-event-mesh-service-instance-in-the-kyma-environment-3de02d2.md)




</td>
</tr>
<tr>
<td valign="top">

2. Define a dedicated JSON file that you add either when creating the SAP Event Mesh service instance, or after that.

</td>
<td valign="top">

[Define SAP Event Mesh Service Descriptor JSON/YAML File](define-sap-event-mesh-service-descriptor-json-yaml-file-5722fc4.md) 

</td>
</tr>
<tr>
<td valign="top">

3. Create a queue in the message client that refers to the SAP Event Mesh service instance and then subscribe the topic of the namespace of the SAP S/4HANA Cloud Extensibility service to that queue.

</td>
<td valign="top">

[Create Queues and Subscribe to Them](create-queues-and-subscribe-to-them-e54e609.md) 

</td>
</tr>
</table>

