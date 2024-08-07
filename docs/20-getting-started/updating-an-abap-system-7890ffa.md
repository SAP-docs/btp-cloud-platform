<!-- loio7890ffa8a7274ac1852b37ede5b773d1 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Updating an ABAP System

Learn how to update your ABAP environment instance.



## Context

After you have created an ABAP environment instance, you can change the following properties:

-   ABAP System Description

-   Total ABAP Runtime Size \(size\_of\_runtime\)

-   ABAP Runtime Size per Application Server \(application\_server\_size\)

-   Elastic Scaling of the ABAP Application Server

-   HANA Cloud Memory Size \(size\_of\_persistence\)

-   HANA Cloud Disk Size \(size\_of\_persistence\_disk\)


> ### Note:  
> The updates of these properties are done without any downtime, or - in case of updating the HANA memory or disk size - with near zero downtime \(meaning that the database is not accessible for a few seconds only\).

To **change the initial admin**, you have to use the *Maintain Employees* SAP Fiori app. See [Maintain Employees](../50-administration-and-ops/maintain-employees-e882b0f.md).

To **update your system from a free to a standard plan**, see [Update to a Paid Service Plan](https://help.sap.com/docs/btp/sap-business-technology-platform/using-free-service-plans?version=Cloud#update-to-a-paid-service-plan). Make sure you have enough hana\_compute\_units and abap\_compute\_units available as quota in your subaccount before updating to a paid plan. For more information, see [Increasing the Quota for the ABAP Environment](increasing-the-quota-for-the-abap-environment-c40cb18.md).

> ### Restriction:  
> A downsizing of the HANA Cloud memory size is only possible down to the minimum amount of memory required for a stable performance of the HANA Cloud database. Before the memory size is decreased, an SQL query \(as described on [SAP HANA Database Downsizing](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-administration-guide/sap-hana-database-downsizing)\) is automatically run on the database to make sure the downsizing is possible based on the already consumed memory.
> 
> The HANA Cloud memory size cannot be decreased while a system is stopped. To decrease the HANA Cloud memory size of a stopped instance, the instance has to be started via the `Landscape Portal` first.
> 
> The HANA Cloud disk size can currently only be increased, and not decreased.
> 
> Both the HANA Cloud memory and the disk size can only be resized once every 24 hours.



## Procedure

1.  In the SAP BTP cockpit, choose your Cloud Foundry subaccount and navigate to the space, in which you have created your ABAP environment instance. See [Navigate in the Cockpit](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/0874895f1f78459f9517da55a11ffebd.html).

2.  From the navigation area, choose *Services* \> *Instances and Subscriptions*.

    You see a list of all instances that have been created.

3.  Select your *ABAP environment* instance and choose *Update* by clicking on <span class="SAP-icons-V5"></span> at the end of the row. If you'd like to check the values that are currently configured first, please select *View Parameters* instead.

4.  In the *Update Instance* wizard, you can update the parameters listed above. See [Increasing the Quota for the ABAP Environment](increasing-the-quota-for-the-abap-environment-c40cb18.md). The currently configured values are prefilled in the *Update Wizard*, so you can keep the values that you don’t want to change as they are.

5.  Choose *Update Instance* to save your changes.




<a name="loio7890ffa8a7274ac1852b37ede5b773d1__result_zgb_jqd_q4b"/>

## Results

Your ABAP environment instance is being updated. This might take a while.

