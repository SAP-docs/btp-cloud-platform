<!-- loioe3baa5f1a0c64c44aac8ab3ea3d1b500 -->

# Audit Log Viewer for the Cloud Foundry Environment

The SAP Audit Log Viewer service displays the audit logs for your Cloud Foundry account, produced by SAP applications and services you’ve subscribed to.

The UI allows you to:

-   read the audit logs written for your account in selected time frame. The SAP Audit Log Viewer service displays 500 audit log records per request. If you want to view more audit log records, specify a shorter time frame.

-   display more detailed information on each single audit log record.

-   filter the retrieved client-side chunk for certain strings.

-   download the audit logs in the selected time frame.


The default displayed columns are:

-   User - the person that has executed the event reflected in the written audit log.

-   Time - creation time for the audit log message.

-   Message - summary of the audit log message that is written.

-   Category - audit log message category. The four-supported audit log message categories are:

    -   `audit.security-events`

    -   `audit.configuration`

    -   `audit.data-access`

    -   `audit.data-modification`



The appearance of the UI can be modified by selecting the rows to be displayed on a single page, as well as the columns that you want to be visible.



<a name="loioe3baa5f1a0c64c44aac8ab3ea3d1b500__section_er5_g3k_kfb"/>

## SAP Audit Log Viewer service Subscription



### Prerequisites

Before subscribing to the Audit Log Viewer service, you need to configure the relevant entitlement in your Global Account. For more information, see**Related Information**.



### Subscribe to Audit Log Viewer service

To use the SAP Audit Log Viewer service, subscribe to it using the SAP BTP cockpit in the *Services* \> *Instances and Subscriptions* \> *Subscriptions* tab of your subaccount. Once you're subscribed, select *Go to Application* to open the SAP Audit Log Viewer service and log in there.



<a name="loioe3baa5f1a0c64c44aac8ab3ea3d1b500__section_cbf_43k_kfb"/>

## SAP Audit Log Viewer service Access

To retrieve the audit logs for your subaccount using the SAP Audit Log Viewer service, you need to have proper authorizations. See [https://docs.cloudfoundry.org/concepts/roles.html\#permissionsInformation](https://docs.cloudfoundry.org/concepts/roles.html#permissionsInformation), published on a non-SAP site.

1.  Create a `RoleCollection`.

2.  Search for roles with the name "Auditlog\_Auditor" and select both entries with the following application identifiers:
    -   auditlog-management!b\*

    -   auditlog-viewer!t\*

3.  Assign the role to a user or create a rule to assign it to users based on the SAML Assertion coming from the IDP.

> ### Note:  
> Only account members with the `Security Administrator` role are authorized to edit application authorizations.

**Related Information**  


[Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md "When you purchase an enterprise account, you are entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

