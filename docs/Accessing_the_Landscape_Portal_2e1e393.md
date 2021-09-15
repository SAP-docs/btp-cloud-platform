<!-- loio2e1e3931d39b4e2e88a411799de31616 -->

# Accessing the Landscape Portal

> ### Note:  
> You can only access the *Landscape Portal* in one global account. If you want to access the *Landscape Portal* in another global account, you need to create a new SAP IDP user.



To enable the *Landscape Portal*, you need to subscribe to it in the SAP BTP cockpit. Here’s how:



### Subscribing to the *Landscape Portal* in the SAP BTP cockpit 

1.  Sign into your account in the *SAP BTP Cockpit*.
2.  Select your global account, then navigate to *Subaccounts* and select your production subaccount.
3.  Navigate to *Subscriptions*.
4.  The *Landscape Portal*tile is now visible but still says "*Not subscribed*".
5.  Click the tile to subscribe to it. The subscription process might take a few minutes. When everything is ready, the tile will say *Subscribed*. From now on, you can open the Landscape Portal simply by navigating to the tile and clicking on*Go to application*.



In order to log into the *Landscape Portal* app, a user first needs to be assigned the necessary role collection. This is done by the security administrators in the SAP BTP cockpit. For more information on how to add security administrators, see [Add Security Administrators to Your Subaccount \[Feature Set A\]](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/fea877c449ba4c5fbb0aafd92a80afb4.html).



### Assigning the Landscape Portal Role Collections

> ### Note:  
> You need to be a security administrator in your production subaccount in order to assign the role collections. 

There are two different role collections with which you can access the *Landscape Portal*:

-   Landscape Portal Admin \("LandscapePortalAdminRoleCollection"\): Full functionality of the *Landscape Portal*.

-   Landscape Portal User \("LandscapePortalUserRoleCollection"\): Read-only view of the *Landscape Portal*and the right to create Support Users.


For more information on how to assign role collections, see [Assign Users to Role Collections](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/c5766765bda74ad59fe656977c8fa4d6.html).

> ### Note:  
> -   The old role collection "LandscapePortalRoleCollection" is obsolete \(can be deleted\) and should no longer be used as of release 2105. Users that were assigned this role collection will need to be assigned one of the role collections mentioned above. After assignment of the new role collection, please sign out of the *Landscape Portal* and sign in again.
> 
> -   Unsubscription and renewed subscription to the *Landscape Portal* is not required to use this functionality.

> ### Note:  
> If you have subscribed to the *Landscape Portal* from multiple subaccounts, you have to adjust the role collection assignment consistently, that is you need to assign the same role collections to the same user in every subaccount you are accessing the *Landscape Portal* from.

