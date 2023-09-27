<!-- loiodd7d8e854d35412180c64f6c15364add -->

# Manage Test Tenants

As a provider, you might want to test your solution on a test tenant. While you could create a new subaccount and provision a new tenant for yourself for test purposes, the *Landscape Portal* offers a much simpler and faster way for you to create a test tenant.

With the*Manage Test Tenant*app, you can easily create or delete test tenants, and view their status history.

> ### Note:  
> The business type of the test tenant depends on the system type. In a development system, a tenant of type "Partner Test Tenant" is created. In non-development systems, a tenant of type "Test Tenant" is created. Unlike consumer tenants, created via subscription, test tenants can be created in any type of system. For more information, see [Tenant Business Types](tenant-business-types-018e8bd.md).



<a name="loiodd7d8e854d35412180c64f6c15364add__section_drt_brz_f4b"/>

## Creating / Deleting a Test Tenant:

1.  Sign in to the *Landscape Portal* and click on the *Manage Test Tenant* tile to open the app.
2.  In the *Available Systems*list, select a system. The *Available Tenants* list on the right will now display all tenants in this system. Use the filter in the top right-hand corner to view all tenants or only test tenants.
3.  a\) *To delete a test tenant*: select it, and click the *Delete* button. Note that only test tenants can be deleted in the app. Keep in mind that there is no retention time: once the test tenant is deleted, it cannot be restored.

    b\) *To create a new test tenant*: click the*Create Tenant* button. Enter the email address for the initial tenant admin. This is the user who will be the first to sign into the test tenant. Use a provider's email address that is contained in the provider IDP. Click *OK*. A request to create the tenant is now scheduled. Once the tenant has been created, a request to provision the initial tenant admin will be triggered automatically.

4.  Track the progress of your action in the status list below.




<a name="loiodd7d8e854d35412180c64f6c15364add__section_wh4_crz_f4b"/>

## Accessing a Test Tenant

You can log on to the Fiori Launchpad of the tenant via the link in the *Available Tenants* list. Note that you need to subscribe to Web Access for ABAP in order to gain access, see [Subscribing to the Web Access for ABAP](../20-getting-started/subscribing-to-the-web-access-for-abap-98928b0.md).

1.  Once the test tenant and the initial tenant admin have been provisioned, the test tenant is added to the list of *Available Tenants* with *Lifecycle Status* "*Live*". You can now click on the tenant's client number to open the test tenant.
2.  Use the initial tenant admin's credentials to sign into the test tenant for the first time.

> ### Note:  
> Note that you cannot access a test tenant via ADT with a support user.

