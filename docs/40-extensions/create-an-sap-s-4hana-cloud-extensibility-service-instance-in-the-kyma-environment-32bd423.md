<!-- loio32bd4237bbc643f7a7c0b3e7aed13cc7 -->

# Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment



<a name="loio32bd4237bbc643f7a7c0b3e7aed13cc7__prereq_fms_2dv_5lb"/>

## Prerequisites

-   Before creating an SAP S/4HANA Cloud Extensibility service instance in the Kyma environment, see [Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](create-a-service-instance-to-consume-the-sap-s-4hana-cloud-apis-a735641.md).

-   Have the Kyma environment enabled for the subaccount you are using. See [Creating Kyma Instances](../50-administration-and-ops/creating-kyma-instances-09dd313.md).

-   Configure the roles in the Kyma environment. See [Assign Roles in the Kyma Environment](../60-security/assign-roles-in-the-kyma-environment-148ae38.md).

-   The SAP BTP Operator module is enabled. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c)

-   Have the entitlements of the SAP S/4HANA Cloud Extensibility service configured. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md).




<a name="loio32bd4237bbc643f7a7c0b3e7aed13cc7__context_b4x_ncv_5lb"/>

## Context

To consume the SAP S/4HANA Cloud APIs \(inbound connection\) or consume APIs exposed by the extension application from SAP S/4HANA Cloud \(outbound connection\), you create an SAP S/4HANA Cloud Extensibility service instance. When creating the service instance, you configure the communication arrangement and the authentication type for the connection.

For communication arrangements with inbound connections, a destination on a subaccount level with the same name as the service instance name is automatically created in this subaccount. It contains all instance binding properties which are sufficient to establish connection to the SAP S/4HANA Cloud system.

> ### Note:  
> Make sure that you don't already have a destination with the same name as the service instance. If you do, you will not be able to create the service instance.



## Procedure

1.  Navigate to the subaccount for which you want to create an SAP S/4HANA Cloud Extensibility service instance.

2.  On the subaccount *Overview* page, in the *Kyma Environment* section, open the Kyma dashboard.

3.  Choose *Namespaces* from the left-hand side navigation and open the namespace in which you want to create a service instance.

4.  Choose *Service Management* \> *Service Instances* from the left-hand side navigation.

5.  In the *Service Instances* page, choose *Create Service Instance* in the upper right-hand corner. A new dialog opens.

6.  Choose the *Simple* tab and fill in the following fields:

    -   Give a meaningful name of the new SAP S/4HANA Cloud Extensibility service instance.

    -   In the *Offering Name* field, enter `s4-hana-cloud`, which is the technical name of the SAP S/4HANA Cloud Extensibility service.

    -   In the *Plan Name* field, enter `api-access`.


7.  Choose the *YAML* tab.

    To define the communication arrangement and the authentication type for the API access, specify in *parameters:* in the *spec:* section, the parameters listed in this YAML file: [Communication Arrangement JSON/YAML File - Properties](communication-arrangement-json-yaml-file-properties-553a4c6.md).

    For specific examples, see [Communication Arrangement YAML File - Examples](communication-arrangement-yaml-file-examples-1ab9bf6.md).

8.  Choose *Create*.




<a name="loio32bd4237bbc643f7a7c0b3e7aed13cc7__postreq_adb_3v5_gmb"/>

## Next Steps

After creating the *SAP S/4HANA Cloud Extensibility* service instance, you must bind the instance to an application, and it will be assigned an access URL and credentials to the corresponding API. See [Using SAP BTP Services in the Kyma Environment](../30-development/using-sap-btp-services-in-the-kyma-environment-ea4dd81.md).

