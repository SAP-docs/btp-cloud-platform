<!-- loiof371f81d06c64a0fb507307c9ad24646 -->

# Create an SAP SuccessFactors Extensibility Service Instance in the Kyma Environment



<a name="loiof371f81d06c64a0fb507307c9ad24646__prereq_fms_2dv_5lb"/>

## Prerequisites

-   Before creating an SAP SuccessFactors Extensibility service instance in the Kyma environment, see [Create a Service Instance to Consume the SAP SuccessFactors HXM Suite OData API](Create_a_Service_Instance_to_Consume_the_SAP_SuccessFactors_HXM_Suite_OData_API_46c5ea1.md).

-   Configure the roles in the Kyma environment. See [Roles in the Kyma Environment](../50-administration-and-ops/Roles_in_the_Kyma_Environment_148ae38.md).

-   Have the Kyma environment enabled for the subaccount you are using. See [Create the Kyma Environment Instance](../50-administration-and-ops/Create_the_Kyma_Environment_Instance_09dd313.md).

-   Have the entitlements of the SAP SuccessFactors Extensibility service configured. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](Configure_the_Entitlements_for_the_SAP_S4HANA_Cloud_Extensibility_Service_65ad330.md).




## Context

During the creation of the service instance, a destination on the subaccount level with the same name as the service instance name is automatically created in this subaccount. It contains all instance binding properties which are sufficient to establish connection to the SAP SuccessFactors system.

> ### Note:  
> Make sure that you don't already have a destination with the same name as the service instance. If you do, you will not be able to create the service instance.



<a name="loiof371f81d06c64a0fb507307c9ad24646__steps_uws_wlh_vlb"/>

## Procedure

1.  Navigate to the subaccount for which you want to create an SAP SuccessFactors Extensibility service instance.

2.  On the subaccount *Overview* page, in the *Kyma Environment* section, open the Kyma Console.

3.  Choose *Namespaces* from the left-hand side navigation and open the *default* Namespace.

4.  Choose *Catalog* from the left-hand side navigation.

5.  In the *Services* tab, search for the *SAP SuccessFactors Extensibility* tile.

6.  Open the *SAP SuccessFactors Extensibility* tile and choose *Add* in the upper right-hand corner. A new dialog opens.

7.  Fill in the fields of the SAP SuccessFactors cluster service class:

    -   Give a meaningful name of the new cluster service class.

    -   Select the *api-access* plan.

    -   Choose *Add parameters*.

    -   To define the authentication type for the API access, specify a JSON file or specify parameters in the JSON format. For more information about the structure of the JSON file, see [Authentication Type JSON File](Authentication_Type_JSON_File_543fbd6.md).

    -   Choose *Create*.





<a name="loiof371f81d06c64a0fb507307c9ad24646__postreq_adb_3v5_gmb"/>

## Next Steps

After creating the *SAP SuccessFactors Extensibility* service instance, you have to bind the instance to an application, and it will be assigned an access URL and credentials to the corresponding API. See [Binding Service Instances to Applications](../30-development/Binding_Service_Instances_to_Applications_d1aa23c.md).

