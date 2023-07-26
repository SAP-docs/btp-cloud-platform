<!-- loio13c0366d40aa42dfb94939bdb711f472 -->

# Set Up the Connectivity Between Event Mesh and the SAP S/4HANA Cloud Tenant



<a name="loio13c0366d40aa42dfb94939bdb711f472__section_cjq_hc3_qnb"/>

## Overview

To configure the connectivity between the SAP S/4HANA Cloud tenant and SAP Event Mesh and to enable the exchange of credentials between the two systems, you first need to create an *SAP S/4HANA Cloud Extensibility* service instance with service plan `messaging`. For more information about the `messaging` service plan, see [Supported Service Plans for SAP S/4HANA Cloud](supported-service-plans-for-sap-s-4hana-cloud-925c00a.md).

When creating this service instance, you create the required configurations in both the SAP S/4HANA Cloud tenant and theEvent Mesh system associated with the subaccount in SAP BTP, so that events can flow. Depending on the SAP BTP environment, to create an `SAP S/4HANA Cloud Extensibility` service instance, you have to choose one of the following options:

-   [Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment](create-an-sap-s-4hana-extensibility-service-instance-in-the-cloud-foundry-environment-531a909.md)

-   [Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment](create-an-sap-s-4hana-cloud-extensibility-service-instance-in-the-kyma-environment-55d876e.md)


After you have created the `SAP S/4HANA Cloud Extensibility` service instance, either in the Cloud Foundry or Kyma environment, you need to configure event topics for the channel inside the SAP S/4HANA Cloud tenant, and then you need to create an SAP Event Mesh service instance, respectively in the Cloud Foundry or Kyma environment, for the application to consume SAP S/4HANA Cloud events. You do this in a dedicated JSON file that you add either when creating the service instance, or after that. To construct this JSON file, see [Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON/YAML File](define-sap-s-4hana-cloud-extensibility-service-descriptor-json-yaml-file-2d50d91.md).



<a name="loio13c0366d40aa42dfb94939bdb711f472__section_w3s_zcl_d4b"/>

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

1. Create an `SAP S/4HANA Cloud Extensibility` service instance with service plan `messaging`.



</td>
<td valign="top">

-   [Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment](create-an-sap-s-4hana-extensibility-service-instance-in-the-cloud-foundry-environment-531a909.md)

-   [Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment](create-an-sap-s-4hana-cloud-extensibility-service-instance-in-the-kyma-environment-55d876e.md)




</td>
</tr>
<tr>
<td valign="top">

2. Define a dedicated JSON file that you add either when creating the `SAP S/4HANA Cloud Extensibility` service instance, or after that.



</td>
<td valign="top">

[Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON/YAML File](define-sap-s-4hana-cloud-extensibility-service-descriptor-json-yaml-file-2d50d91.md) 



</td>
</tr>
<tr>
<td valign="top">

3. Configure event topics for the channel inside SAP S/4HANA Cloud tenant.



</td>
<td valign="top">

[Configure Event Topics in SAP S/4HANA Cloud](configure-event-topics-in-sap-s-4hana-cloud-f5bbc57.md) 



</td>
</tr>
</table>

