<!-- loiodd7d8e854d35412180c64f6c15364add -->

# Use Test Tenants

As a SAP BTP ABAP environment user, you might want to test your solution on a test tenant. While you could create a new subaccount and provision a new tenant for yourself for test purposes, the *Landscape Portal* offers a much simpler and faster way for you to create a test tenant.

> ### Note:  
> The business type of the test tenant depends on the system type. In a development system, a tenant of type "Partner Test Tenant" is created. In non-development systems, a tenant of type "Test Tenant" is created. Unlike consumer tenants, created via subscription, test tenants can be created in any type of system.



<a name="loiodd7d8e854d35412180c64f6c15364add__section_drt_brz_f4b"/>

## Creating a Test Tenant:

1.  Sign in to the *Landscape Portal* and click on the tile *Systems Overview*, then navigate to the system in which you want to create the test tenant.
2.  Click the *New Tenant*button in the top right corner and confirm the dialog box.
3.  Enter the email address for the initial tenant admin. This is the user who will be the first to sign into the test tenant. Use a provider's email address that is contained in the provider IDP. Click *OK*.
4.  A request to create the tenant is now scheduled. Once the tenant has been created, a request to provision the initial tenant admin will be triggered automatically. You can view the status of your requests in the *Requests* log.



<a name="loiodd7d8e854d35412180c64f6c15364add__section_wh4_crz_f4b"/>

## Accessing a Test Tenant:

1.  Once the test tenant and the initial tenant admin have been provisioned, the test tenant is added to the list of *Tenants* with *Lifecycle Status* "*Live*".
2.  You can now click on the tenant's client number to open the test tenant.
3.  Use the initial tenant admin's credentials to sign into the test tenant for the first time.
4.  \(Optional\) To add new users to the tenant, use the apps *Maintain Employees* and *Maintain Business Users*.

> ### Note:  
> Note that you cannot access a test tenant via ADT with a support user.



<a name="loiodd7d8e854d35412180c64f6c15364add__section_py4_crz_f4b"/>

## Deleting a Test Tenant:

Test tenants can be deleted in the *Landscape Portal*. Once you don't need your test tenant anymore, you can simply delete it by selecting the tenant and clicking *Delete* on the tenant's details page.

Keep in mind that there is no retention time: once the test tenant is deleted, it cannot be restored. All the requests related to a test tenant that has been deleted will be removed from the request log.

