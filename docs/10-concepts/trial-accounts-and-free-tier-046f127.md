<!-- loio046f127f2a614438b616ccfc575fdb16 -->

# Trial Accounts and Free Tier

Explore the different options for trying out SAP BTP.



<a name="loio046f127f2a614438b616ccfc575fdb16__section_ykc_swd_4rb"/>

## Trial Account or Free Tier Offering: When to Use Which?

Before setting up your account, you need to decide which free offering for SAP BTP is suitable for your needs:

-   **Pay-As-You-Go or CPEA accounts with free tier service plans** are open to customers, partners, and individual developers and let you try out SAP BTP for free without time limits. These account types enable you to test your scenarios and generally offer the option to upgrade to paid service plans. These accounts also allow you to store data long-term and move projects to production. You also get access to our community, including free technical resources such as tutorials and blog posts. For more information, see [Enterprise Accounts](enterprise-accounts-171511c.md) and [Using Free Service Plans](using-free-service-plans-524e108.md).

    You can self-register for an enterprise account with free tier service plans. For more information, see [Get an Account on SAP BTP to Try Out Free Tier Service Plans](https://developers.sap.com/tutorials/btp-free-tier-account.html).

    > ### Note:  
    > Only community support is available for free tier service plans and these are not subject to SLAs.

    > ### Note:  
    > The option to upgrade from free tier service plans to paid service plans is not yet available for all services and runtimes, such as Kyma. See [Using Free Service Plans](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/524e1081d8dc4b0f9d055a6bec383ec3.html#loio524e1081d8dc4b0f9d055a6bec383ec3__Upgrade-FreeServices) to read more about upgrading from free tier service plans to paid service plans.

-   A **trial account** lets you try out SAP BTP for free for 90 days. The services provided for the trial account allow restricted use of the platform resources and services. Access is open to everyone. Trial accounts are intended for personal exploration, your own non-productive testing, and evaluation of the services in accordance with [SAP BTP trial terms and conditions](https://accounts.sap.com/ui/public/viewTextResource?scenario=1b5ff22b-ac85-466f-9644-833d07e77d5e&resourceType=RESOURCE_TERMS_OF_USE&locale=en_US). A SAP BTP trial account must not be used for production use or team development. You are not permitted to use the trial account in any productive or commercial manner.

    You can self-register for a trial account. For more information on how to do that, see [Get a Free Account on SAP BTP Trial](https://developers.sap.com/tutorials/hcp-create-trial-account.html)




<a name="loio046f127f2a614438b616ccfc575fdb16__section_yq4_ngy_gwb"/>

## Free Tier and Always Free Tags in the SAP Discovery Center

In the [SAP Discovery Center service catalog overview](https://discovery-center.cloud.sap/viewServices?provider=all&regions=all), some services display the tag *Free Tier*, which indicates the service is offering a free tier service plan. Some services display the tag *Always Free*, which indicates the service is offering a service plan that comes free of additional charges, as it is already included in your overall SAP BTP contract. You can use the filter function of the SAP Discovery Center to filter for services that offer *Free Tier* and *Always Free* plans. The *Always Free* service plans include the following note in their service plan description: "This service plan is included in the overall SAP Business Technology Platform contract".

> ### Note:  
> *Always Free* service plans might not be available in all regions or for all providers.



<a name="loio046f127f2a614438b616ccfc575fdb16__section_trial-lifecycle"/>

## Trial Lifecycle

-   **Use your SAP BTP trial account:**

    Familiarize yourself with the [Trial Scope](trial-accounts-and-free-tier-046f127.md#loio046f127f2a614438b616ccfc575fdb16__section_trial-scope) or try out one of our [Starter Scenarios](https://developers.sap.com/tutorial-navigator.html?tag=tutorial:topic/cp-starter-scenario) on the [Tutorial Navigator](https://developers.sap.com/tutorial-navigator.html?tag=products:technology-platform/sap-business-technology-platform).

-   **Extend your SAP BTP trial account in intervals:**

    -   Your 90-day trial period is divided in intervals. If you sign in to your trial account regularly, the intervals are extended automatically for you by up to 30 days or until your overall 90-day trial is finished.

    -   Extend your trial account interval by clicking *Extend Trial Account* in the pop-up window that appears once 30 days have passed.

    -   If you don't sign in to your trial account for 30 days or more, your account will be suspended. You won't be able to use applications or services. However, your account will not be deleted yet. To unsuspend your trial account, click *Extend Trial Account* in the pop-up window that appears when you try to sign in. You'll then be able to use your account again, provided that there are still days left in your overall 90-day trial period.

    -   **Delete your SAP BTP trial account:**

        After 90 days, your trial account is automatically deleted. But if you want to proactively delete your SAP BTP trial account, you can navigate to the global accounts scope and select the Account Explorer page, then click the *Delete Trial Account* button.

        -   If you want to continue to use an SAP BTP trial account after deletion, you need to set up a new account.

        -   If you want to explore SAP BTP without time limit, create an enterprise account with free tier service plans allowing you to test your scenarios. See: [Get an Account on SAP BTP to Try Out Free Tier Service Plans](https://developers.sap.com/tutorials/btp-free-tier-account.html).




> ### Caution:  
> Environments enabled on your trial account may not be valid for your whole trial period. To learn about the validity period for the Kyma environment, see [About the Trial Account](../20-getting-started/about-the-trial-account-c4fff0f.md).



<a name="loio046f127f2a614438b616ccfc575fdb16__section_trial-scope"/>

## Trial Scope

-   A trial account enables you to explore the basic functionality of SAP BTP.

-   SAP BTP trial accounts use cloud management tools feature set B. For more information, see [Cloud Management Tools — Feature Set Overview](cloud-management-tools-feature-set-overview-caf4e4e.md).

-   SAP BTP trial accounts are available in several regions. For more information, see [Regions](regions-350356d.md).

-   You can create directories in your trial account. For more information, see [Managing Directories Using the Cockpit \[Feature Set B\]](../50-administration-and-ops/managing-directories-using-the-cockpit-feature-set-b-f495ac1.md)

-   You can use productive and beta services. To consume beta services, you must enable the subaccount for beta features during the subaccount creation or when you edit the subaccount details.

-   You can manage security users in your subaccounts by assigning them role collections. For more information, see [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   A trial account includes 4 GB of memory for applications.

-   You can use 8 GB of instance memory.

-   There are 10 total routes and 40 total services available.

-   You can use 2 configured on-premise systems with the Cloud connector.

-   There’s no service level agreement with regards to the availability of the platform.

-   You can use HDI containers in a shared SAP HANA database \(only available on cf-us10\).

-   For cleanup purposes, applications stop automatically on a daily basis. You need to manually restart them when needed.

    > ### Note:  
    > Applications are stopped at midnight \(or some time later depending on server load\) relative to the region in which you created your trial account. If you're working in a time zone that is far from the region where your trial account was created, then your applications may stop during business hours.


**Related Information**  


[Getting Started with a Trial Account in the Cloud Foundry Environment](../20-getting-started/getting-started-with-a-trial-account-in-the-cloud-foundry-environment-e50ab7b.md "Quickly get started with a trial account.")

 <?sap-ot O2O class="- topic/link " href="720c423ef1a8498ab690cf0e5512ba50.xml" text="" desc="" xtrc="link:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/046f127f2a614438b616ccfc575fdb16.xml" ?> 

[Getting Started with a Trial Account in the Kyma Environment](../20-getting-started/getting-started-with-a-trial-account-in-the-kyma-environment-ccb83c7.md "Quickly get started with a trial account in the Kyma environment.")

