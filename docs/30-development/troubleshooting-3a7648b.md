<!-- loio3a7648b69f514365b1842dde29cfda85 -->

# Troubleshooting



<a name="loio3a7648b69f514365b1842dde29cfda85__section_q4v_pnn_ysb"/>

## Multitenant application cannot be undeployed

-   Always use MTA Undeployment \(cf undeploy <MTA ID\> --delete-services\) instead of deleting service instances individually.

-   Check if the saas-registry service instance still contains active subscriptions: the saas-registry instance can only be deleted once there are no more active subscriptions. Unsubscribe using the [Subscription Management Dashboard](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/434be695f9e946ccb4c28911dd1e16d0.html?locale=en-US&version=Cloud).




<a name="loio3a7648b69f514365b1842dde29cfda85__section_qfm_snn_ysb"/>

## Cannot create consumer-specific route according to `TENANT_HOST_PATTERN` \(in the development phase\)

> ### Sample Code:  
> ```
> TENANT_HOST_PATTERN: (.*)-my-consumer-subdomain-productabcdefghijklmnopq-saas-solution-dev.cfapps.eu10.hana.ondemand.com
> Consumer Subaccount Subdomain: my-consumer-subdomain
> Route Domain: cfapps.eu10.hana.ondemand.com
> Route Hostname: my-consumer-subdomain-productabcdefghijklmnopq-saas-solution-dev (64 characters)
> 
> ```



<a name="loio3a7648b69f514365b1842dde29cfda85__section_bzz_5nn_ysb"/>

## After deployment of MTA for multitenant application, no abap system is created

-   ABAP systems are automatically created by the ABAP Solution Provider \(ASP\) during the first subscription.




<a name="loio3a7648b69f514365b1842dde29cfda85__section_kxc_wnn_ysb"/>

## Issues with parameter consumer\_tenant\_limit

-   Keep in mind that recently deleted consumer tenants are counted towards the tenant limit. Systems are automatically created.


