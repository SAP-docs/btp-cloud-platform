<!-- loiocd7e7e6108c24b5384b7d218c74e80b9 -->

# Using a Booster to Automate the Setup of the ABAP Environment \(Optional\)

You can use a booster to automate some of the required steps for setting up the ABAP environment. Automation includes creating a subaccount and space, configuring the required entitlements, and assigning administrators and developers to the subaccount.



## Context

A booster is a set of guided interactive steps that enable you to select, configure, and consume services on SAP BTP. For more information, see [Boosters](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/fb1b56148f834749a2bf51127421610b.html).

> ### Caution:  
> The booster is only intended to create development systems. For non-development systems, follow the steps to set up the ABAP environment manually \(see [Getting Started with a Customer Account in the ABAP Environment](getting-started-with-a-customer-account-in-the-abap-environment-e34a329.md)\).



## Procedure

1.  Log on to the SAP BTP cockpit and choose the global account for the Cloud Foundry environment as administrator.

2.  From the navigation menu, choose *Boosters*.

3.  Choose the booster *Prepare an Account for ABAP Development*.

    The tab pages *Overview*, *Components*, and *Additional Resources* are displayed, where you get more information about the booster.

4.  Choose *Start*.

5.  After the system has successfully checked the prerequisites, choose *Next* to continue.

6.  On the *Prepare an Account for ABAP Development* dialog, entitlements and quotas for the new subaccount are proposed, but you can change them if needed:

    -   For the *ABAP environment* service, the service plan *standard* enables you to size ABAP server and persistence independently from each other in 16 GB units. These units are represented in the quota plans *abap\_compute\_unit* and *hana\_compute\_unit*.

        As part of the default quota assignment, you get at least 1 compute unit in the *abap\_compute\_unit* service plan and at least 4 compute units in the *hana\_compute\_unit* service plan. This corresponds to the minimum configuration for an instance of the ABAP Environment service. You can also choose higher quotas in the dialog of the booster.

    -   For the *Web Access to ABAP* service, a default plan is chosen that you cannot change. You need the service and the quota for direct browser access to your instances in the ABAP environment, including access to the administration launchpad for ABAP.
    -   Depending on what you have ordered for your account, additional entitlements for the services *Cloud Foundry Runtime*, *Launchpad*, and *SAP Business Application Studio* might be shown. They are optional; you can remove the entitlements if you don't need them right now and want to add them later:
        -   A quota for the Cloud Foundry runtime is only needed for the ABAP environment if your developers want to deploy their own apps in Cloud Foundry.
        -   The SAP Build Work Zone, standard edition enables organizations to establish a central point of access to SAP, custom-built, and third party applications and extensions, both in the cloud and on premise.
        -   SAP Business Application Studio is a UI development environment.


7.  On the *Prepare an Account for ABAP Development* dialog, follow the instructions on the screen to enter subaccount name, provider, region, and so on.

8.  On the *Add Users* dialog, add the e-mail addresses of new users in the ABAP environment.

    This step allows you to quickly create additional administration users for the ABAP environment, if needed, and developer users. In the *Origin* field, you can see the identity provider for the ABAP environment. By default, this is SAP ID service \(*sap.ids*\), but if you have set up a custom identity provider, you can choose this provider from the dropdown list.

9.  On the *Configure ABAP Environment Instance* dialog, enter a 3-character ID for your ABAP system.

10. Review your settings and finish the booster.




<a name="loiocd7e7e6108c24b5384b7d218c74e80b9__result_rlt_hb3_jkb"/>

## Results

After the booster has run successfully, the following tasks have been performed automatically:

-   A new Cloud Foundry subaccount for the ABAP environment is created and enabled.

-   A space and an organization for the ABAP environment are available.

-   A service instance for the ABAP environment has been created.

-   A system ID of your choice has been assigned to the ABAP system.

-   An identity provider \(SAP ID service or a custom identity provider\) has been set up for the ABAP environment.

-   For the *ABAP environment* service, quotas have been distributed for the ABAP server and the SAP HANA persistence. The quotas that you have chosen are deducted from the available quota for each service in your global account..

-   If you have entitlements for SAP Build Work Zone, standard edition and SAP Business Application Studio, then you have subscribed to these services and standard quotas have been assigned accordingly. \(\[Feature Set B\]: Entitlements for subscription services are assigned to the subaccount.\)

-   You’re subscribed to the Web access for ABAP SaaS application and get direct browser access to your instances in the ABAP environment. \(\[Feature Set B\]: Entitlements for subscription services are assigned to the subaccount.\)

-   Additional users with Cloud Foundry organization manager and space manager roles have been added. If you have ordered the launchpad as a service, the additional administration users have also been assigned to the role collection *Launchpad\_Admin*.

-   Additional users for developers with space developer role have been added. If you have ordered SAP Business Application Studio as a service, the additional developer users have also been assigned to the role collection *Business\_Application\_Studio\_Developer*.


> ### Note:  
> The booster speeds up the initial setup, but there are still some tasks that you need to perform after the booster has run.
> 
> In the following, you can find documentation for all necessary intial tasks, including the tasks that you don't need to perform if you have run the booster successfully. A note at the beginning of each task indicates that you can skip it if you’ve used the booster.

