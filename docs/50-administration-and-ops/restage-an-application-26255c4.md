<!-- loio26255c49fefa4729a46d2b5d564c42ac -->

# Restage an Application

You can use the SAP BTP cockpit to restage an application deployed to the Cloud Foundry environment.



## Prerequisites

-   You have either the Space Developer or Space Supporter role. For more information, see [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).

-   You've prepared for the downtime caused by restaging the application.




## Context

You need to restage your application when environmental changes might affect how it runs, even if you have not changed the application code. Restaging is useful when runtime dependencies change, such as when you bind your application to a new service or you modify environment variables. You also use it when buildpacks or stacks are updated.

Restaging:

-   Integrates updated configurations or dependencies with your current code. This process re-compiles the application so that the new droplet reflects these changes.

-   Helps ensure that the performance of your application matches the latest environment settings and service configurations.




## Procedure

1.  In your Cloud Foundry subaccount, navigate to the space where you would like to restage your application.

2.  On the *Applications* page, choose *Restage Application*.

3.  Choose an application from the dropdown menu.

    The dropdown contains all applications deployed in the space.

4.  Choose *Restage* to confirm the action.




## Results

Similar to restarting, it may take several minutes for the application to start working again.

**Related Information**  


[Application Operations in the Cloud Foundry Environment](application-operations-in-the-cloud-foundry-environment-0f1286a.md "Learn more about the different application operations that you can perform in the Cloud Foundry environment.")

