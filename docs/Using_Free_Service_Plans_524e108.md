<!-- loio524e1081d8dc4b0f9d055a6bec383ec3 -->

# Using Free Service Plans

The free tier model for SAP BTP lets you try out services in global accounts without any additional cost using the consumption-based commercial model.



We offer Free service plans for many services within SAP BTP. Free service plans are limited in scope and capacity. They are designed to allow you and your team to explore new SAP BTP capabilities before committing to subscribing to a full capacity paid service.

The free tier model for SAP BTP is added automatically to new and existing contracts using the consumption-based commercial model. There, the Free service plans are visible.

> ### Note:  
> The use of the consumption-based commercial model is subject to its availability in your country or region.

The consumption-based commercial model is available in two flavors; the **CPEA** \(**Cloud Platform Enterprise Agreement**\) and **Pay-As-You-Go for SAP BTP**. For more information, see [What Is the Consumption-Based Commercial Model?](What_Is_the_Consumption-Based_Commercial_Model_7047eb4.md).

To try out services that participate in the free tier model for SAP BTP, create a service instance using the **Free** service plan offered by the service.

> ### Tip:  
> To find out which services offer the Free plans, see [Discover Free Services](Using_Free_Service_Plans_524e108.md#loio524e1081d8dc4b0f9d055a6bec383ec3__Find-FreeServices). Here, you also find information on how to identify the technical limitations of the Free plan of each service.[Access Free Services](Using_Free_Service_Plans_524e108.md#loio524e1081d8dc4b0f9d055a6bec383ec3__Access-FreeServices) by assigning entitlements to subaccounts and creating service instances.

Once you reach the technical limits of a service and want to continue using it, you must move to a paid service plan. Upgrading an existing service instance from free tier to paid use is straightforward and doesn't require creating a new service instance. Find out how to upgrade a service plan at [Upgrade to a Paid Service Plan](Using_Free_Service_Plans_524e108.md#loio524e1081d8dc4b0f9d055a6bec383ec3__Upgrade-FreeServices).

Use of free tier service plans is subject to additional terms and conditions as provided in the [Business Technology Platform Supplemental Terms and Conditions](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?tag=language:english&search=Supplement%20Business%20Technology%20Platform&sort=latest_desc) Only community support is available for Free service plans and these aren't subject to SLAs.



<a name="loio524e1081d8dc4b0f9d055a6bec383ec3__Find-FreeServices"/>

## Discover Free Services

Find out which services offer Free plans and what the limitations are.

Free Tier services can be explored in the SAP Discovery Center's service catalog. A free tier service appears as a "Free" plan offering for a service.

1.  Access the *Service Catalog* in the [SAP Discovery Center](https://discovery-center.cloud.sap/#/viewServices).

2.  In the *Categories* section, select *Free Tier Services*.

    ![](images/Discovery_Center_Free-Tier_Services_SUI_3aadc27.png)

3.  Select one of the services displayed in the catalog.

4.  Navigate to the *Pricing* tab.

    On this page, you can see all available plans for this service, including the limitations of each plan. Plans that participate in the free tier model for SAP BTP are labeled **Free**.




<a name="loio524e1081d8dc4b0f9d055a6bec383ec3__Access-FreeServices"/>

## Access Free Service Plans

To try out the free tier model for SAP BTP, you must entitle your subaccount for the free plan and create a service instance using this plan.

1.  Enter your CPEA or Pay-As-You-Go for SAP BTP global account.

    For more information, see [Accessing the SAP BTP Cockpit](Regions_350356d.md#loio350356d1dc314d3199dca15bd2ab9b0e__access-cockpit).

2.  Configure entitlements for the subaccount in which you want to use the free service plans. Select the service and choose the free plan.

    For more information, see [Managing Entitlements and Quotas Using the Cockpit](Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md).

3.  Navigate into the subaccount and go to the *Service Marketplace*.

4.  Find the service you want to try out and select it.

    You find a description of the available service plans, including the free service plan. By clicking *More*, you find the scope and limitations of the free plan for this service.

5.  Create an instance of the service and select the free service plan.

    For more information, see [View and Manage Services from the Service Marketplace](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/affcc245c332433ba71917ff715b9971.html).


You can now start using this service.



<a name="loio524e1081d8dc4b0f9d055a6bec383ec3__Upgrade-FreeServices"/>

## Update to a Paid Service Plan

Once you've reached the limits of the free plan, you can easily upgrade the free service plan to a paid plan. No data or configurations are lost.

> ### Note:  
> It's not possible to switch from a paid plan to a free plan.

1.  In your subaccount, navigate to the *Instances and Subscriptions* page.

2.  Find the instance of the service and click   \(Actions\)  and *Update*.

3.  In the *Update Instance* dialog, change the plan to a paid service plan.

4.  Click *Update Instance* to save your changes.


You can now use the service without the limitations of the free service plan.



<a name="loio524e1081d8dc4b0f9d055a6bec383ec3__Scope-FreeServices"/>

## Scope

-   The free tier model for SAP BTP is available for CPEA and Pay-As-You-Go for SAP BTP contracts. For more information, see [What Is the Consumption-Based Commercial Model?](What_Is_the_Consumption-Based_Commercial_Model_7047eb4.md).

-   Services using the free tier service plans run on the same platform as paid services.

-   Services are technically limited. This limit depends on the service. You can find a description of the service plans in the *Service Marketplace* in the cockpit or in the [SAP Discovery Center](https://discovery-center.cloud.sap/#/viewServices).


