<!-- loio7890ffa8a7274ac1852b37ede5b773d1 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Updating an ABAP System

Learn how to update your ABAP environment instance or change its service plan.



## Context



### Update the Properties of Your ABAP environment Instance

After you have created an ABAP environment instance, you can change the following properties:

-   ABAP System Description

-   Total ABAP Runtime Size \(size\_of\_runtime\)

-   ABAP Runtime Size per Application Server \(application\_server\_size\)

-   Elastic Scaling of the ABAP Application Server

-   HANA Cloud Memory Size \(size\_of\_persistence\)

-   HANA Cloud Disk Size \(size\_of\_persistence\_disk\)


> ### Note:  
> The updates are done with zero downtime, except for the HANA database resizing, which is performed with near zero downtime. This means that the database is inaccessible for only a few seconds.

> ### Tip:  
> To **change the initial admin**, you have to use the *Maintain Employees* SAP Fiori app. See [Maintain Employees](../50-administration-and-ops/maintain-employees-e882b0f.md).

> ### Restriction:  
> The following restrictions apply when resizing the HANA Cloud database:
> 
> -   Memory downsizing is limited to the minimum amount of memory required for a stable performance of the database. Before the memory size is decreased, an automatic SQL query \(as described in [SAP HANA Database Downsizing](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-administration-guide/sap-hana-database-downsizing)\) verifies that sufficient memory is available before downsizing.
> 
> -   The memory size cannot be decreased while a system is stopped. To decrease the memory size of a stopped instance, the instance has to be started via the `Landscape Portal` first.
> 
> -   The disk size can only be increased, not decreased.
> 
> -   Both memory and disk size can only be resized once every 24 hours.



### Interdependencies Between HANA Cloud Memory and Disk Sizes

****


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

When increasing memory

</th>
<th valign="top">

When decreasing memory

</th>
</tr>
<tr>
<td valign="top">

**Disk size = auto**

</td>
<td valign="top">

If the current disk size is below the new minimum, it's automatically increased.

</td>
<td valign="top" rowspan="2">

The disk size stays at its current value, even if it exceeds the new maximum disk size.

</td>
</tr>
<tr>
<td valign="top">

**Disk size unchanged \(fixed value\)**

</td>
<td valign="top">

The disk size must be at least equal to the new minimum disk size.

</td>
</tr>
<tr>
<td valign="top">

**Disk size increased**

</td>
<td valign="top" colspan="2">

The new disk size must be within the new minimum-maximum range.

</td>
</tr>
</table>

> ### Note:  
> The minimum and maximum disk sizes \(`size_of_persistence_disk`\) are defined by the memory size \(`size_of_persistence`\) as follows:
> 
> -   `min(size_of_persistence_disk) = 40 * size_of_persistence + 40`
> 
> -   `max(size_of_persistence_disk) = 240 * size_of_persistence + 40`
> 
> 
> Each GB above the \(new\) minimum disk size consumes 0.002 HANA compute units \(HCU\) of your quota.



### Change the Service Plan of Your ABAP environment Instance

You can update the service plan from one ABAP environment service plan to another. For example: once you've reached the limits of the free plan, you can upgrade the free service plan to a paid plan \(standard plan or build-runtime plan\). You could also update your standard plan to a build-runtime plan if you have a SAP Build subscription that includes quota for the ABAP environment service.

> ### Note:  
> To update the ABAP environment to a paid service plan, you first need to configure entitlements and quotas for the ABAP environment. You need at least the following entitlements assigned to your subaccount:
> 
> -   service plan: standard or build-runtime \(service ABAP Environment\)
> 
> -   quota plans:
> 
>     -   1 abap\_compute\_unit
> 
>     -   2 hana\_compute\_unit
> 
> 
> 
> For more information, see [Increasing the Quota for the ABAP Environment](increasing-the-quota-for-the-abap-environment-c40cb18.md).

> ### Restriction:  
> It's not possible to switch from a paid plan to a free plan.



## Procedure

1.  In the SAP BTP cockpit, choose your Cloud Foundry subaccount and navigate to the space in which you have created your ABAP environment instance. See [Navigate in the Cockpit](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/0874895f1f78459f9517da55a11ffebd.html).
2.  Make sure that you have the Space Developer role in the service instance's space:
    -   Go to *Space Members* and check if your user is listed there
    -   If you're not listed as a member, add yourself as a *Space Developer*. For more information, see [Add Space Members](https://help.sap.com/docs/btp/sap-business-technology-platform/add-space-members-using-cockpit?version=Cloud)

3.  From the navigation area, choose *Services* \> *Instances*.

    You see a list of all instances that have been created.

4.  Select your *ABAP environment* instance and choose *Update* by clicking on <span class="SAP-icons-V5"></span> \(Actions\) at the end of the row. If you'd like to check the values that are currently configured first, please select *View Parameters* instead.
5.  In the *Update Instance* wizard, you can either
    -   update the parameters listed above. See [Increasing the Quota for the ABAP Environment](increasing-the-quota-for-the-abap-environment-c40cb18.md). The currently configured values are prefilled in the *Update Wizard*, so you can keep the values that you don’t want to change as they are
    -   or change the plan to a new service plan. The following changes are possible:
        -   From free to standard
        -   From free to build-runtime
        -   From standard to build-runtime


6.  Choose *Update Instance* to save your changes.



Your ABAP environment instance is being updated. This might take a while.

