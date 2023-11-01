<!-- loioe2c250dc5abd468a81f4f619206157a2 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Managing Resource Providers

SAP BTP allows you to connect your global account in the SAP BTP cockpit to your provider account from a non-SAP cloud vendor, and consume remote service resources that you already own and which are supported by SAP through this channel.

> ### Note:  
> The use of this functionality is subject to the availability of the supported non-SAP cloud vendors in your country or region.



## Context

For example, if you are subscribed to Amazon Web Services \(AWS\) and have already purchased services, such as PostgreSQL, you can register the vendor as a resource provider in SAP BTP and consume this service across your subaccounts together with other services offered by SAP.

SAP BTP currently supports the following vendors and their consumable services:


<table>
<tr>
<th valign="top">

Cloud Vendor

</th>
<th valign="top">

Supported Services

</th>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Amazon Relational Database Service \(RDS\) - PostgreSQL

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

Azure Database for PostgreSQL

</td>
</tr>
</table>

More information: [PostgreSQL on SAP BTP - Product Documentation](https://help.sap.com/viewer/product/PostgreSQL/Cloud/en-US) 

<a name="task_mjl_zgl_g3b"/>

<!-- task\_mjl\_zgl\_g3b -->

## Configure a New Resource Provider



<a name="task_mjl_zgl_g3b__context_njl_zgl_g3b"/>

## Context

To consume the resources provisioned by your provider account, you need to first create a resource provider instance in the cockpit.



<a name="task_mjl_zgl_g3b__steps_ojl_zgl_g3b"/>

## Procedure

1.  Navigate to your global account in the cockpit.

2.  Choose *Resource Providers* from the left hand-side navigation panel.

3.  Choose *New Provider*.

4.  Choose the provider from the list of supported vendors.

5.  Enter a display name for the provider.

    You can create more than one instance of a given resource provider, each with its unique configuration properties. In such cases, the display name \(and technical name\) should be descriptive enough so that you and developers can easily differentiate between each instance.

6.  Enter a unique technical name for the provider.

    The technical name can contain only letters \(a-z\), digits \(0-9\), and underscore \(\_\) characters.

    This name can be used by developers as a parameter when creating service instances from this provider.

    > ### Note:  
    > After you save the settings for the resource provider, you cannot change its technical name.

7.  Choose either *Manually enter provider configuration properties* or *Add provider configuration properties by JSON file*, depending on how you prefer to provide the necessary configuration properties for the given provider.

    > ### Tip:  
    > Each supported vendor has its own unique configuration properties. The *New Resource Provider* form provides a description of each property and indicates whether they are mandatory or optional.

    If you choose to configure the properties by uploading a JSON file, which is typically provided by the vendor, make sure that the file contains the required configuration properties for connecting to the provider, and is correctly formatted.

    > ### Sample Code:  
    > Sample JSON for configuring Amazon Web Services \(AWS\) as a resource provider:
    > 
    > ```
    > {
    > “access_key_id”: “AWSACCESSKEY”,
    > “secret_access_key”: “SECRETKEY”,
    > “vpc_id”: “vpc-test”,
    > “region”: “eu-central-1”
    > }
    > 
    > ```

8.  Save your changes.

    The new resource provider is added to the resource providers table.




<a name="task_mjl_zgl_g3b__result_rtf_cys_g3b"/>

## Results

After you configure a new resource provider, its supported services are added as entitlements in your global account. In the *Entitlements* page in the cockpit, you can then allocate the required services and quotas to the relevant directories and subaccounts in your global account.

<a name="task_vvv_12l_3cb"/>

<!-- task\_vvv\_12l\_3cb -->

## Manage Resource Providers and Service Entitlements



<a name="task_vvv_12l_3cb__context_szl_vgl_g3b"/>

## Context

Follow these steps to manage the resource providers that you have already configured in the cockpit.



<a name="task_vvv_12l_3cb__steps_oyn_c2l_3cb"/>

## Procedure

1.  Navigate to your global account in the cockpit.

2.  Open the *Resource Providers* page.

    The page displays the resources providers that you have already configured.

3.  In the *Actions* columns, you can perform the following for each resource provider:


    <table>
    <tr>
    <th valign="top">

    Action
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    <span class="SAP-icons"></span>

    Manage Entitlements and Quotas
    
    </td>
    <td valign="top">
    
    View the subaccount entitlements and quotas of services that are consumed from a resource provider.

    This action opens the *Entitlements* \> *Service Assignments* page in the cockpit, and is prefiltered for the selected resource provider.

    > ### Tip:  
    > Whenever you need to manage assigned entitlements, you can navigate directly to the *Service Assignments* or *Subaccount Assignments* pages in the cockpit without going through the *Resource Providers* page.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    :pencil2:

    Edit Resource Provider
    
    </td>
    <td valign="top">
    
    Edit the display name, description, and configuration properties of a resource provider.

    > ### Note:  
    > You cannot change the technical name of a resource provider.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    :wastebasket:

    Delete
    
    </td>
    <td valign="top">
    
    Delete a resource provider.

    When you delete an existing resource provider, all the services offered by this instance of the resource provider will no longer be available on SAP BTP.

    > ### Note:  
    > You cannot delete a resource provider that already has service entitlements assigned to subaccounts in your global account. To delete the provider, you need to first remove its subaccount assignments in the *Subaccount Assignments* page.


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Configure Entitlements and Quotas for Subaccounts](configure-entitlements-and-quotas-for-subaccounts-5ba357b.md "Distribute the entitlements that are available in your global account by adding service plans and their allowed quotas to your subaccounts using the SAP BTP cockpit.")

