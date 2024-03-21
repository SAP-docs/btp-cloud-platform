<!-- loio524e1081d8dc4b0f9d055a6bec383ec3 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Using Free Service Plans

The free tier model for SAP BTP lets you try out services in global accounts without any additional cost using the consumption-based commercial model and an [enterprise account](https://help.sap.com/docs/btp/sap-business-technology-platform/enterprise-accounts?version=Cloud).



We offer free service plans for many services within SAP BTP. Free service plans are limited in scope and capacity. They are designed to allow you and your team to explore new SAP BTP capabilities before committing to subscribing to a full capacity paid service.

The free tier model for SAP BTP is added automatically to new and existing contracts using the consumption-based commercial model. There, the free service plans are visible.

> ### Note:  
> The use of the consumption-based commercial model is subject to its availability in your country or region.

The consumption-based commercial model is available in the following flavors: the **CPEA** \(**Cloud Platform Enterprise Agreement**\) and **Pay-As-You-Go for SAP BTP**. For more information, see [What Is the Consumption-Based Commercial Model?](what-is-the-consumption-based-commercial-model-7047eb4.md).

To try out services that participate in the free tier model for SAP BTP, create a service instance using the **Free** service plan offered by the service.

> ### Tip:  
> To find out which services offer the free plans, see [Discover Free Services](using-free-service-plans-524e108.md#loio524e1081d8dc4b0f9d055a6bec383ec3__Find-FreeServices). Here, you also find information on how to identify the technical limitations of the free plan of each service. [Access Free Services](using-free-service-plans-524e108.md#loio524e1081d8dc4b0f9d055a6bec383ec3__Access-FreeServices) by assigning entitlements to subaccounts and creating service instances.

Once you reach the technical limits of a service and want to continue using it, you must move to a paid service plan. Upgrading an existing service instance from free tier to paid usually doesn't require creating a new service instance. Find out how to upgrade a service plan at [Upgrade to a Paid Service Plan](using-free-service-plans-524e108.md#loio524e1081d8dc4b0f9d055a6bec383ec3__Upgrade-FreeServices).

Use of free tier service plans is subject to additional terms and conditions as provided in the [Business Technology Platform Supplemental Terms and Conditions](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?tag=language:english&search=Supplement%20Business%20Technology%20Platform&sort=latest_desc) Only community support is available for Free service plans and these aren't subject to SLAs.



<a name="loio524e1081d8dc4b0f9d055a6bec383ec3__Find-FreeServices"/>

## Discover Free Services

Find out which services offer Free plans and what the limitations are.

Free Tier services can be explored in the service catalog of SAP Discovery Center. A free tier service appears as a "Free" plan offering for a service.

1.  Access the *Service Catalog* in the [SAP Discovery Center](https://discovery-center.cloud.sap/#/viewServices).

2.  In the *Categories* section, select *Free Tier Services*.

    ![](images/Discovery_Center_Free-Tier_Services_SUI_3aadc27.png)

3.  Select one of the services displayed in the catalog.

4.  Navigate to the *Pricing* tab.

    On this page, you can see all available plans for this service, including the limitations of each plan. Plans that participate in the free tier model for SAP BTP are labeled **Free**.




<a name="loio524e1081d8dc4b0f9d055a6bec383ec3__Access-FreeServices"/>

## Access Free Service Plans

To try out the free tier model for SAP BTP, you must entitle your subaccount for the free plan and create a service instance using this plan.

> ### Note:  
> The free tier model for SAP BTP is available for accounts that use the consumption-based commercial model.

1.  Enter your global account.

    For more information, see [Access the Cockpit](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/4e750660b72e4fd6b2485ffb0b3cbdca.html?version=Cloud).

2.  Configure entitlements for the subaccount in which you want to use the free service plans. Select the service and choose the free plan.

    For more information, see [Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/managing-entitlements-and-quotas-using-the-cockpit-c824874.md).

3.  Navigate into the subaccount and go to the *Service Marketplace*.

4.  Find the service you want to try out and select it.

    You find a description of the available service plans, including the free service plan. By clicking *More*, you find the scope and limitations of the free plan for this service.

5.  Create an instance of the service and select the free service plan.

    For more information, see [View and Manage Services from the Service Marketplace](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/affcc245c332433ba71917ff715b9971.html).


You can now start using this service.



<a name="loio524e1081d8dc4b0f9d055a6bec383ec3__Upgrade-FreeServices"/>

## Update to a Paid Service Plan

Once you've reached the limits of the free plan, you can upgrade the free service plan to a paid plan.

> ### Note:  
> The option to upgrade from free tier service plans to paid service plans is not yet available for all services and runtimes, such as Kyma. To use a paid service plan for Kyma runtime, you will need a new Kyma cluster. It is possible to have both - free and paid clusters - in parallel.

> ### Note:  
> It's not possible to switch from a paid plan to a free plan.

1.  In your subaccount, navigate to the *Instances and Subscriptions* page.

2.  Find the instance of the service and click <span class="SAP-icons-V5"></span> \(Actions\) and *Update*.

3.  In the *Update Instance* dialog, change the plan to a paid service plan.

4.  Click *Update Instance* to save your changes.


You can now use the service without the limitations of the free service plan.



<a name="loio524e1081d8dc4b0f9d055a6bec383ec3__Scope-FreeServices"/>

## Scope

-   The free tier model for SAP BTP is available for CPEA and Pay-As-You-Go for SAP BTP contracts. For more information, see [What Is the Consumption-Based Commercial Model?](what-is-the-consumption-based-commercial-model-7047eb4.md).

-   Services using the free tier service plans run on the same platform as paid services.

-   Services are technically limited. This limit depends on the service. You can find a description of the service plans in the *Service Marketplace* in the cockpit or in the [SAP Discovery Center](https://discovery-center.cloud.sap/#/viewServices).


