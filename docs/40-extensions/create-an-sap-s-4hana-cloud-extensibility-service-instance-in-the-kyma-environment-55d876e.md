<!-- loio55d876e1d63b4955bd57fbb842a89f92 -->

# Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment

Use this procedure to configure the communication between SAP S/4HANA Cloud and SAP Event Mesh in the Kyma environment.



<a name="loio55d876e1d63b4955bd57fbb842a89f92__prereq_mbc_zvk_1nb"/>

## Prerequisites

In the SAP BTP cockpit, you have assigned the `messaging` SAP S/4HANA Cloud service plan to the subaccount you want to pair with the SAP S/4HANA Cloud tenant. See [Configure the Entitlements for the SAP BTP Subaccount](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md).



## Context

To configure the connectivity between an SAP S/4HANA Cloud tenant and Event Mesh and to enable the exchange of credentials between the two systems, you first need to create an SAP S/4HANA Cloud Extensibility service instance with `messaging` service plan in the Kyma Dashboard. For more information about the `messaging` service plan, see [Supported Service Plans for SAP S/4HANA Cloud](supported-service-plans-for-sap-s-4hana-cloud-925c00a.md).

When creating this service instance, you create the required configurations in both the SAP S/4HANA Cloud tenant and the Event Mesh system associated with the subaccount in SAP BTP, so that the events can flow from one system to the other.



<a name="loio55d876e1d63b4955bd57fbb842a89f92__steps_nqw_ngm_lhb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount for which you want to create an SAP S/4HANA Cloud Extensibility service instance.

2.  On the subaccount *Overview* page in the *Kyma Environment* section, open the Kyma Dashboard.

3.  Navigate to the *default* namespace from the drop-down list in the top navigation.

4.  Choose *Service Management* \> *BTP Service Instances* from the left-hand side navigation.

5.  In the *Service Instances* page, choose *Create Service Instance* in the upper right-hand corner. A new dialog opens.

6.  Choose the *Simple* tab and fill in the following fields:

    -   Give a meaningful name of the new SAP S/4HANA Cloud Extensibility service instance.

    -   In the *Offering Name* field, enter `s4-hana-cloud`, which is the technical name of the SAP S/4HANA Cloud Extensibility service.

    -   In the *Plan Name* field, enter `messaging`.


7.  Choose the *YAML* tab.

    In *parameters:* in the *spec:* section, specify the parameters to define the communication arrangement for the communication scenario *Enterprise Eventing Integration \(SAP\_COM\_0092\)* in the SAP S/4HANA Cloud tenant and to configure the parameters for the Event Mesh service. Make sure you include at least these two required parameters: `systemName` and `emclientId`. The parameters are listed in this YAML file: [Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON/YAML File](define-sap-s-4hana-cloud-extensibility-service-descriptor-json-yaml-file-2d50d91.md).

8.  Choose *Create*.




<a name="loio55d876e1d63b4955bd57fbb842a89f92__postreq_jjk_j3h_vhb"/>

## Next Steps

After creating the SAP S/4HANA Cloud Extensibility service instance with the `messaging` plan, a respective messaging client is created for you in the `sap/S4HANAOD/{emClientId}` namespace of the Event Mesh service. As the next step, you must relate the two clients \(SAP S/4HANA Cloud Extensibility and Event Mesh\) in the Kyma Dashboard. To do this, create an instance of the Event Mesh service with the details of the automatically created Event Mesh namespace. Follow the steps in [Create an SAP Event Mesh Service Instance in the Kyma Environment](create-an-sap-event-mesh-service-instance-in-the-kyma-environment-3de02d2.md).

