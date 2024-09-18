<!-- loio272ca23a7ebf4532922b226dc0310c45 -->

# Enabling System Landscape for SAP Business Application Studio



<a name="loio272ca23a7ebf4532922b226dc0310c45__section_vzy_bz2_lcc"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

A registered SAP S/4HANA Cloud system in the SAP BTP cockpit can expose consumption bundles that contain APIs and events. You can easily discover and consume the APIs exposed by the SAP S/4HANA Cloud systems in your system landscape when you develop and extend applications on SAP BTP, Cloud Foundry environment, using SAP Business Application Studio. To do this, first you need to enable connectivity between your system landscape in SAP BTP cockpit and SAP Business Application Studio. The integration requires performing several configuration steps starting with configuration on a global account level, and then, configuration on a subaccount level.



<a name="loio272ca23a7ebf4532922b226dc0310c45__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have an SAP Business Application Studio subscription. See [Subscribe to SAP Business Application Studio](https://help.sap.com/docs/SAP%20Business%20Application%20Studio/9d1db9835307451daa8c930fbd9ab264/6331319fd9ea4f0ea5331e21df329539.html).




<a name="loio272ca23a7ebf4532922b226dc0310c45__section_tmz_zy2_lcc"/>

## Procedure

The following procedure outlines the steps you need to perform to consume the APIs of registered SAP S/4HANA Cloud systems within the SAP Business Application Studio.

1.  In the *System Landscape* page of SAP BTP cockpit, in the *Systems* tab, add and then register an SAP system of type *SAP S/4HANA Cloud*.

    To expose information about its APIs and events and show this information on the *System Landscape* page, an SAP system of type *SAP S/4HANA Cloud* must be registered in the SAP BTP cockpit. Only when registered, the system communicates information about its APIs and other technical details across the landscape. See [Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](extending-sap-s-4hana-cloud-in-the-cloud-foundry-and-kyma-environment-40b9e6c.md).

2.  In the *Formations* tab, create a formation of type *Developing with SAP Business Application Studio* and include the SAP Business Application Studio system and the SAP S/4HANA Cloud systems you want to expose in SAP Business Application Studio.

    > ### Note:  
    > In the formation type *Developing with SAP Business Application Studio*, you can include only SAP systems of type *SAP Business Application Studio* and *SAP S/4HANA Cloud*.

    To enable connectivity between given SAP systems of type *SAP S/4HANA Cloud* from the *System Landscape* page of SAP BTP cockpit and the SAP Business Application Studio, you must create a formation of the corresponding type and include the SAP S/4HANA Cloud systems in it. See [Including Systems in a Formation](including-systems-in-a-formation-68b04fa.md).

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
        
        The property identifies the consumption bundle and its APIs that are exposed by the SAP S/4HANA Cloud system. The destination also provides the required credentials to consume the bundle and use it for further development in the SAP Business Application Studio.
        
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
        
        All of the required properties of a given SAP S/4HANA Cloud system are accessible in the corresponding *System Details* section on the *System Landscape* page. See [Create a Destination](../30-development/create-a-destination-3fa7934.md) and [Configuring the Extension Application's Connectivity to SAP S/4HANA Cloud](configuring-the-extension-application-s-connectivity-to-sap-s-4hana-cloud-ef4b7ca.md).

    -   Create a destination automatically.

        Alternatively, the destination can be created automatically. You can do this, by creating a service instance of the SAP S/4HANA Cloud Extensibility service after you register an SAP S/4HANA Cloud system. See [Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](extending-sap-s-4hana-cloud-in-the-cloud-foundry-and-kyma-environment-40b9e6c.md) and [Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](create-a-service-instance-to-consume-the-sap-s-4hana-cloud-apis-a735641.md).





<a name="loio272ca23a7ebf4532922b226dc0310c45__section_cq1_15q_jvb"/>

## Next Steps

Develop applications on SAP BTP, Cloud Foundry environment using SAP Business Application Studio and the system landscape.

When you enable the connectivity, the SAP S/4HANA Cloud systems and their APIs are accessible in the SAP Business Application Studio. Next you can use the APIs to develop new or extend the existing functionality with the help of SAP Business Application Studio. See [Unified Customer Landscape Service Provider](https://help.sap.com/docs/SAP%20Business%20Application%20Studio/daa8adb7947848d8af8fc62e838e830e/830adebf4ab3470c9c3278188ceef8a1.html).

