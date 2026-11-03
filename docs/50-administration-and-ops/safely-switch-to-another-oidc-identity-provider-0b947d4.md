<!-- loio0b947d490dd540aab009d9eac4b83885 -->

# Safely Switch to Another OIDC Identity Provider

Safely move an OIDC trust configuration to another SAP Cloud Identity Services tenant without losing user data, such as authorizations or user-related data in subscribed applications.



## Context

As a subaccount administrator, you want to consolidate your landscape. You want to use a different SAP Cloud Identity Services tenant than the one you used so far. Be aware that data provided by identity providers and key data of trust configurations are used to store user-related data, so you want to ensure that this change doesn't impact any user data. To avoid any impact, safely update your trust configuration and switch to another identity provider.

For more information, see SAP Note [3468982](https://me.sap.com/notes/3468982).

This change requires planned downtime. Reconfigure the trust in SAP BTP and SAP Cloud Identity Services so that SAP BTP receives exactly the same user data as before. Some time is needed before sign-in is available again.

> ### Caution:  
> For such a change, it's not a good idea to delete your old trust configuration and then create a new identity provider. When you delete a trust configuration, you lose all role collection assignments and the shadow users in the subaccount. User-related data in applications and services might be affected as well.

> ### Recommendation:  
> Practice this procedure in your development or test subaccounts before carrying it out in your productive subaccounts.



## Procedure

1.  To switch the SAP Cloud Identity Services tenant of your trust configuration, go to the custom trust configuration for applications that you want to switch to another identity provider.

2.  Select the trust configuration.

3.  Choose the *Switch Tenant* button. A popup is displayed that lists all resources of this subaccount. Multiple cases are possible.

    1.  The subaccount doesn't contain any applications, which use SAP Cloud Identity Services directly. You can perform a tenant switch.
    2.  The applications support a tenant switch and can be migrated to the selected tenant. Review, re-create the user group assignments, and adapt the configuration of the applications.
    3.  Some of the applications don't support a tenant switch. In this case, you can't perform a tenant switch.

    For more information, see SAP Note [3468982](https://me.sap.com/notes/3468982).

4.  If a tenant switch is possible, confirm that you want to perform the tenant switch. Don't forget to adjust the configuration of the applications afterwards.

5.  \(If required\) With the new tenant, the cockpit automatically suggests you a domain of the new tenant. Check the domain. To adapt it, choose *Edit*.

6.  \(If required\) Save your domain changes.

    The origin, user names, and shadow user IDs remain the same. Make sure you keep the same subject identifier and user attributes.


