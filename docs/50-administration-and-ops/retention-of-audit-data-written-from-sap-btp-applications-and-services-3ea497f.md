<!-- loio3ea497f0483343ff892e7ecc12b6c0da -->

# Retention of Audit Data written from SAP BTP Applications and Services



<a name="loio3ea497f0483343ff892e7ecc12b6c0da__section_q3r_ngc_wbc"/>

## Free Retention Period

By default, you can retain the securely stored SAP-generated audit log data for your subaccount for 90 days, free of charge. After this period, the data is automatically deleted. Within this free default retention period, as an authorized stakeholder you can access, retrieve, and download the stored audit log data.



<a name="loio3ea497f0483343ff892e7ecc12b6c0da__section_ljp_wjc_wbc"/>

## Configurable Retention Period



### Enable *Audit Log service, premium edition*

To follow the Industry and Business Regulations requirements for a longer retention and storage of audit log data written on behalf of a customer's subaccount, and to be able to configure a custom retention period longer than the free 90 days, you must enable *Audit Log service, premium edition* service plan for your subaccount as follows:

1.  Entitle your subaccount with service auditlog and plan premium. For more information, see [Configure Entitlements and Quotas for Subaccounts](configure-entitlements-and-quotas-for-subaccounts-5ba357b.md)

2.  Create a service instance *auditlog* of plan *premium*. For more information, see [Creating Service Instances](../30-development/creating-service-instances-8221b74.md)




### Configure a Retention period

When you enable the *Audit Log service, premium edition* service plan, you can create a [support ticket](https://me.sap.com/getsupport) with component BC-CP-CF-SEC-AUDITLG to the Audit Log service to configure a flexible retention period for storing your audit data. In the support ticket provide the following data:

-   Subaccount ID\(s\) and Tenant ID\(s\) whose retention you want to extend.

-   Your desired retention period in days.

-   The date from which you want the configurable retention to be effective.




### Pricing

The premium edition with its advanced functionalities is a commercialized consumption based service plan, which prices per GB you can check in [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/audit-log-service?region=all&tab=service_plan&commercialModel=cpea).



<a name="loio3ea497f0483343ff892e7ecc12b6c0da__section_rpq_npc_wbc"/>

## Revoking Custom Retention of SAP-Generated Audit Data



### Revoke Custom retention of an Existing Subaccount

To revoke custom retention, create a [support ticket](https://me.sap.com/getsupport) with component BC-CP-CF-SEC-AUDITLG to the Audit Log service to configure a flexible retention period for storing your audit data. In the support ticket provide the following data:

-   Subaccount ID\(s\) and Tenant ID\(s\) whose custom retention you want to revoke.

-   The date from which you want the revokation to be effective.


When you revoke custom retention all stored audit data which is older than 90 days is removed and charging for extra storage stops.



### Revoke Custom retention of a Terminated Subaccount

SAP-generated audit log data for a terminated subaccount deleted when it is older than 90 days. The 90-day retention period is kept free of charge for audit purposes.

> ### Note:  
> When you delete a subaccount, all audit log data older than 90 days is automatically deleted.

> ### Note:  
> When you delete an auditlog premium service instance, the charging for storage doesn't stop automatically. To avoid accumulating further costs, you must either create a [support ticket](https://me.sap.com/getsupport) to revoke the custom retention period, or delete the subaccount.

