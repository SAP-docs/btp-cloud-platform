<!-- loioc882a2af60e84cf8912b878ddabff3cf -->

# Consumer Offboarding

As soon as a consumer unsubscribes from the SaaS solution, an immediate tenant decommissioning process will take place while taking a “grace period” of 30 days into account, according to the following legal obligations:

![](images/tenant_decom_11f150d.jpg)

During the grace period

-   the tenant access is blocked for the consumer and for the SaaS provider as well in the support use case.

-   the provider can restore the tenant in the*Landscape Portal*. See [Restore Tenants](Restore_Tenants_619c40e.md).


After the end of the grace period, the tenant and all related data are irreversibly deleted and cannot be restored anymore.

Once the last consumer unsubscribes from the SaaS solution, the provider needs to delete the empty system in the BTP cockpit.

