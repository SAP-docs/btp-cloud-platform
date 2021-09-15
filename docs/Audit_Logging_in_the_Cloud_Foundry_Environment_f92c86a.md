<!-- loiof92c86ab11f6474ea5579d839051c334 -->

# Audit Loggingin the Cloud Foundry Environment

In this section you can find information for audit log functionalities in the  Cloud Foundry environment.

The SAP Audit Log service is a platform service which stores all the audit logs written on your behalf by other platform services that you use. It allows you to retrieve the audit logs for your subaccount via the audit log retrieval API or view them using the SAP Audit Log Viewer service. To retrieve the audit logs stored for your global account, create a support ticket with component BC-CP-CF-SEC-AUDITLG.

As you know audit logs are a special type of logs. They represent security-relevant chronological records that provide documentary evidence for an event or activity. The following table gives you a better understanding what is the difference between audit logs, activity logs and application logs. The SAP Audit Log service only stores audit logs written by SAP BTP services, when taking action over your account data.

![](images/Log_type_differences_325f42d.png)

The SAP Audit Log service stores audit logs representing different actions taken over your account and/or data. There are predefined audit categories which represent such kind of actions:

-   Data protection and privacy related

    -   *audit.data-access* read-access logging records for access to sensitive personal data;

    -   *audit.data-modification* data modification logging records for sensitive personal data.

    Security related

    -   *audit.security-events* logging of general security events like login, logout, and other;

    -   *audit.configuration* logging of security critical configuration changes.


See [Change Logging and Read-Access Logging](Change_Logging_and_Read-Access_Logging_93fac8d.md).



If your subaccount audit logs contain other log types or information, create a support ticket with component BC-CP-CF-SEC-AUDITLG.

-   **[Audit Log Retrieval API Usage for the Cloud Foundry Environment](Audit_Log_Retrieval_API_Usage_for_the_Cloud_Foundry_Environment_30ece35.md "The audit log retrieval API allows you to retrieve the audit logs for your SAP BTP
		Cloud
                                Foundry
		environment account. It provides the audit log results as a collection of JSON
		entities.")**  
The audit log retrieval API allows you to retrieve the audit logs for your SAP BTP Cloud Foundry environment account. It provides the audit log results as a collection of JSON entities.
-   **[Audit Log Retention for the Cloud Foundry Environment](Audit_Log_Retention_for_the_Cloud_Foundry_Environment_adaefa6.md "The audit log data stored for your account will be retained for 90 days, after which it
		will be deleted. ")**  
The audit log data stored for your account will be retained for 90 days, after which it will be deleted.
-   **[Audit Log Viewer for the Cloud Foundry Environment](Audit_Log_Viewer_for_the_Cloud_Foundry_Environment_e3baa5f.md "The SAP Audit Log Viewer
                                    service
		displays the audit logs for your Cloud
                                Foundry account,
		produced by SAP applications and services you’ve subscribed to. ")**  
The SAP Audit Log Viewer service displays the audit logs for your Cloud Foundry account, produced by SAP applications and services you’ve subscribed to.

**Related Information**  


[Audit Log Retrieval API Usage for the Cloud Foundry Environment](Audit_Log_Retrieval_API_Usage_for_the_Cloud_Foundry_Environment_30ece35.md "The audit log retrieval API allows you to retrieve the audit logs for your SAP BTP Cloud Foundry environment account. It provides the audit log results as a collection of JSON entities.")

[Audit Log Retention for the Cloud Foundry Environment](Audit_Log_Retention_for_the_Cloud_Foundry_Environment_adaefa6.md "The audit log data stored for your account will be retained for 90 days, after which it will be deleted.")

[Audit Log Viewer for the Cloud Foundry Environment](Audit_Log_Viewer_for_the_Cloud_Foundry_Environment_e3baa5f.md "The SAP Audit Log Viewer service displays the audit logs for your Cloud Foundry account, produced by SAP applications and services you’ve subscribed to.")

