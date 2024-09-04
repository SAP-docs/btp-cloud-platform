<!-- loio195a685a71f84953813e7b3bd255e849 -->

# Access to Landscape Portal

The *Landscape Portal* acts as a central tool that allows you to perform lifecycle management operations, such as provisioning new consumers tenants, users, and more. See [Landscape Portal](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/6aa0a773510e4c82b167fcca4c755327.html).

As an operator, subscribe to the *Landscape Portal* application in the *05 Provide* subaccount in both the global account for development and global account for production. The `LandscapePortalAdminRoleCollection` needs to be assigned to the users in the default identity provider of the subaccount that you want to provide access to the *Landscape Portal* app. See [Accessing the Landscape Portal](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/d9e865ad47204b80816b6f62af57b823.html).

> ### Note:  
> Note: In the global account for development, you can use a booster \(see [Booster for Landscape Portal](prepare-4338854.md#loio8d34e0f80489468088a99202a7fb4a60)\) to automatically set up a subaccount with a working Landscape Portal subscription.

> ### Note:  
> In the Landscape Portal, you can access the provider system and choose the provider tenant \(client 100\). Via the provider tenant, you get access to Fiori Apps, for example the *Manage Software Components* app, which is used for importing software components via gCTS.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

