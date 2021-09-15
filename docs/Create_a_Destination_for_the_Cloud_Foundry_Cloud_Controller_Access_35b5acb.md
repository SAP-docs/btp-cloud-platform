<!-- loio35b5acbb32024aa6b90a22e9f957a9f6 -->

# Create a Destination for the Cloud Foundry Cloud Controller Access

As a provider, you need to create a destination for the Cloud Foundry Cloud Controller to enable the creation and access of service instances.



<a name="loio35b5acbb32024aa6b90a22e9f957a9f6__section_ex4_dnw_qmb"/>

## Prerequisites

-   You've created a user in SAP ID service.
-   The user has been added as a member of the subaccount.
-   The user has been added as space developer in the provider subaccount.

> ### Note:  
> You might want to use a dedicated technical user rather than your personal one.



<a name="loio35b5acbb32024aa6b90a22e9f957a9f6__section_wl5_4nw_qmb"/>

## Process Steps

1.  Log into your provider subaccount.
2.  Navigate to *Connectivity* \> uic. Click on "*New Destination*". Fill in the template as follows:
    -   Name: ASP\_CC
    -   Type: HTTP
    -   Description: <optional\>
    -   URL: <enter the API Endpoint domain of your cloud foundry landscape. You can find it under your subaccount \> *Overview*. Example: https://api.cf.eu10.hana.ondemand.com
    -   Proxy Type: Internet
    -   Authentication: OAuth2Password
    -   User: <User ID/E-mail\>
    -   Password: <password\>
    -   Client ID: cf
    -   Client Secret <needs to be left blank\>
    -   Token Service URL: http://uaa.<landscape-host\>/oauth/token Example: https://uaa.cf.eu10.hana.ondemand.com/oauth/token \(For more information, see [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/viewer/3504ec5ef16548778610c7e89cc0eac3/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#879f37370d9b45e99a16538e0f37ff2c.html)\)
3.  Save your changes.

> ### Note:  
> Please make sure to add the respective user of the destination service as a member with role "space developer" in the space where your ABAP solution is deployed.

