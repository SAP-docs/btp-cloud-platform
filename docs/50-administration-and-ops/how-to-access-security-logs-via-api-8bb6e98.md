<!-- loio8bb6e98b2642486591b65ea4833bc021 -->

# How to Access Security Logs via API

Service name: `RSAU_LOG_API`

Communication scenario: `SAP_COM_0750`

This service enables you to retrieve the security audit log data from SAP S/4HANA Cloud. You can use the audit log data to integrate them into your Security and Event Management solution \(SIEM\) to detect security relevant event situations.

This is an OData version 4 service. It can be accessed via GET request in the following format:

`<host>/sap/opu/odata4/sap/rsau_log_api/srvd_a2x/sap/rsau_log_api/0001/SecurityAuditLog?$top=1000`

To use the service, you need to configure a communication arrangement for communication scenario `SAP_COM_0750`.

**Related Information**  




