<!-- loio9cf4217c7a8042968694a345b4b95708 -->

# Retention of Audit Data written from Customer’s BTP Applications



<a name="loio9cf4217c7a8042968694a345b4b95708__section_bch_51m_wbc"/>

## Initial retention period

There is no free retention period for any customer-generated audit data. If you enable **Audit Log service, premium edition** service plan, the default period in which you can retain all audit data written from your customer applications built on top of SAP BTP is 90 days. For more information, see [Audit Log Write API for Customers](audit-log-write-api-for-customers-64e99bb.md).



<a name="loio9cf4217c7a8042968694a345b4b95708__section_mcr_xlp_xbc"/>

## Configurable Retention Period for Subaccounts

When you have enabled the **Audit Log service, premium edition** service plan, you can create a support ticket with component BC-CP-CF-SEC-AUDITLG to the Audit Log service to configure a custom retention period for storing your audit data.



<a name="loio9cf4217c7a8042968694a345b4b95708__section_ayd_xmp_xbc"/>

## Availability of the Write API for Customers

The functionality for writing customer-generated audit data as part of the **Audit Log service, premium edition** service plan, is currently available in the following regions:

-   Europe \(Frankfurt\)

-   Europe \(Frankfurt, EU Access\)

-   US East \(VA\)


If you want to use this functionality in another region, contact the Service owner to discuss the conditions for storing large volumes of audit data. **Audit Log service, premium edition** with its advanced functionalities is a commercialized consumption-based service plan. You can find the cost per Customer Written Volume stored in GB in [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/audit-log-service?commercialModel=cpea&tab=service_plan&region=all).



<a name="loio9cf4217c7a8042968694a345b4b95708__section_s3j_dpp_xbc"/>

## Revoking Custom Retention of SAP-Generated Audit Data



### Revoke Custom retention of an Existing Subaccount

To revoke custom retention, create a [support ticket](https://me.sap.com/getsupport) with component BC-CP-CF-SEC-AUDITLG to the Audit Log service to configure a flexible retention period for storing your audit data. In the support ticket provide the following data:

-   Subaccount ID\(s\) and Tenant ID\(s\) whose custom retention you want to revoke.

-   The date from which you want the revokation to be effective.


When you revoke custom retention all stored audit data which is older than 90 days is removed and charging for extra storage stops.

> ### Note:  
> Audit log data written from Customer's SAP BTP Applications is still charged per GB at the price in [SAP Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/audit-log-service?commercialModel=cpea&tab=service_plan&region=all) no matter the retention period in days.



### Revoke Custom retention of a Terminated Subaccount

Audit log data written by Customer’s SAP BTP Applications is removed immediately in case of a subaccount termination, as noted in [Delete a Subaccount](delete-a-subaccount-419dc3d.md).

> ### Note:  
> When you delete a subaccount, all audit log data written from your Customer’s SAP BTP Applications is automatically deleted.

> ### Note:  
> When you delete an auditlog premium service instance, the charging for storage doesn't stop automatically. To avoid accumulating further costs, you must either create a [support ticket](https://me.sap.com/getsupport) to revoke the custom retention period, or delete the subaccount.

