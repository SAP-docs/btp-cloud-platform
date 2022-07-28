<!-- loiof5bbc57845ef47bab40d0da3ec754e79 -->

# Configure Event Topics in SAP S/4HANA Cloud

Configure event topics for the channel inside the SAP S/4HANA Cloud tenant.



<a name="loiof5bbc57845ef47bab40d0da3ec754e79__prereq_a4p_d4t_b4b"/>

## Prerequisites

Уou have created the `SAP S/4HANA Cloud Extensibility` service instance in the Cloud Foundry or Kyma environment. See:

-   [Create an SAP S/4HANA Extensibility Service Instance in the Cloud Foundry Environment](create-an-sap-s-4hana-extensibility-service-instance-in-the-cloud-foundry-environment-531a909.md)

-   [Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment](create-an-sap-s-4hana-cloud-extensibility-service-instance-in-the-kyma-environment-55d876e.md)




## Context

After you have created the `SAP S/4HANA Cloud Extensibility` service instance, you need to configure event topics for the channel inside the SAP S/4HANA Cloud tenant, and then you need to create an SAP Event Mesh service instance for the application to consume SAP S/4HANA Cloud events.



## Procedure

1.  Configure event topics for the channel inside SAP S/4HANA Cloud tenant. Use the channel you have specified in SAP S/4HANA Cloud Extensibility service descriptor JSON file when configuring the parameters for the communication arrangement in SAP S4/HANA Cloud tenant.

    As an example, you can use the *sap/s4/beh/businesspartner/v1/BusinessPartner/Changed/v1* outbound topic.




<a name="loiof5bbc57845ef47bab40d0da3ec754e79__postreq_jjk_j3h_vhb"/>

## Next Steps

Create an SAP Event Mesh service instance in the Cloud Foundry or the Kyma environment. See:

-   [Create an SAP Event Mesh Service Instance in the Cloud Foundry Environment](create-an-sap-event-mesh-service-instance-in-the-cloud-foundry-environment-c2d4d87.md)

-   [Create an SAP Event Mesh Service Instance in the Kyma Environment](create-an-sap-event-mesh-service-instance-in-the-kyma-environment-3de02d2.md)


