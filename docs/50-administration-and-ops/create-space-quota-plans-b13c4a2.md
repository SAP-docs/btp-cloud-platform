<!-- loiob13c4a2666dd4018a52780da581bbf6d -->

# Create Space Quota Plans

You can use the cockpit to create space quota plans.



<a name="loiob13c4a2666dd4018a52780da581bbf6d__prereq_ofw_ghw_4bb"/>

## Prerequisites

You have the Org Manager role for the org in which you want to create a space quota plan.



<a name="loiob13c4a2666dd4018a52780da581bbf6d__steps_l1r_b3w_4bb"/>

## Procedure

1.  Navigate to the subaccount that contains the spaces to which you want to add quotas.

2.  In the navigation menu, choose *Cloud Foundry* \> *Quota Plans*.

3.  Choose *New Plan*.

4.  Enter a name for your quota plan and add limits for the following quotas:

    -   Memory \(MB\): Total amount of memory a space can have
    -   \(Optional\) Routes: Total number of routes
    -   \(Optional\) Services: Total number of service instances
    -   \(Optional\) Instance memory: Maximum amount of memory an application instance can have \(`-1` represents an unlimited amount\)

    -   \(Optional\) App Instances: Total number of application instances
    -   \(Optional\) Allow paid services: Select if you'd like to allow the provisioning of instances of paid service plans

    > ### Note:  
    > The org quota limit is applicable for a resource if you don’t enter a space quota limit. If the space quota limit for a resource exceeds the org quota limit, the org quota limit applies.

5.  Save your changes.


**Related Information**  


[Entitlements and Quotas](../10-concepts/entitlements-and-quotas-00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

