<!-- loio35a58825872248d9bef663ad1be5997a -->

# Dismantle



As soon as a consumer unsubscribes from the SaaS solution, an immediate tenant decommissioning process takes place while taking a “grace period” of 30 days into account, according to the following legal obligations:

![](images/tenant_decom_11f150d.jpg)

During the grace period

-   The tenant access is blocked for the consumer and for the SaaS provider as well in the support use case.

-   The provider can restore the tenant in the *Landscape Portal*. See [Restore Consumer Tenants](restore-consumer-tenants-619c40e.md).


After the end of the grace period, the tenant and all related data are irreversibly deleted and cannot be restored anymore.

Once the last consumer unsubscribes from the SaaS solution, the provider needs to delete the empty system in the BTP cockpit.

Alternatively, as a SaaS solution operator, your can use the *Subscription Management Dashboard* in the provider subaccount to unsubscribe tenants centrally without triggering unsubscription in the consumer subaccount. See [Using the Subscription Management Dashboard](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/434be695f9e946ccb4c28911dd1e16d0.html).

