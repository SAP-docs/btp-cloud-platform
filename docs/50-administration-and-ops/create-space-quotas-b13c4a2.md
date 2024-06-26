<!-- loiob13c4a2666dd4018a52780da581bbf6d -->

# Create Space Quotas

You can use the cockpit to create space quotas.



<a name="loiob13c4a2666dd4018a52780da581bbf6d__prereq_ofw_ghw_4bb"/>

## Prerequisites

You have the Org Manager role for the org in which you want to create a space quota.

<a name="task_igz_xgy_dzb"/>

<!-- task\_igz\_xgy\_dzb -->

## Feature Set A



<a name="task_igz_xgy_dzb__steps_ycr_pz5_qbc"/>

## Procedure

1.  Navigate to the subaccount that contains the spaces to which you want to add quotas.

2.  In the navigation menu, choose *Cloud Foundry* \> *Quota Plans*.

3.  Choose *Create Quota Plan*.

4.  Enter a name for your quota plan and add limits for the following:

    -   *Memory \(MB\)*: Total amount of memory a space can have

    -   \(Optional\) *Routes*: Total number of routes

    -   \(Optional\) *Services*: Total number of service instances

    -   \(Optional\) *Instance Memory \(MB\)*: Maximum amount of memory an application instance can have \(`-1` represents an unlimited amount\)

    -   \(Optional\) *App Instances*: Total number of application instances

    -   \(Optional\) *Allow Paid Services*: Select if you'd like to allow the provisioning of instances of paid service plans


    > ### Note:  
    > The org quota limit is applicable for a resource if you don’t enter a space quota limit. If the space quota limit for a resource exceeds the org quota limit, the org quota limit applies.

5.  Choose *Create*.


<a name="task_gcl_rhy_dzb"/>

<!-- task\_gcl\_rhy\_dzb -->

## Feature Set B



<a name="task_gcl_rhy_dzb__steps_l1r_b3w_4bb"/>

## Procedure

1.  Navigate to the subaccount that contains the spaces to which you want to add quotas.

2.  In the navigation menu, choose *Cloud Foundry* \> *Space Quotas*.

3.  Choose *Create Space Quota*.

4.  Enter a name for your space quota and add limits for the following:

    -   *Memory \(MB\)*: Total amount of memory a space can have

    -   *Routes*: Total number of routes

    -   *Services*: Total number of service instances

    -   *Instance Memory \(MB\)*: Maximum amount of memory an application instance can have \(`-1` represents an unlimited amount\)

    -   *App Instances*: Total number of application instances

    -   \(Optional\) *Allow Paid Service*: Switch on if you'd like to allow the provisioning of instances of paid service plans

    > ### Note:  
    > If the space quota limit for a resource exceeds the org quota limit, the org quota limit applies.

5.  Choose *Create*.


**Related Information**  


[Entitlements and Quotas](../10-concepts/entitlements-and-quotas-00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Create Space Quota Plans Using the Cloud Foundry Command Line Interface](create-space-quota-plans-using-the-cloud-foundry-command-line-interface-504fde9.md "You can use the Cloud Foundry Command Line Interface to create space quota plans.")

