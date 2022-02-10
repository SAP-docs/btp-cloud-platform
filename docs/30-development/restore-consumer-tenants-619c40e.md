<!-- loio619c40e93cb2420198aa096492f0a9ef -->

# Restore Consumer Tenants

*Partner Customer Production* tenants and*Partner Customer Test*tenants in status *Torn Down* \(i.e. they are currently being deleted\) can be restored while they are still in retention time. You, as a provider, can restore these tenants in the *Landscape Portal*.



## Context

When a consumer unsubscribes from a provider's SaaS production or test solution, a tenant decommisioning process will take place taking a grace period of 30 days into account \(see [Consumer Offboarding](consumer-offboarding-c882a2a.md)\). During the grace period, the tenant is in what is referred to as retention time and can no longer be accessed by you as the provider, nor by your consumer. If the consumer decides to re-subscribe to the SaaS solution during this time, or if the consumer requests important data before the tenant will be deleted, you, as a provider, can trigger the tenant recovery directly in the *Landscape Portal*.

> ### Note:  
> Tenant recovery is only possible for tenants which were created via consumer subscription. Tenants which can be created and deleted directly in the *Landscape Portal* for test purposes can't be restored.
> 
> If a consumer provisions a tenant but doesn't complete the onboarding process by signing in as initial administrator, then the tenant can't be restored after it has been deleted.



## Procedure

1.  Check the BTP Cockpit to make sure that the concerned consumer is unsubscribed from the SaaS solution in their subaccount.

2.  Sign in to the *Landscape Portal* and click on the tile *Restore Consumer Tenant* to see a list of tenants that are currently in retention time.

3.  Select the tenant you would like to restore for the consumer and click *Restore*. Confirm your selection with *OK*.

4.  **\(Optional\)** You can track the status of the tenant restore process in the request log.

5.  Once the tenant has been restored, the consumer can \(re\)subscribe to the SaaS solution from their subaccount. The restored tenant will be immediately accessible for the consumer and can be used again.


