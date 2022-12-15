<!-- loio50b32f144e184154987a06e4b55ce447 -->

# Creating an ABAP System

Create a service instance for the ABAP environment from the Service Marketplace.



<a name="loio50b32f144e184154987a06e4b55ce447__prereq_cbh_1ft_r4b"/>

## Prerequisites

You have increased the quota for the ABAP environment. See [Increasing the Quota for the ABAP Environment](increasing-the-quota-for-the-abap-environment-c40cb18.md).



<a name="loio50b32f144e184154987a06e4b55ce447__context_bck_rbn_q2b"/>

## Context

> ### Note:  
> If you have run the booster *Prepare an Account for ABAP Development*, you can also skip this step.

For more information about creating service instances, see [Create Service Instances Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8221b7434d8e484fab5ec5d219b7bf64.html).



## Procedure

1.  Log on to the SAP BTP cockpit and navigate to the Cloud Foundry subaccount. See [Navigate in the Cockpit](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/0874895f1f78459f9517da55a11ffebd.html).

2.  From the navigation area, choose *Services* \> *Service Marketplace.* 

    You see a list of all services that are available to you.

3.  Choose *ABAP environment*.

4.  Choose *Create*.

    A wizard opens that helps you create your instance.

    > ### Tip:  
    > To see a list of all instances that have already been created in your subaccount, choose *Services* \> *Instances and Subscriptions* from the navigation area. Here, you can also create a new ABAP environment instance.

5.  Select the `standard` service plan.

6.  Choose *Cloud Foundry* as your runtime environment.

7.  Select a space.

8.  Enter a CLI-friendly instance name, and choose *Next*.

    The instance name identifies the service instance in the Cloud Foundry environment. Specify an instance name that is unique among all the service instances in a space and only contains alphanumeric characters \(A-Z, a-z\), periods, underscores, and hyphens.

9.  Provide additional instance parameters for the configuration by either using the default **form** or by uploading a **JSON file** from your computer or by specifying the parameters in JSON format.

    > ### Note:  
    > The admin email address is used to create the initial user for the ABAP system automatically, including the assignment of the administrator role to this user. You can access the ABAP environment system only with this specified user.
    > 
    > The ABAP system description is optional.
    > 
    > The Development System checkbox is checked by default. By using this setting, you can control the changeability of development objects in the system. If you want to protect all your customer-related software components and ABAP namespaces against manual changes via ABAP Development Tools, uncheck the box. This setting is used for test and productive systems, where changes must be imported only.
    > 
    > The ABAP system ID must consist of exactly three alphanumeric characters. Only uppercase letters are allowed. The first character must be a letter \(not a digit\). The ID does not have to be technically unique.
    > 
    > ABAP runtime size \(parameter `size_of_runtime`\) refers to the size of the ABAP runtime. It's part of the quota plan *abap\_compute\_unit*, with one ABAP compute unit representing 16 GB. The supported number of abap\_compute\_unit is 1, 2, 4, 6, 8, 16, or 32. For more information, see[ABAP Compute Units](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/7d1caa87c4b34366a7cf1b00a93199e2.html)
    > 
    > HANA memory size \(parameter `size_of_persistence`\) refers to the size of SAP HANA memory. It's part of the quota plan *hana\_compute\_unit*, with one HANA compute unit representing the suitable block size for the underlying SAP HANA Cloud instance \(15 GB on AWS\). The supported number of hana\_compute\_unit per HANA instance is 2, 4, 8, 16, 32, or 64.
    > 
    > Make sure that you don't choose more compute units than you have assigned to your subaccount for the ABAP environment \(see [Increasing the Quota for the ABAP Environment](increasing-the-quota-for-the-abap-environment-c40cb18.md)\).

    > ### Caution:  
    > If you update your ABAP system, you can only change the system description and ABAP runtime size \(parameter `size_of_runtime`\). See [Updating an ABAP System](updating-an-abap-system-7890ffa.md).

10. Choose *Next* to review and verify your instance details.

11. Choose *Create*.

    The ABAP environment instance is being set up, which might take a while. Wait for an email that is sent when the setup is completed and the system up and running. The email is sent to the email address that you specified as admin email in the previous steps.


