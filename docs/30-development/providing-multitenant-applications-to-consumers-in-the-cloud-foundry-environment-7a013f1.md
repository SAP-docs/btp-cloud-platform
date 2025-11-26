<!-- loio7a013f1d89f34a0084ea3d9a8bb2adbd -->

# Providing Multitenant Applications to Consumers in the Cloud Foundry Environment

Once you have built a multitenant application in the Cloud Foundry environment using SAP BTP, you can then share the application with multiple consumers, such as business units in your organization. 





<a name="loio7a013f1d89f34a0084ea3d9a8bb2adbd__section_ty2_spn_s2b"/>

## Consumer Subaccounts and Subaccount Members

To use multitenancy in the Cloud Foundry environment in SAP BTP, the application provider must create a subaccount for each consumer in the same global account where the multitenant application is deployed.

The multitenant application is deployed to one subaccount only, which is the hosting subaccount of the application provider. Consumers simply subscribe to the provider application from their subaccount through the SAP BTP cockpit, the SAP BTP command line interface, or dedicated REST APIs.

The application provider is responsible for:

-   Creating and managing the tenant subaccounts.

-   Setting up the necessary role access authorizations.

-   Subscribing each tenant to the application.


Typically, consumers of multitenant applications provided by a non-SAP application owner, such as an IT department of an organization, do not own or have access to their tenant subaccount.

  
  
**Account setup for an application owner provisioning a multitenant application to its consumers.**

![](images/CF_Subscriptions_with_External_Providers_-_Detailed_a65f2d5.png "Account
					setup for an application owner provisioning a multitenant application to its consumers.")

Subaccount members are users who are registered via the SAP ID service. Subaccount members may have different privileges regarding the operations that are possible for a subaccount \(for example, subaccount administration, deploy, start, and stop applications\).

The subaccount-specific configuration allows application providers to adapt the consumer subaccounts to their specific needs.



<a name="loio7a013f1d89f34a0084ea3d9a8bb2adbd__section_aq3_sqn_s2b"/>

## What Do You Need to Do, and How?

Once you have developed, deployed, configured, and registered your multitenant application, your account administrator is ready to do the following.

1.  Create a subaccount in your global account for each application consumer.

    See [Create a Subaccount](../50-administration-and-ops/create-a-subaccount-05280a1.md).

2.  Subscribe each consumer subaccount to the hosted application deployed in the provider account.

    See:

    -   [Subscribe to Multitenant Applications Using the Cockpit](../50-administration-and-ops/subscribe-to-multitenant-applications-using-the-cockpit-7a3e396.md)
    -   [Working with Multitenant Applications Using the btp CLI](../50-administration-and-ops/working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md)
    -   Subscribe the tenant to an application using the REST API. For more information, see [Using SAP SaaS Provisioning Service APIs to Manage Multitenant Applications](using-sap-saas-provisioning-service-apis-to-manage-multitenant-applications-ed08c7d.md)

3.  Set up application roles and assign users.

    See  <?sap-ot O2O class="- topic/xref " href="56a71531fc154717bf221f9e293ba215.xml" text="" desc="" xtrc="xref:5" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/7a013f1d89f34a0084ea3d9a8bb2adbd.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .




<a name="loio7a013f1d89f34a0084ea3d9a8bb2adbd__section_f4t_q52_vqb"/>

## Viewing and Managing of Your Multitenant Application’s Subscriptions

Once you've provided your multitenant application to consumers to subscribe to it, you can view and manage all the subscriptions by using a dedicated interface called SAP BTP subscription management dashboard.

For more information, see [Using the Subscription Management Dashboard](using-the-subscription-management-dashboard-434be69.md).

