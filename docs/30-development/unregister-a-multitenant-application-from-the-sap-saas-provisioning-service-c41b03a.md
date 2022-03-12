<!-- loioc41b03aad96147daa284f9f5cb2952c6 -->

# Unregister a Multitenant Application from the SAP SaaS Provisioning Service

Unbind and delete the service instance you have created during the registration of your multitenant application to complete the unregistration process.



<a name="loioc41b03aad96147daa284f9f5cb2952c6__prereq_gk5_vsj_vkb"/>

## Prerequisites

Make sure that no tenant is subscribed to your application before you initiate the deletion of the service instance.

> ### Tip:  
> Use the `Get Application Subscriptions` API to get the application subscriptions.
> 
> In case there are subscribed tenants, unsubscribe them first by calling the `Unsubscribe the tenant from an application` API.
> 
> For more information, see [Using SAP SaaS Provisioning Service APIs to Manage Multitenant Applications](using-sap-saas-provisioning-service-apis-to-manage-multitenant-applications-ed08c7d.md).



## Context

The procedure described in this section uses the cf CLI.

> ### Tip:  
> You can delete a service instance directly in the SAP BTP cockpit, in the *Service Instances* page.



## Procedure

1.  Use cf CLI to remove any existing service keys and app bindings:

    1.  Run the following command to delete the service key:

        ```
        cf delete-service-key SERVICE-INSTANCE-NAME KEY-NAME
        ```

        > ### Note:  
        > Service key is an optional parameter.
        > 
        > In case you haven't created a service key during the registration process, skip to substep b.

    2.  Run the following command to unbind your application from the service instance:

        ```
        cf unbind-service APP-NAME SERVICE-INSTANCE-NAME
        ```

    3.  Run the following command to delete the service instance:

        ```
        cf delete-service SERVICE-INSTANCE-NAME
        ```


2.  The deletion process is asynchronous. Run `cf services` to view the current status of the process.


