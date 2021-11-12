<!-- loio32bd4237bbc643f7a7c0b3e7aed13cc7 -->

# Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment



<a name="loio32bd4237bbc643f7a7c0b3e7aed13cc7__prereq_fms_2dv_5lb"/>

## Prerequisites

-   Before creating an SAP S/4HANA Cloud Extensibility service instance in the Kyma environment, see [Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](Create_a_Service_Instance_to_Consume_the_SAP_S4HANA_Cloud_APIs_a735641.md).

-   Configure the roles in the Kyma environment. See [Assign Roles in the Kyma Environment](../50-administration-and-ops/Assign_Roles_in_the_Kyma_Environment_148ae38.md).

-   Have the Kyma environment enabled for the subaccount you are using. See [Create the Kyma Environment Instance](../50-administration-and-ops/Create_the_Kyma_Environment_Instance_09dd313.md).

-   Have the entitlements of the SAP S/4HANA Cloud Extensibility service configured. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](Configure_the_Entitlements_for_the_SAP_S4HANA_Cloud_Extensibility_Service_65ad330.md).




<a name="loio32bd4237bbc643f7a7c0b3e7aed13cc7__context_b4x_ncv_5lb"/>

## Context

During the creation of the service instance, a destination on a subaccount level with the same name as the service instance name is automatically created in this subaccount. It contains all instance binding properties which are sufficient to establish connection to the SAP S/4HANA Cloud system.

> ### Note:  
> Make sure that you don't already have a destination with the same name as the service instance. If you do, you will not be able to create the service instance.



## Procedure

1.  Navigate to the subaccount for which you want to create an SAP S/4HANA Cloud Extensibility service instance.

2.  On the subaccount *Overview* page, in the *Kyma Environment* section, open the Kyma Console.

3.  Choose *Namespaces* from the left hand-side navidation and open the *default* Namespace.

4.  Go to *Service Management* \> *Catalog* in the left-hand side navigation.

5.  In the *Services* tab, search for the *SAP S/4HANA Cloud Extensibility* tile.

6.  Open the *SAP S/4HANA Cloud Extensibility* tile and choose *Add* in the upper right-hand corner. A new dialog opens.

7.  Fill in the fields of the SAP S/4HANA Cloud cluster service class:

    -   Give a meaningful name of the new cluster service class.

    -   Select the *api-access* plan.

    -   Choose *Add parameters*.

    -   To define the communication arrangement and the authentication type for the API access, specify a JSON file or specify parameters in the JSON format. For more information about the structure of the JSON file, see [Communication Arrangement JSON File - Properties](Communication_Arrangement_JSON_File_-_Properties_553a4c6.md).

    -   Choose *Create*.





<a name="loio32bd4237bbc643f7a7c0b3e7aed13cc7__postreq_adb_3v5_gmb"/>

## Next Steps

After creating the *SAP S/4HANA Cloud Extensibility* service instance, you must bind the instance to an application, and it will be assigned an access URL and credentials to the corresponding API. See [Binding Service Instances to Applications](../30-development/Binding_Service_Instances_to_Applications_d1aa23c.md).

