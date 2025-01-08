<!-- loio642431173d3c4fabb7f5a155836903be -->

# Setting Up System Landscape for SAP Build



<a name="loio642431173d3c4fabb7f5a155836903be__section_yv3_cy2_lcc"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

A registered SAP S/4HANA Cloud system in the SAP BTP cockpit can expose consumption bundles that contain APIs and events. You can easily discover and consume the APIs exposed by the SAP S/4HANA Cloud systems in your system landscape when you develop and extend applications on SAP BTP, Cloud Foundry environment, using SAP Build. To do this, first you need to enable connectivity between your system landscape in SAP BTP cockpit and SAP Build. The integration requires performing several configuration steps starting with configuration on a global account level, and then, configuration on a subaccount level.

> ### Note:  
> This documentation refers to SAP S/4HANA Cloud Public Edition. See [Introduction to the Universe of SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).



<a name="loio642431173d3c4fabb7f5a155836903be__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have an SAP Build subscription.




<a name="loio642431173d3c4fabb7f5a155836903be__section_ij4_zx2_lcc"/>

## Procedure

The following procedure outlines the steps you need to perform to consume the APIs of registered SAP S/4HANA Cloud systems within SAP Build.

1.  Add and then register an SAP system of type *SAP S/4HANA Cloud* in the *System Landscape* \> *Systems* page of SAP BTP cockpit.

    To expose information about its APIs and events and show this information on the *Systems* page, an SAP system of type *SAP S/4HANA Cloud* must be registered in the SAP BTP cockpit. Only when registered, the system communicates information about its APIs and other technical details across the landscape. See [Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](extending-sap-s-4hana-cloud-in-the-cloud-foundry-and-kyma-environment-40b9e6c.md).

2.  In the *Formations* page, create a formation of type *Integration with SAP Build* and include the SAP Build system and the SAP S/4HANA Cloud systems you want to expose in SAP Build.

    > ### Note:  
    > In the formation type *Integration with SAP Build*, you can include only SAP systems of type *SAP Build* and *SAP S/4HANA Cloud*.

    To enable connectivity between given SAP systems of type *SAP S/4HANA Cloud* from the *Systems* page of SAP BTP cockpit and SAP Build, you must create a formation of the corresponding type and include the SAP S/4HANA Cloud systems in it. See [Automating Integrations Using Formations](automating-integrations-using-formations-68b04fa.md).

3.  Create a destination and make sure it has the corresponding system and consumption bundle properties.

    -   Create a destination manually.

        You can create the destination manually via the SAP Destination service page in SAP BTP cockpit by specifying one of the following additional properties variants in it.


        <table>
        <tr>
        <th valign="top">

        Additional Properties \(variant 1\)
        
        </th>
        <th valign="top">

        Additional Properties \(variant 2\)
        
        </th>
        <th valign="top">

        Description
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        `x-correlation-id` 
        
        </td>
        <td valign="top">
        
        `x-correlation-id` 
        
        </td>
        <td valign="top">
        
        The property identifies the consumption bundle and its APIs that are exposed by the SAP S/4HANA Cloud system. The destination also provides the required credentials to consume the bundle and use it for further development in SAP Build.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `x-system-id` 
        
        </td>
        <td valign="top">
        
        `x-system-name` 
        
        </td>
        <td valign="top" rowspan="2">
        
        Properties that uniquely identify the local tenant of the registered SAP S/4HANA Cloud system.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `x-system-type` 
        
        </td>
        <td valign="top">
        
        `x-system-base-url` 
        
        </td>
        </tr>
        </table>
        
        All of the required properties of a given SAP S/4HANA Cloud system are accessible in the corresponding *System Details* section on the *Systems* page. See [Create a Destination](../30-development/create-a-destination-3fa7934.md).

    -   Create a destination automatically.

        Alternatively, the destination can be created automatically. You can do this, by creating a service instance of the SAP S/4HANA Cloud Extensibility service after you register an SAP S/4HANA Cloud system. See [Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](extending-sap-s-4hana-cloud-in-the-cloud-foundry-and-kyma-environment-40b9e6c.md) and [Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](create-a-service-instance-to-consume-the-sap-s-4hana-cloud-apis-a735641.md).





<a name="loio642431173d3c4fabb7f5a155836903be__section_cq1_15q_jvb"/>

## Next Steps

Develop applications on SAP BTP, Cloud Foundry environment using SAP Build and the system landscape.

When you enable the connectivity, the SAP S/4HANA Cloud systems and their APIs are accessible in SAP Build. Next you can use the APIs to develop new or extend the existing functionality with the help of SAP Build.

**Related Information**  


[SAP Build Process Automation: Using SAP Systems](https://help.sap.com/docs/build-process-automation/sap-build-process-automation/using-sap-systems)

