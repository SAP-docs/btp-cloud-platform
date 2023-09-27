<!-- loio7a3e39622be14413b2a4df7c02ca1170 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Subscribe to Multitenant Applications Using the Cockpit

Subscribe to multitenant applications from the *Service Marketplace* page in the SAP BTP cockpit.



<a name="loio7a3e39622be14413b2a4df7c02ca1170__prereq_acw_hml_pkb"/>

## Prerequisites

-   If you're subscribing to an application provided by SAP:

    -   If your global account uses the subscription-based commercial model, then you must have purchased SaaS licenses for the applications you want to consume. See [https://cloudplatform.sap.com/pricing.html](https://cloudplatform.sap.com/pricing.html). You can also contact us on [SAP BTP](https://cloudplatform.sap.com/index.html) or via an SAP sales representative.

        > ### Note:  
        > If your global account is licensed with the consumption-based commercial model, then you are eligible to subscribe to any multitenant application that is available to this model.

    -   You have created a multi-environment subaccount. See [Create a Subaccount](create-a-subaccount-05280a1.md).


-   If you are an application owner who is subscribing consumer tenants to your own multitenant application that you created in the Cloud Foundry environment:

    -   The application must be deployed to your provider subaccount, configured, and registered as described in [Developing Multitenant Applications in the Cloud Foundry Environment](../30-development/developing-multitenant-applications-in-the-cloud-foundry-environment-5e8a2b7.md).

    -   You have created a multi-environment subaccount for each application consumer in the region in which the application is deployed. See [Providing Multitenant Applications to Consumers in the Cloud Foundry Environment](../30-development/providing-multitenant-applications-to-consumers-in-the-cloud-foundry-environment-7a013f1.md).


-   \[Feature Set A\] You are an administrator of the global account.

-   \[Feature Set B\] You are an admininistrator of the subaccount.

-   \[Feature Set B\] Your subaccount is entitled to the multitenant application. See [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).




<a name="loio7a3e39622be14413b2a4df7c02ca1170__context_ecw_hml_pkb"/>

## Context

The instructions provided here apply whether you are an SAP customer subscribing to an application provided by SAP or you are an application owner who is sharing your multitenant application with your consumers.



<a name="loio7a3e39622be14413b2a4df7c02ca1170__steps_fcw_hml_pkb"/>

## Procedure

1.  Open your global account in the cockpit.

2.  Do one of the following:

    -   If you are subscribing to an SAP application, open your subaccount.
    -   If you are sharing your multitenant application with other consumers in your global account, open the subaccount of each consumer.

    See [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md).

3.  In the navigation area of each subaccount, choose *Services* \> *Service Marketplace*.

    All resources you are entitled to consume in the subaccount appear as tiles.

    > ### Note:  
    > To create a subscription, you need to open the *Create* wizard. There are 2 ways to reach this wizard, either from the *Service Marketplace* or from the *Instances and Subscriptions* page.
    > 
    > In steps 3, 4, 5, and 6, we describe how to reach the wizard from the *Service Marketplace* page.
    > 
    > This way is useful if you want to get an overview of all the applications your subaccount is entitled to use and if you want to get more details about the available plans before you create a subscription.
    > 
    > If you already know these details, select *Services* \> *Instances and Subscriptions*, click on *Create* in the top-right corner, and skip to step 7 to learn about the wizard.

4.  In the filters area, select the *All Types* filter, and from the dropdown menu, select *Application*.

    You can use other filters to narrow down your search by the environments for which the application is available, capabilities, and its status.

    *Active* status means you are currently subscribed to that application.

5.  Click the application name to open its *Overview* page.

    There, you can find more information about the application including all the available plans.

    > ### Tip:  
    > You can also create a new subscription without opening its overview by selecting the three dots in the top-right corner of the tile.

6.  Choose *Create*.

7.  In the wizard that opens, select one of the plans of type subscription and choose *Create*.

    > ### Note:  
    > The wizard contains more than one step if additional subscription configuration input parameters are provided by the app provider.

    A confirmation popup appears with the link to the *Instances and Subscriptions* page, where you can follow the status of your new subscription under the *Subscriptions* table.

    The *Go to Application* link becomes available once the subscription is activated. Choose the link to launch the application and obtain its URL.

    To find the link, either click on the application's name or click on the <span class="SAP-icons"></span> \(Go to Application\) icon in the *Application* column.

    > ### Tip:  
    > To update an existing subscription plan, select the three dots at the end of the subscription row, and from the menu, select *Update*.

    > ### Note:  
    > You can update a subscription plan only if additional plans for the subscription are entitled to the subaccount you're using and if your subscription is eligible for a plan update.

    > ### Tip:  
    > To remove an existing subscription, select the three dots at the end of the subscription row, and from the menu, select *Delete*. All data related to the multitenant application will be deleted in the respective subaccount.

8.  **Optional:** Assign labels to the subscription to make it searchable and organized within the subaccount according to various criteria.

    1.  In the navigation area, choose *Services* \> *Instances and Subscriptions*.

    2.  Find the subscription to which you want to assign labels under the *Subscriptions* section of the page.

    3.  Select the actions \(<span class="SAP-icons"></span>\) menu and from the dropdown list, choose *Add Labels*.

        > ### Note:  
        > If there are already labels assigned to the subscription, the action becomes *Change Labels*.
        > 
        > You can see the existing labels under the *Labels* column.
        > 
        > If you do not see the column, unhide it by clicking on :gear:.


    For more information, see [Labels \[Feature Set B\]](../10-concepts/account-model-8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e).




<a name="loio7a3e39622be14413b2a4df7c02ca1170__postreq_icw_hml_pkb"/>

## Next Steps

1.  Configure user access to the application.

    See [Working with Role Collections](working-with-role-collections-393ea0b.md).

2.  If the application consumer isn't the subaccount owner or administrator, provide the consumer-specific URL of the application to the consumer or the users of the application.


**Related Information**  


[Working with Multitenant Applications Using the btp CLI](working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

