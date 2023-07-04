<!-- loio3de02d29be5e4fedabe84d5fdb4dc924 -->

# Create an SAP Event Mesh Service Instance in the Kyma Environment

Use this procedure to enable the SAP Event Mesh service for the subaccount where your extension application will reside.



<a name="loio3de02d29be5e4fedabe84d5fdb4dc924__prereq_mbc_zvk_1nb"/>

## Prerequisites

-   In the SAP BTP cockpit, you have assigned the `messaging` SAP S/4HANA Cloud Extensibility service plan to the SAP BTP subaccount that you want to pair with the SAP S/4HANA Cloud tenant. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md).

-   In the Kyma Dashboard, you have created the SAP S/4HANA Cloud Extensibility service instance with the `messaging` plan. See [Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment](create-an-sap-s-4hana-cloud-extensibility-service-instance-in-the-kyma-environment-55d876e.md).

-   In the SAP BTP cockpit, you have assigned the `default` SAP Event Mesh service plan to the SAP BTP subaccount that you want to pair with the SAP S/4HANA Cloud tenant. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md).




## Context

In the Kyma Dashboard, create an instance of the SAP Event Mesh service. This instance will specify the details of the namespace that you created in SAP Event Mesh for the SAP S/4HANA Cloud Extensibility service instance with the `default` plan. This way, you are setting up a contract between SAP Event Mesh and the Kyma environment, and connect them to enable seamless event flow from the given SAP S/4HANA Cloud tenant to Kyma.



<a name="loio3de02d29be5e4fedabe84d5fdb4dc924__steps_nqw_ngm_lhb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount for which you want to create an SAP Event Mesh service instance.

2.  On the subaccount *Overview* page in the *Kyma Environment* section, open the Kyma Dashboard.

3.  Navigate to the *default* namespace from the drop-down list in the top navigation.

4.  Choose *Service Management* \> *BTP Service Instances* from the left-hand side navigation.

5.  In the *Service Instances* page, choose *Create Service Instance* in the upper right-hand corner. A new dialog opens.

6.  Choose the *Simple* tab and fill in the following fields:

    -   Give a meaningful name of the new SAP Event Mesh service instance.

    -   In the *Offering Name* field, enter `enterprise-messaging`, which is the technical name of the SAP Event Mesh service.

    -   In the *Plan Name* field, enter `default`.


7.  Choose the *YAML* tab.

    In *parameters:* in the *spec:* section, specify the parameters to define the details of your message client in the SAP Event Mesh service. You must include the `subscribeFilter` parameter which specifies the `sap/S4HANAOD/{emClientId}` namespace you created for the SAP S/4 HANA Cloud Extensibility instance of the `messaging` plan in SAP Event Mesh. For more information about the structure of the YAML file, see [Define SAP Event Mesh Service Descriptor JSON/YAML File](define-sap-event-mesh-service-descriptor-json-yaml-file-5722fc4.md).

8.  Choose *Create*.




<a name="loio3de02d29be5e4fedabe84d5fdb4dc924__result_fh1_mhj_5pb"/>

## Results

Once the service instance is provisioned, you can see it under *Service Management* \> *Instances* in the left-hand side navigation of the Kyma Dashboard.



<a name="loio3de02d29be5e4fedabe84d5fdb4dc924__postreq_jjk_j3h_vhb"/>

## Next Steps

[Create Queues and Subscribe to Them](create-queues-and-subscribe-to-them-e54e609.md)

