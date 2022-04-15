<!-- loiob31712cc9dbf44fb8a603ab4be6f8d28 -->

# Create Support Users



<a name="loiob31712cc9dbf44fb8a603ab4be6f8d28__section_a1p_4hv_gqb"/>

## Context

You can create a support user to access a consumer tenant.



<a name="loiob31712cc9dbf44fb8a603ab4be6f8d28__section_dtt_2rf_knb"/>

## Procedure

1.  Log in to the *Landscape Portal* and click the tile *Systems Overview* to see an overview of all your systems.
2.  Select the system that contains the tenant for which you would like to create a support user.
3.  Navigate to the tenant for which you would like to create a support user.
4.  Click on the *Request Support User* button in the upper right corner of the page.
5.  \(Optional\) Check the *Requests* tab in your system to track the execution status of your action \( "New support user"\).
6.  Afterwards, you can log on to the Fiori Launchpad of the tenant via the link in the tenants overview. Note that you need to subscribe to Web Access for ABAP in order to gain access, see [Subscribing to the Web Access for ABAP](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/98928b0941294c74b946cdcefca9b047.html).

You can connect to the system via ADT.

1.  Retrieve the service key for the targeted ABAP System:
    1.  Navigate to the provider accounts’ service instances.
    2.  Select the ABAP service instance.
    3.  Open and copy the SAP\_ASP service key.

2.  Retrieve the tenant GUID of the targeted ABAP tenant:
    1.  Sign in to the *Landscape Portal*.
    2.  Copy the link of the client column of the target tenant.
    3.  Extract the tenant GUID from the URL.

3.  Create a tenant-specific service key
    1.  Replace the GUID in the url field of the service key from step 1.c with the tenant GUID.

4.  Use the created service key to login to the target system using an ABAP Cloud Project in ABAP Development Tools.

