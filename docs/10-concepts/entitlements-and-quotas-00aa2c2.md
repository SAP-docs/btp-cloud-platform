<!-- loio00aa2c23479d42568b18882b1ca90d79 -->

# Entitlements and Quotas

When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_fx5_nzd_klb"/>

## Services and Service Plans

On SAP BTP, all external dependencies such as databases, messaging systems, files systems, and so on, are **services**. In this context, multitenant applications and environments are considered services.

Each service has one or more **service plans** available. A service plan is the representation of the costs and benefits for a given variant of a particular service. For instance, a database may be configured with various "T-shirt sizes", each of which is a different service plan.



![Relationships between Services Plans, Entilements, and Quotas](images/Service_Plan_1_cd5d379.png)



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_pkd_pyd_klb"/>

## Entitlements

An **entitlement** is your right to provision and consume a resource. In other words, entitlements are **the service plans** that you're entitled to use.

The entitlements that are available in your enterprise account are determined by the commercial model used by your global account:

-   In the consumption-based commercial model, your organization buys an entitlement to all current and future SAP BTP services eligible under this model. During your contract period, you have full flexibility to switch services on and off and change between them as your business needs. For more information, see [What Is the Consumption-Based Commercial Model?](what-is-the-consumption-based-commercial-model-7047eb4.md).

-   In the subscription-based commercial model, your organization is authorized to use only the services you have subscribed to, as per your commercial agreement. To access additional services at an extra cost, you can modify your contract through your sales representative or account executive. For more information, see [What Is the Subscription-Based Commercial Model?](what-is-the-subscription-based-commercial-model-239b6e0.md).




<a name="loio00aa2c23479d42568b18882b1ca90d79__section_fpq_pyd_klb"/>

## Quotas

A **quota** represents the numeric quantity of a service plan that you're entitled to consume in your global account and its subaccounts.

From the perspective of your SAP BTP global account contract, the global quota of a service plan can be defined as either fixed or unlimited:

-   **Fixed quota:** The quota or allowance of the service plan is the upper limit at which the plan can be consumed collectively across your global account. This is typical of global accounts that have the **subscription-based** commercial model agreement.

-   **Unlimited quota:** There is no upper limit to how much the service plan can be used collectively across your global account. This is typical of most services that are eligible to global accounts with a **consumption-based** commercial model agreement \(Cloud Platform Enterprise Agreement \(CPEA\) and Pay-As-You-Go for SAP BTP\). At the end of the month, the number of units used determines how much you are charged.


Regardless of whether the global quota of a plan on the global account level is fixed or unlimited, the specifics and properties of each plan determines how its quota can be distributed by the global account admin to the subaccounts in your global account. There are two types of quota assignments:

-   **Numeric assignments:** The global account admin assigns the plan to a subaccount and specifies the maximum quantity of units from the global quota that can be consumed by the subaccount. Admins can use this assignment to limit users from exceeding a specific quota for cost-controlling purposes. Typically, but not always, the assigned quota is directly related to the number of instances that can be created in subaccounts for the assigned plan.

-   **Non-numeric assignments:** The global account admin does not assign a specific quantity but simply grants access to the specific plan by assigning the plan to the subaccount. When the plan is assigned, it's available for use by the subaccount. SaaS application assignments are typically non-numeric, whereby a subaccount can either subscribe to the app or not. For services that fall into this category of non-numeric assignments, there is usually no limit to the number of instances that can be created.


See also the sections below and [Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/managing-entitlements-and-quotas-using-the-cockpit-c824874.md).



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_lqp_5b2_klb"/>

## Distribution and Usage of Entitlements and Quotas

Entitlements and quotas are purchased and managed at global account level, from where they’re distributed to subaccounts, which consume them.

> ### Tip:  
> You can also distribute entitlements to directories, and then redistribute to the subaccounts under the directories; however, this is optional. By default, directories are not enabled to manage entitlements. This feature needs to be enabled per directory by the global account administrator.

When assigning entitlements and quotas to directories, you also have the option to automatically assign a set amount of quota to each new subaccount added to the directory. This option doesn’t apply to subaccounts that are already in the directory when you select this option. The quota you assigned to the directory is then gradually distributed to all subaccounts that you add to that directory, until it runs out. Once the directory quota runs out, if you add a new subaccount to that directory it won't get any quota automatically anymore.

Since directories are only a way of grouping subaccounts, you can't consume a service at directory level. However, when you assign entitlements and quotas from the global account to a directory, the quota you assigned is shown as used, even if there are no subaccounts in that directory to consume the quota. You can think of it as a way to "reserve" quota and make sure it's not assigned to other subaccounts or directories.

When you remove quotas or assignments from a directory or subaccount, they become available again at global account level and can be assigned to other directories or subaccounts; unless the quota is reserved for a given directory then the freed quota remains available only to that directory and its subaccounts.

> ### Note:  
> Before a subaccount admin can enable a quota-based environment, such as Kyma, the subaccount admin must first assign the environment as an entitlement to the subaccount. Other environments, such as Cloud Foundry, are available by default to all subaccounts, and therefore are not available as entitlements.

For more information, see:

-   [Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/configure-entitlements-and-quotas-for-subaccounts-5ba357b.md)
-   [Configure Entitlements and Quotas for Directories](../50-administration-and-ops/configure-entitlements-and-quotas-for-directories-37f8871.md)



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_lqj_qyd_klb"/>

## Quota Plans

In the Cloud Foundry environment, you can further distribute the quotas that are allocated to a subaccount. This is done by creating space quota plans and assigning them to the spaces.

Space quota plans are optional and are used to limit how much each space can use, not to enable. If you don't create any space quota plans, all spaces in a subaccount using the Cloud Foundry environment have access to all entitlements and quotas in that subaccount. This means that one space could use up all the quota in a subaccount. If you want to prevent that from happening and set a limit to how much each space can use from the total quota available in the subaccount, you can use quota plans and assign them to spaces.

For more information on space quota plans in the Cloud Foundry environment, see:

-   [https://docs.cloudfoundry.org/adminguide/quota-plans.html](https://docs.cloudfoundry.org/adminguide/quota-plans.html)
-   [Managing Space Quotas](../50-administration-and-ops/managing-space-quotas-4e5f0ee.md)



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_x2p_ryd_klb"/>

## Resource Providers

SAP BTP allows you to connect your global account in the SAP BTP Cockpit to your provider account from a non-SAP cloud vendor, and consume remote service resources that you already own and which are supported by SAP through this channel.

For example, if you’re subscribed to Amazon Web Services \(AWS\) and have already purchased services, such as PostgreSQL, you can register the vendor as a resource provider in SAP BTP and consume this service across your subaccounts together with other services offered by SAP.

SAP BTP currently supports the following vendors and their consumable services:


<table>
<tr>
<th valign="top">

Cloud Vendor

</th>
<th valign="top">

Supported Services

</th>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

[Amazon Relational Database Service \(RDS\) - PostgreSQL](https://help.sap.com/viewer/product/PostgreSQL/Cloud/en-US) 

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

[Azure Database for PostgreSQL](https://help.sap.com/viewer/product/PostgreSQL/Cloud/en-US).

</td>
</tr>
</table>

After you configure a new resource provider, its supported services are added as entitlements in your global account. In the *Entitlements* page in the cockpit, you can then allocate the required services and quotas to the relevant directories and subaccounts in your global account.

For more information, see [Managing Resource Providers](../50-administration-and-ops/managing-resource-providers-e2c250d.md).

**Related Information**  


[Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/managing-entitlements-and-quotas-using-the-cockpit-c824874.md "When you purchase an enterprise account, you are entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[**Tutorial**: Manage Entitlements on SAP BTP Trial](https://developers.sap.com/tutorials/cp-trial-entitlements.html)

[**Troubleshooting**: Entitlement and Quota Problems](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2065/actions/26547:27066)

