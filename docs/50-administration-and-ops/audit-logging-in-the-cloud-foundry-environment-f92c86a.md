<!-- loiof92c86ab11f6474ea5579d839051c334 -->

# Audit Loggingin the Cloud Foundry Environment

In this section, you can find information for audit log functionalities in the Cloud Foundry environment.

SAP Audit Log is a core, security, and compliance-based SAP BTP service to provide means for audit purposes. The following features of Audit Log Service are available for SAP BTP Applications and Services:

-   With the default features, you have:

    -   Written compliance audit data from SAP BTP services and applications, through oAuth2 service plan.
    -   Audit data securely stored for a default retention time of 90 days with no additional costs applied.

    -   Retrieval of audit data within the default retention period ensured as part of the Auditlog Management Service.


-   With the advanced features you can:

    -   Write audit data from your owned BTP applications.

    -   Configure the retention period.



The advanced features enable you to comply with the SAP Product Standards and Business Industry regulations you're subject to. To enable the advanced features, you need to enable the premium edition service plan, where additional costs are applied based on the consumed volumes.

Audit logs are a special type of logs. They represent security-relevant chronological records that provide documentary evidence for an event or activity. The following table gives you a better understanding what is the difference between audit logs, activity logs, and application logs. The SAP Audit Log only stores audit logs written by SAP BTP services, when you take action over your account data.

![](images/Log_type_differences_325f42d.png)

The SAP Audit Log stores audit logs representing different actions taken over your account and/or data. There are predefined audit categories, which represent such kinds of actions:

-   Data protection and privacy related

    -   *audit.data-access* read-access logging records for access to sensitive personal data;

    -   *audit.data-modification* data modification logging records for sensitive personal data.


    Security related

    -   *audit.security-events* logging of general security events like login, logout, and other;

    -   *audit.configuration* logging of security critical configuration changes.



See [Change Logging and Read-Access Logging](../60-security/change-logging-and-read-access-logging-93fac8d.md).

If your subaccount audit logs contain other log types or information, create a support ticket with component BC-CP-CF-SEC-AUDITLG.

**Related Information**  


[Audit Log Retrieval API Usage for Subaccounts in the Cloud Foundry Environment](audit-log-retrieval-api-usage-for-subaccounts-in-the-cloud-foundry-environment-30ece35.md "The audit log retrieval API allows you to retrieve the audit logs for your SAP BTP Cloud Foundry environment subaccount.")

[Audit Log Retention for the Cloud Foundry Environment](audit-log-retention-for-the-cloud-foundry-environment-adaefa6.md "The audit log data is stored on a subaccount level. The access to the stored audit log data is strictly restricted - only authorized stakeholders can preview, retrieve, and download their audit log data.")

[Audit Log Viewer for the Cloud Foundry Environment](audit-log-viewer-for-the-cloud-foundry-environment-e3baa5f.md "The SAP Audit Log Viewer service displays the audit logs for your Cloud Foundry account, produced by SAP applications and services you’ve subscribed to.")

[Guided Answers for Audit Logging in the Cloud Foundry Environment](https://ga.support.sap.com/dtp/viewer/#/tree/3642/actions/59095)

