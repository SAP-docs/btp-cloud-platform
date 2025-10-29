<!-- loio0751a246cbe942188ee1e986e5c5c545 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Migrating Cloud Foundry Environment Instance to SAP Build

Update your Cloud Foundry environment instance to migrate it to the build runtime plan.



## Prerequisites

-   You're using an enterprise global account. For more information, see [Enterprise Accounts](../10-concepts/enterprise-accounts-171511c.md).

-   You're a subaccount administrator. For more information, see [Find Users and Their Role Collection Assignments](find-users-and-their-role-collection-assignments-870533e.md).

-   The following entitlement has been assigned to your subaccount:


    <table>
    <tr>
    <th valign="top">

    Service
    
    </th>
    <th valign="top">

    Technical Name
    
    </th>
    <th valign="top">

    Service Plan
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Cloud Foundry Environment
    
    </td>
    <td valign="top">
    
    `cloudfoundry`
    
    </td>
    <td valign="top">
    
    `build-runtime`
    
    </td>
    </tr>
    </table>
    
    For more information, see [Upgrading your service to the build-default or build-runtime plan](https://help.sap.com/docs/build-service/build-service-guide/changing-service-plans?version=Cloud#upgrading-your-service-to-the-build-default-or-build-runtime-plan).

-   In your subaccount, there's an active instance of the Cloud Foundry environment that uses one of the following plans:
    -   `standard`: see [Standard Plan for Cloud Foundry Runtime](https://help.sap.com/viewer/4287333baaa6413a8ece0a8ed1196af4/Cloud/en-US/102df6e2c3e74e4ea6c8067809a03a7e.html "Learn how to set up the standard plan for SAP BTP, Cloud Foundry runtime in enterprise global accounts.") :arrow_upper_right:
    -   `free`: see [Free Plan for Cloud Foundry Runtime](https://help.sap.com/viewer/4287333baaa6413a8ece0a8ed1196af4/Cloud/en-US/5f4a816f349f46a9b792df000be32117.html "Learn how to set up the free tier plan available for SAP BTP, Cloud Foundry runtime in an enterprise global account that uses the consumption-based commercial model.") :arrow_upper_right:
    -   `build-code`: see [What Is SAP Build Code](https://help.sap.com/docs/build_code/d0d8f5bfc3d640478854e6f4e7c7584a/504854f457cc4fbf9f79136dbc773618.html)




## Context

Here are the possible options for migrating your Cloud Foundry environment instance to SAP Build:

-   `standard` \(together with `MEMORY`\) → `build-runtime`
-   `free` → `build-runtime`
-   `build-code` → `build-runtime`

For more information, see [What Is SAP Build](https://help.sap.com/docs/build-service/build-service-guide/what-is-sap-build?version=Cloud).

> ### Note:  
> When you migrate to the `build-runtime` plan, 400 GB of runtime memory are automatically assigned to your subaccount. This value overwrites any original runtime memory assignment and can't be changed.



## Procedure

> ### Caution:  
> The migration procedure is irreversible. You can't move the Cloud Foundry environment instance back to your original plan after switching to `build-runtime`.

1.  Log in to your global account in the SAP BTP cockpit.

2.  Go to your subaccount and choose *Instances and Subscriptions*.

3.  Under *Environments*, find your Cloud Foundry environment instance and do the following:

    1.  Choose the <span class="SAP-icons-V5"></span> Actions icon on the right.

    2.  Choose *Update*.

    3.  In the drop-down list *Plan*, select `build-runtime`.

    4.  Check the box with a warning that has appeared.

    5.  Choose *Update Instance*.


4.  Wait for your Cloud Foundry environment instance to update.




## Results

If the status of your Cloud Foundry environment instance after the procedure is *Created*, you've successfully migrated the instance to SAP Build.

> ### Note:  
> After the migration, the runtime memory consumption of your Cloud Foundry environment instance is going to be reflected in the *SAP Build - Cloud Foundry Runtime* plan, instead of its original plan. The consumption of the SAP Build capacity units is going to be reflected in the *SAP Build - Runtime* plan.

**Related Information**  


[Service Plans and Metering for Cloud Foundry Runtime](../10-concepts/service-plans-and-metering-for-cloud-foundry-runtime-8d41fa4.md "This page explains the relationship between the service plans in the SAP Discovery Center and those in the SAP BTP cockpit, and provides information to help you understand how the service is billed.")

