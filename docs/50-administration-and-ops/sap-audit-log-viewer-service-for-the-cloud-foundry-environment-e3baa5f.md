<!-- loioe3baa5f1a0c64c44aac8ab3ea3d1b500 -->

# SAP Audit Log Viewer service for the Cloud Foundry Environment

The SAP Audit Log Viewer service displays the audit logs for your Cloud Foundry account, produced by SAP applications and services you’ve subscribed to.

The UI allows you to:

-   Read the audit logs written for your account in selected time frame. The SAP Audit Log Viewer service displays 500 audit log records per request. If you want to view more audit log records, specify a shorter time frame.

-   Display more detailed information on each single audit log record.

-   Filter the retrieved client-side chunk for certain strings.

-   Select which of the four audit log message categories to be returned. If you don't select any category, all are returned.

-   Download the audit logs in the selected time frame.


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

**Related Information**  


[Subscribe to SAP Audit Log Viewer service](subscribe-to-sap-audit-log-viewer-service-8ef9054.md "Subscribe to SAP Audit Log Viewer service for access to audit log information.")

[Access SAP Audit Log Viewer service](access-sap-audit-log-viewer-service-af26206.md "")

[Accessibility Features in Audit Log Viewer](accessibility-features-in-audit-log-viewer-bf36fd1.md "To optimize your experience of Audit Log Viewer, SAP Business Technology Platform (SAP BTP) provides features and settings that help you use the software efficiently.")

