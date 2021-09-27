<!-- loio3de02d29be5e4fedabe84d5fdb4dc924 -->

# Create an SAP Event Mesh Service Instance in the Kyma Environment

Use this procedure to enable the SAP Event Mesh service for the subaccount where your extension application will reside.



<a name="loio3de02d29be5e4fedabe84d5fdb4dc924__prereq_mbc_zvk_1nb"/>

## Prerequisites

-   In the SAP BTP cockpit, you have assigned the `messaging` SAP S/4HANA Cloud Extensibility service plan to the SAP BTP subaccount that you want to pair with the SAP S/4HANA Cloud tenant. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](Configure_the_Entitlements_for_the_SAP_S4HANA_Cloud_Extensibility_Service_65ad330.md).

-   In the Kyma Console, you have created the SAP S/4HANA Cloud Extensibility service instance with the `messaging` plan. See [Create an SAP S/4HANA Extensibility Service Instance in the Kyma Environment](Create_an_SAP_S4HANA_Extensibility_Service_Instance_in_the_Kyma_Environment_55d876e.md).

-   In the SAP BTP cockpit, you have assigned the `default` SAP Event Mesh service plan to the SAP BTP subaccount that you want to pair with the SAP S/4HANA Cloud tenant. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](Configure_the_Entitlements_for_the_SAP_S4HANA_Cloud_Extensibility_Service_65ad330.md).




## Context

In the Kyma Console, create an instance of the SAP Event Mesh service. This instance will specify the details of the namespace that you created in SAP Event Mesh for the SAP S/4HANA Cloud Extensibility service instance with the `default` plan. This way, you are setting up a contract between SAP Event Mesh and the Kyma environment, and connect them to enable seamless event flow from the given SAP S/4HANA Cloud tenant to Kyma.



<a name="loio3de02d29be5e4fedabe84d5fdb4dc924__steps_nqw_ngm_lhb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount for which you want to create an SAP S/4HANA Cloud Extensibility service instance.

2.  On the subaccount *Overview* page in the *Kyma Environment* section, open the Kyma Console.

3.  Navigate to the *default* namespace from the drop-down list in the top navigation.

4.  Go to *Service Management* \> *Catalog* in the left-hand side navigation.

5.  In the *Services* tab, search for *Event Mesh*.

6.  Open the *Event Mesh* tile and select *Add* in the upper right-hand corner.

7.  In the new dialog box that opens, fill in these fields for the SAP Event Mesh cluster service class:

    -   Give a meaningful name for the new cluster service class.

    -   Select the `default` plan.

    -   Select *Add parameters*.

        Specify parameters in the JSON format to define the details of your message client in the SAP Event Mesh service. You must include the `subscribeFilter` parameter which specifies the `sap/S4HANAOD/{emClientId}` namespace you created for the SAP S/4 HANA Cloud Extensibility instance of the `messaging` plan in SAP Event Mesh. For more information about the structure of the JSON file, see [Define SAP Event Mesh Service Descriptor JSON File](Define_SAP_Event_Mesh_Service_Descriptor_JSON_File_5722fc4.md).

    -   Select *Create*.




<a name="loio3de02d29be5e4fedabe84d5fdb4dc924__result_fh1_mhj_5pb"/>

## Results

Once the service instance is provisioned, you can see it under *Service Management* \> *Instances* in the left-hand side navigation of the Kyma Console.



<a name="loio3de02d29be5e4fedabe84d5fdb4dc924__postreq_jjk_j3h_vhb"/>

## Next Steps

[Create Queues and Subscribe to Them](Create_Queues_and_Subscribe_to_Them_e54e609.md)

