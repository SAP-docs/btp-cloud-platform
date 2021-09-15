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



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_fpq_pyd_klb"/>

## Quotas

A **quota** represents the numeric quantity that defines the maximum allowed consumption of a resource. In other words, **how much** of a service plan you're entitled to use.

Some service plans use numeric quota, which means that you can increase or decrease the number of units available in a subaccount. Depending on the service, these units represent different things and may impact the number of service instances, applications, or routes you can have in a subaccount.

There are also service plans where the quota is shown as “limited”. The unit that is metered and billed for service plans with limited quota depends on the service. In that case, you can entitle that service to multiple subaccounts without having to worry about how much of it to distribute to each subaccount. You can think of assigning entitlements for such service plans as “enabling” or "allowing" subaccounts to use them.

For more information, see [Managing Entitlements and Quotas Using the Cockpit](Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md).



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_uqw_t12_klb"/>

## Distribution and Usage of Entitlements and Quotas \[Feature Set A\]

Entitlements and quotas are purchased and managed at global account level, from where they’re distributed to subaccounts, which consume them.

When you remove quotas or entitlements from a subaccount, they become available again at global account level and can be assigned to other subaccounts.

For example, let's say you've purchased 10 units of service plan <x\> for your global account. If you have 3 subaccounts in your global account and you assign all 10 units to only one of them, the other 2 subaccounts won't be able to use that service plan at all. You would have to remove some quota from that one subaccount and then entitle that service plan to the other subaccount, distributing the globally available quota among them.



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_lqp_5b2_klb"/>

## Distribution and Usage of Entitlements and Quotas \[Feature Set B\]

Entitlements and quotas are purchased and managed at global account level, from where they’re distributed to directories and/or subaccounts, which consume them.

When assigning entitlements and quotas to directories, you also have the option to automatically assign a set amount of quota to each new subaccount added to the directory. This option doesn’t apply to subaccounts that are already in the directory when you select this option. The quota you assigned to the directory is then gradually distributed to all subaccounts that you add to that directory, until it runs out. Once the directory quota runs out, if you add a new subaccount to that directory it won't get any quota automatically anymore.

> ### Tip:  
> Not all directories manage their own entitlements. This feature needs to be enabled per directory by the directory administrator.

Since directories are only a way of grouping subaccounts, you can’t consume a service at directory level. However, when you assign entitlements and quotas from the global account to a directory, the quota you assigned is shown as used, even if there are no subaccounts in that directory to consume the quota. You can think of it as a way to "reserve" quota and make sure it's not assigned to other subaccounts or directories.

When you remove quotas or entitlements from a directory or subaccount, they become available again at global account level and can be assigned to other directories or subaccounts.

> ### Note:  
> Before a subaccount admin can enable a quota-based environment, such as Kyma, the subaccount admin must first assign the environment as an entitlement to the subaccount. Other environments, such as Cloud Foundry, are available by default to all subaccounts, and therefore are not available as entitlements.



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_lqj_qyd_klb"/>

## Quota Plans

In the Cloud Foundry environment, you can further distribute the quotas that are allocated to a subaccount. This is done by creating space quota plans and assigning them to the spaces.

Space quota plans are optional and are used to limit how much each space can use, not to enable. If you don't create any space quota plans, all spaces in a subaccount using the Cloud Foundry environment have access to all entitlements and quotas in that subaccount. This means that one space could use up all the quota in a subaccount. If you want to prevent that from happening and set a limit to how much each space can use from the total quota available in the subaccount, you can use quota plans and assign them to spaces.

For more information on space quota plans in the Cloud Foundry environment, see:

-   [https://docs.cloudfoundry.org/adminguide/quota-plans.html](https://docs.cloudfoundry.org/adminguide/quota-plans.html)
-   [Managing Space Quota Plans](Managing_Space_Quota_Plans_4e5f0ee.md)



<a name="loio00aa2c23479d42568b18882b1ca90d79__section_x2p_ryd_klb"/>

## Resource Providers

SAP BTP allows you to connect your global account in the SAP BTP Cockpit to your provider account from a non-SAP cloud vendor, and consume remote service resources that you already own and which are supported by SAP through this channel.

For example, if you’re subscribed to Amazon Web Services \(AWS\) and have already purchased services, such as PostgreSQL, you can register the vendor as a resource provider in SAP BTP and consume this service across your subaccounts together with other services offered by SAP.

SAP BTP currently supports the following vendors and their consumable services:


<table>
<tr>
<th>

Cloud Vendor



</th>
<th>

Supported Services



</th>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

 [Amazon Relational Database Service \(RDS\) - PostgreSQL](https://help.sap.com/viewer/product/PostgreSQL/Cloud/en-US) 



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

 [Azure Database for PostgreSQL](https://help.sap.com/viewer/product/PostgreSQL/Cloud/en-US).



</td>
</tr>
</table>

After you configure a new resource provider, its supported services are added as entitlements in your global account. In the *Entitlements* page in the cockpit, you can then allocate the required services and quotas to the relevant directories and subaccounts in your global account.

For more information, see [Managing Resource Providers](Managing_Resource_Providers_e2c250d.md).

**Related Information**  


[Managing Entitlements and Quotas Using the Cockpit](Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md "When you purchase an enterprise account, you are entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[**Tutorial**: Manage Entitlements on SAP BTP Trial](https://developers.sap.com/tutorials/cp-trial-entitlements.html)

[**Troubleshooting**: Entitlement and Quota Problems](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2065/actions/26547:27066)

