<!-- loio60e8f54fe40147249ce8c067948abb11 -->

# Troubleshooting

Find out which steps you can take to identify and resolve specific issues that may come up when developing a multitenant application.



<a name="loio60e8f54fe40147249ce8c067948abb11__section_efb_jnn_ysb"/>

## SaaS subscription error

-   The *Landscape Portal* subscription might be missing. Make sure the *Landscape Portal* is subscribed to in the provider subaccount. This needs to be done before the SaaS subscription.

-   The ASP\_CC \(CF Cloud Controller\) destination might have failed: An ASP\_CC destination with the correct credentials/URLs must exist in the provider subaccount \(see [Cloud Controller Access Destination](order-and-provide-975bd3e.md#loio35b5acbb32024aa6b90a22e9f957a9f6)\). You can use a connection check in the destination for a basic connectivity test. You can also test if the user that was used in the ASP\_CC destination is able to authenticate with the following cf command: cf login -a <cf-api-endpoint e.g. https://api.cf.eu10.hana.ondemand.com\> -u <destination-user-name\> -p <password\> -s <provider-space\> -o <provider-org\>. Make sure the following is the case:

    -   You have the credentials you require \(space developer user\). This user is a CF Platform User, i.e. it is either an S-User or a P-User, usually created using a distribution list so that it is a non-personalized e-mail address. A technical communication user that can also be created similar to normal S-Users cannot be used here.

    -   You are using the correct URL: the URL needs to be the same as the CF API URL in the provider subaccount, depending on the region, see [Region](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/350356d1dc314d3199dca15bd2ab9b0e.html?locale=en-US&version=Cloud#loio879f37370d9b45e99a16538e0f37ff2c).

    -   You are using the right Token Service URL for the region.

    -   You are using a technical user as recommended, not a personal user. Personal user accounts can cause issues due to password changes etc.


-   The space developer user might be missing: The user used in the credentials of the ASP\_CC destination must be added as space developer in the space of the multitenant application.

-   There might be missing entitlements for ABAP systems: During the subscription, the multitenant application/ASP automatically provisions ABAP systems. Make sure that the necessary entitlements are added to the provider subaccount:

    -   abap/standard \(for delivery via gCTS\) or abap/saas\_oem \(for add-on based delivery\), depending on the configuration of ASP parameter addon\_product\_name. See [Multitenancy in the ABAP Environment](multitenancy-in-the-abap-environment-633cc61.md) and [ABAP Solution Service](order-and-provide-975bd3e.md#loio1697387c02e74e66a55cf21a05678167).

    -   abap\_compute\_unit and hana\_compute\_unit depending on the configuration of ASP parameter size\_of\_runtime and size\_of\_persistence. See [Multitenancy in the ABAP Environment](multitenancy-in-the-abap-environment-633cc61.md) and [ABAP Solution Service](order-and-provide-975bd3e.md#loio1697387c02e74e66a55cf21a05678167).


-   There might be missing entitlements for multitenant app deployment. Make sure that the necessary entitlements are added to the provider subaccount:

    -   Cloud Foundry Runtime entitlement for the approuter in the multitenant app.

    -   ABAP Solution Service.


-   In case of error "Illegal given domain name" during subscription:

    -   The subscription fails because in the saas-registry service instance the URL defined for onSubscription and getDependencies callbacks does not match the pattern of the cis-... route assigned to the approuter application. Please make sure that the route defined in your saas-registry configuration for callbacks has the same pattern as defined in the cis-... route.





<a name="loio60e8f54fe40147249ce8c067948abb11__section_l5t_lnn_ysb"/>

## Cannot delete ABAP service instance

-   If you cannot delete an ABAP service instance, the ABAP service instance might still contain *Partner Test*, *Partner Customer Test*, or *Partner Customer Production* tenants. Make sure you delete these tenants first by unsubscribing from them \(for tenants created via consumer subscription\) or deleting the tenants in the *Landscape Portal*\(for test tenants created directly in the *Landscape Portal*\).

-   The ABAP service instance might still contain a SAP\_ASP service key: The service key needs to be deleted before the service instance can be deleted.




<a name="loio60e8f54fe40147249ce8c067948abb11__section_q4v_pnn_ysb"/>

## Multitenant application cannot be undeployed

-   Always use MTA Undeployment \(cf undeploy <MTA ID\> --delete-services\) instead of deleting service instances individually.

-   Check if the saas-registry service instance still contains active subscriptions: the saas-registry instance can only be deleted once there are no more active subscriptions. Unsubscribe using the [Subscription Management Dashboard](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/434be695f9e946ccb4c28911dd1e16d0.html?locale=en-US&version=Cloud).




<a name="loio60e8f54fe40147249ce8c067948abb11__section_qfm_snn_ysb"/>

## Cannot create consumer-specific route according to `TENANT_HOST_PATTERN` \(in the development phase\)

> ### Sample Code:  
> ```
> TENANT_HOST_PATTERN: (.*)-my-consumer-subdomain-productabcdefghijklmnopq-saas-solution-dev.cfapps.eu10.hana.ondemand.com
> Consumer Subaccount Subdomain: my-consumer-subdomain
> Route Domain: cfapps.eu10.hana.ondemand.com
> Route Hostname: my-consumer-subdomain-productabcdefghijklmnopq-saas-solution-dev (64 characters)
> 
> ```

-   Keep in mind that the hostname of the route in CF is limited to 63 characters.

-   In the development phase, the hostname part of the route should consist of the consumer subdomain, separator \(“-“\), and the appName.

-   Either shorten the subdomain of the consumer subaccount or shorten the appName used in TENANT\_HOST\_PATTERN.




<a name="loio60e8f54fe40147249ce8c067948abb11__section_bzz_5nn_ysb"/>

## After deployment of MTA for multitenant application, no abap system is created

-   ABAP systems are automatically created by the ABAP Solution Provider \(ASP\) during the first subscription.




<a name="loio60e8f54fe40147249ce8c067948abb11__section_kxc_wnn_ysb"/>

## Issues with parameter consumer\_tenant\_limit

-   Keep in mind that recently deleted consumer tenants are counted towards the tenant limit. Systems are automatically created.




<a name="loio60e8f54fe40147249ce8c067948abb11__section_z3g_xnn_ysb"/>

## First consumer tenant is missing application content after subscription

-   Only in case of delivery via add-on, the application content is installed before the consumer tenant is accessible. In case of delivery via gCTS, the software components need to be imported manually using the *Manage Software Components* app in client 100 of the system.




