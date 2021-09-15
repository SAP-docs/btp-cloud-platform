<!-- loio55d876e1d63b4955bd57fbb842a89f92 -->

# Create an SAP S/4HANA Extensibility Service Instance in the Kyma Environment

Use this procedure to configure the communication between SAP S/4HANA Cloud and SAP Event Mesh in the Kyma environment.



<a name="loio55d876e1d63b4955bd57fbb842a89f92__prereq_mbc_zvk_1nb"/>

## Prerequisites

In the SAP BTP cockpit, you have assigned the `messaging` SAP S/4HANA Cloud service plan to the subaccount you want to pair with the SAP S/4HANA Cloud tenant. See [Configure the Entitlements for the SAP BTP Subaccount](Configure_the_Entitlements_for_the_SAP_S4HANA_Cloud_Extensibility_Service_65ad330.md).



## Context

To configure the connectivity between an SAP S/4HANA Cloud tenant and Event Mesh and to enable the exchange of credentials between the two systems, you first need to create an SAP S/4HANA Cloud Extensibility service instance with `messaging` service plan in the Kyma Console. For more information about the `messaging` service plan, see [Supported Service Plans for SAP S/4HANA Cloud](Supported_Service_Plans_for_SAP_S4HANA_Cloud_925c00a.md).

When creating this service instance, you create the required configurations in both the SAP S/4HANA Cloud tenant and the Event Mesh system associated with the subaccount in SAP BTP, so that the events can flow from one system to the other.



<a name="loio55d876e1d63b4955bd57fbb842a89f92__steps_nqw_ngm_lhb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount for which you want to create an SAP S/4HANA Cloud Extensibility service instance.

2.  On the subaccount *Overview* page in the *Kyma Environment* section, open the Kyma Console.

3.  Navigate to the *default* namespace from the drop-down list in the top navigation.

4.  Go to *Service Management* \> *Catalog* in the left-hand side navigation.

5.  In the *Services* tab, search for *SAP S/4HANA Cloud Extensibility*.

6.  Open the *SAP S/4HANA Cloud Extensibility* tile and select *Add* in the upper right-hand corner.

7.  In the new dialog box that opens, fill in these fields for the SAP S/4HANA Cloud Extensibility cluster service class:

    -   Give a meaningful name for the new cluster service class.

    -   Select the `messaging` plan.

    -   Select *Add parameters*.

        Specify parameters in the JSON format to define the communication arrangement for the communication scenario *Enterprise Eventing Integration \(SAP\_COM\_0092\)* in the SAP S/4HANA Cloud tenant and to configure the parameters for the Event Mesh service. Make sure you include at least these two required parameters: `systemName` and `emclientId`. For more information about the structure of the JSON file, see [Define SAP S/4HANA Cloud Extensibility Service Descriptor JSON File](Define_SAP_S4HANA_Cloud_Extensibility_Service_Descriptor_JSON_File_2d50d91.md).

    -   Select *Create*.

        Once the service instance is provisioned, you can see it under *Service Management* \> *Instances* in the left-hand side navigation of the Kyma Console.




<a name="loio55d876e1d63b4955bd57fbb842a89f92__postreq_jjk_j3h_vhb"/>

## Next Steps

After creating the SAP S/4HANA Cloud Extensibility service instance with the `messaging` plan, a respective messaging client is created for you in the `sap/S4HANAOD/{emClientId}` namespace of the Event Mesh service. As the next step, you must relate the two clients \(SAP S/4HANA Cloud Extensibility and Event Mesh\) in the Kyma Console. To do this, create an instance of the Event Mesh service with the details of the automatically created Event Mesh namespace. Follow the steps in [Create an SAP Event Mesh Service Instance in the Kyma Environment](Create_an_SAP_Event_Mesh_Service_Instance_in_the_Kyma_Environment_3de02d2.md).

