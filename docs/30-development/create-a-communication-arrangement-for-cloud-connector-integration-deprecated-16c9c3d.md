<!-- loio16c9c3d29c79484c9b7cc0560e08e770 -->

# Create a Communication Arrangement for Cloud Connector Integration \(Deprecated\)

Learn how to create a communication arrangement for communication scenario `SAP_COM_0200` to integrate the Cloud Connector.



<a name="loio16c9c3d29c79484c9b7cc0560e08e770__prereq_nzm_3hq_4gb"/>

## Prerequisites

> ### Note:  
> This procedure is deprecated and is only available for systems provisioned before May 2022. It was replaced with a scenario that does not require a Neo subaccount. To learn about the steps to migrate to a Cloud Foundry-only usage, see section **Next Steps** below.

To set up your ABAP environment, you have to create a communication arrangement for communication scenario **<code>SAP_COM_0200 - Cloud Connector Integration</code>**, that requires the following:

-   An administrative user in the ABAP environment tenant.
-   Increased quota for the ABAP runtime.
-   An ABAP service instance set up in Cloud Foundry.
-   Your Neo subaccount name.
-   The name of the region host of your Neo subaccount

    > ### Note:  
    > Please check out the supported Neo subaccounts for on-premise connectivity of the ABAP environment. See SAP Note [2765161](https://me.sap.com/notes/2765161).

-   Installation of Cloud Connector version 2.11 or higher. See [Cloud Connector: Installation](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/57ae3d62f63440f7952e57bfcef948d3.html)
-   Initial configuration for Cloud Connector and the Neo subaccount. See [Cloud Connector: Initial Configuration](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/db9170a7d97610148537d5a84bf79ba2.html)

    > ### Note:  
    > The Cloud Connector is connected to the Neo subaccount and is displayed in the Cloud Cockpit, section *Connectivity* under *Cloud Connectors*.

-   User credentials for the Cloud Connector admin role in the Neo subaccount



<a name="loio16c9c3d29c79484c9b7cc0560e08e770__ol_l5r_j2t_jz"/>

## Procedure

1.  To create a communication system that represents your Neo subaccount, open the *Communication Systems* app from the SAP Fiori launchpad in your Cloud Foundry subbaccount and select *New*.

2.  Provide a meaningful system name and choose *Create* to proceed.

    > ### Note:  
    > You have to disable the destination service first by using the *on/off* slider button.

    Enter the following information:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Host Name*
    
    </td>
    <td valign="top">
    
    Enter the name of the region host of your Neo subaccount.

    If your Neo URL is [https://account.xyz.hana.ondemand.com](https://account.xyz.hana.ondemand.com), you need to enter `xyz.hana.ondemand.com`, where `xyz` represents the region name. See [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loiod722f7cea9ec408b85db4c3dcba07b52).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *HTTPS Port*
    
    </td>
    <td valign="top">
    
    Enter `443`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Checkbox *Use Cloud Connector*
    
    </td>
    <td valign="top">
    
    Make sure this checkbox is **not checked** .
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    User for Outbound Communication
    
    </td>
    <td valign="top">
    
    a\) Scroll down to this section.

    b\) Add a new user.

    c\) In the dropdown list for *Authentication Method*, select a user name and password.

    d\) Enter the user name and password of the Cloud Connector admin user of the Neo subaccount.
    
    </td>
    </tr>
    </table>
    
    For more information on how to create a communication system, see [How to Create Communication Systems](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/LATEST/en-US/1bfe32ae08074b7186e375ab425fb114.html).

3.  Save the communication system to activate it.

4.  To create a communication arrangement that activates the connection to the Neo subaccount, open the *Maintain Communication Arrangements* app from the SAP Fiori Launchpad and click *New*.

5.  Select scenario `SAP_COM_0200` and enter a meaningful arrangement name.

6.  Click *Create* to proceed.

    Enter the following information:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Communication System*
    
    </td>
    <td valign="top">
    
    Enter the name of the communication system created in steps 1-3, or select it from the value help.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Additional Properties* \> *Account Name*
    
    </td>
    <td valign="top">
    
    Enter the name of your Neo subaccount.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Outbound Communication* \> *User Name*
    
    </td>
    <td valign="top">
    
     
    
    </td>
    </tr>
    </table>
    
    For more information on how to create a communication arrangement, see [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).

7.  Save the communication arrangement to activate it.

8.  Carry out the initial configuration for Cloud Connector and the Neo subaccount to make it operational for connections between your Neo subaccount and the on-premise systems.




<a name="loio16c9c3d29c79484c9b7cc0560e08e770__result_pfg_xj1_2hb"/>

## Results

You have associated the ABAP environment tenant with the Neo subaccount. This enables the ABAP environment tenant to request the Neo environment to open a tunnel connection.



<a name="loio16c9c3d29c79484c9b7cc0560e08e770__postreq_hjp_bp3_qgb"/>

## Next Steps

After completing the setup of communication scenario `SAP_COM_0200`, you are ready to set up your actual data connections between your ABAP environment and on-premise systems. This requires the configuration of other communication systems and communication arrangements in the ABAP environment tenant as well as the configuration of Cloud Connector. See [Enable On-Premise Connectivity](enable-on-premise-connectivity-9b6510e.md).

To **migrate** to the usage of the **Cloud Foundry Connectivity service**, proceed as follows:

1.  Configure trust in the Cloud Connector for the Cloud Foundry subaccount in which the ABAP instance resides.
2.  Delete communication arrangement `SAP_COM_0200`.
3.  Destinations do not need to be modified if the same `LocationID` is used.

