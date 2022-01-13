<!-- loio60e8f54fe40147249ce8c067948abb11 -->

# Troubleshooting



<a name="loio60e8f54fe40147249ce8c067948abb11__section_uzd_yg2_trb"/>

## Multitenant Application / ABAP Solution Provider \(ASP\)



### SaaS subscription error

-   The *Landscape Portal* subscription might be missing. Make sure the *Landscape Portal* is subscribed to in the provider subaccount. This needs to be done before the SaaS subscription.

-   The ASP\_CC \(CF Cloud Controller\) destination might have failed: An ASP\_CC destination with the correct credentials/URLs must exist in the provider subaccount. You can use a connection check in the destination for a basic connectivity test. Make sure the following is the case:

    -   You have the credentials you require \(space developer user\).

    -   You are using the correct URL: the URL needs to be the same as the CF API URL in the provider subaccount, depending on the region, see [Region](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/350356d1dc314d3199dca15bd2ab9b0e.html?locale=en-US&version=Cloud#loio879f37370d9b45e99a16538e0f37ff2c).

    -   You are using the right UAA Token Service URL for the region, see [Region](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/350356d1dc314d3199dca15bd2ab9b0e.html?locale=en-US&version=Cloud#loio879f37370d9b45e99a16538e0f37ff2c).

    -   You are using a technical user as recommended, not a personal user. Personal user accounts can cause issues due to password changes etc.


-   The space developer user might be missing: The user used in the credentials of the ASP\_CC destination must be added as space developer in the space of the multitenant application.

-   There might be missing entitlements for ABAP systems: During the subscription, the multitenant application/ASP automatically provisions ABAP systems. Make sure that the necessary entitlements are added to the provider subaccount:

    -   abap/standard \(for delivery via gCTS\) or abap/saas\_oem \(for add-on based delivery\), depending on the configuration of ASP parameter addon\_product\_name. See [Multitenancy in the ABAP Environment](multitenancy-in-the-abap-environment-633cc61.md) and [Define Your ABAP Solution](define-your-abap-solution-1697387.md).

    -   abap\_compute\_unit and hana\_compute\_unit depending on the configuration of ASP parameter size\_of\_runtime and size\_of\_persistence. See [Multitenancy in the ABAP Environment](multitenancy-in-the-abap-environment-633cc61.md) and [Define Your ABAP Solution](define-your-abap-solution-1697387.md).


-   There might be missing entitlements for multitenant app deployment. Make sure that the necessary entitlements are added to the provider subaccount:

    -   Cloud Foundry Runtime entitlement for the approuter in the multitenant app.

    -   ABAP Solution Service.


-   In case of error "Illegal given domain name" during subscription:

    -   The subscription fails because in the saas-registry service instance the URL defined for onSubscription and getDependencies callbacks does not match the pattern of the cis-... route assigned to the approuter application. Please make sure that the route defined in your saas-registry configuration for callbacks has the same pattern as defined in the cis-... route.





### Cannot delete ABAP service instance

-   If you cannot delete an ABAP service instance, the ABAP service instance might still contain *Partner Test*, *Partner Customer Test*, or *Partner Customer Production* tenants. Make sure you delete these tenants first by unsubscribing from them \(for tenants created via consumer subscription\) or deleting the tenants in the *Landscape Portal*\(for test tenants created directly in the *Landscape Portal*\).

-   The ABAP service instance might still contain a SAP\_ASP service key: The service key needs to be deleted before the service instance can be deleted.




### Multitenant application cannot be undeployed

-   Always use MTA Undeployment \(cf undeploy <MTA ID\> --delete-services\) instead of deleting service instances individually.

-   Check if the saas-registry service instance still contains active subscriptions: the saas-registry instance can only be deleted once there are no more active subscriptions. Unsubscribe using the [Subscription Management Dashboard](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/434be695f9e946ccb4c28911dd1e16d0.html?locale=en-US&version=Cloud).




### Cannot create consumer-specific route according to `TENANT_HOST_PATTERN` \(in the development phase\)

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




### After deployment of MTA for multitenant application, no abap system is created

-   ABAP systems are automatically created by the ABAP Solution Provider \(ASP\) during the first subscription.




### Issues with parameter consumer\_tenant\_limit

-   Keep in mind that recently deleted consumer tenants are counted towards the tenant limit. Systems are automatically created.




### First consumer tenant is missing application content after subscription

-   Only in case of delivery via add-on, the application content is installed before the consumer tenant is accessible. In case of delivery via gCTS, the software components need to be imported manually using the *Manage Software Components* app in client 100 of the system.




<a name="loio60e8f54fe40147249ce8c067948abb11__section_bpt_nh2_trb"/>

## Landscape Portal



### *Add-on Update* button is not enabled

-   Check if you have the necessary role collection assigned to your user. This feature requires role collection “LandscapePortalAdminRoleCollection”.

-   To use this feature, an add-on product needs to be installed. Make sure the add-on product is shown in the *Software* section of the system.

-   Make sure there are no ongoing add-on update processes.




### Version number does not change after add-on update

-   If the version number does not change after an add-on update, a new add-on version might have already been installed in the system.

-   The software component version may already be installed in the system or the add-on configuration might not match the required settings. Please see [Add-on descriptor file.](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#add-on-descriptor-file) 


