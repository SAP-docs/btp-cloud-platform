<!-- loiof92c86ab11f6474ea5579d839051c334 -->

# Audit Loggingin the Cloud Foundry Environment

In this section you can find information for audit log functionalities in the  Cloud Foundry environment.

The SAP Audit Log service is a platform service which stores all the audit logs written on your behalf by other platform services that you use. It allows you to retrieve the audit logs for your subaccount via the audit log retrieval API or view them using the SAP Audit Log Viewer service. To retrieve the audit logs stored for your global account, create a support ticket with component BC-CP-CF-SEC-AUDITLG.

Audit logs are a special type of logs. They represent security-relevant chronological records that provide documentary evidence for an event or activity. The following table gives you a better understanding what is the difference between audit logs, activity logs and application logs. The SAP Audit Log service only stores audit logs written by SAP BTP services, when taking action over your account data.

![](images/Log_type_differences_325f42d.png)

The SAP Audit Log service stores audit logs representing different actions taken over your account and/or data. There are predefined audit categories which represent such kind of actions:

-   Data protection and privacy related

    -   *audit.data-access* read-access logging records for access to sensitive personal data;

    -   *audit.data-modification* data modification logging records for sensitive personal data.


    Security related

    -   *audit.security-events* logging of general security events like login, logout, and other;

    -   *audit.configuration* logging of security critical configuration changes.



See [Change Logging and Read-Access Logging](../60-security/change-logging-and-read-access-logging-93fac8d.md).

If your subaccount audit logs contain other log types or information, create a support ticket with component BC-CP-CF-SEC-AUDITLG.

**Related Information**  


[Audit Log Retrieval API Usage for Subaccounts in the Cloud Foundry Environment](audit-log-retrieval-api-usage-for-subaccounts-in-the-cloud-foundry-environment-30ece35.md "The audit log retrieval API allows you to retrieve the audit logs for your SAP BTP Cloud Foundry environment subaccount. It provides the audit log results as a collection of JSON entities.")

[Audit Log Retention for the Cloud Foundry Environment](audit-log-retention-for-the-cloud-foundry-environment-adaefa6.md "The audit log data stored for your account will be retained for 90 days, after which it will be deleted.")

[Audit Log Viewer for the Cloud Foundry Environment](audit-log-viewer-for-the-cloud-foundry-environment-e3baa5f.md "The SAP Audit Log Viewer service displays the audit logs for your Cloud Foundry account, produced by SAP applications and services you’ve subscribed to.")

