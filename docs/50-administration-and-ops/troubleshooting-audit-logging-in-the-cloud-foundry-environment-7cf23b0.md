<!-- loio7cf23b0b0e6c41b387f27597e4aa68d5 -->

# Troubleshooting Audit Logging in the Cloud Foundry Environment

SAP Audit Log is a core, security, and compliance-based SAP BTP service to provide means for audit purposes. It offers default and advanced premium features that support audit requirements and help ensure adherence to SAP Product Standards and relevant industry regulations.

The following sections provide information and describe possible sollutions of known audit logging issues in the Cloud Foundry environment:

-   [Information Resources](troubleshooting-audit-logging-in-the-cloud-foundry-environment-7cf23b0.md#loio4e7ac27c19794065935ebeca4e650540)
-   [Audit Categories](troubleshooting-audit-logging-in-the-cloud-foundry-environment-7cf23b0.md#loio2e9facfabe7d443fbb84f749253e4ae2)
-   [Audit Logs are Missing or Detailed Information is not Written](troubleshooting-audit-logging-in-the-cloud-foundry-environment-7cf23b0.md#loiod314f9319d834053bfa25d82f5837b66)
-   [Unable to Understand the Description of the Retrieved Data](troubleshooting-audit-logging-in-the-cloud-foundry-environment-7cf23b0.md#loioea513a474b4d4438862a9db02e2a473a)
-   [Increase the Data Retention Period](troubleshooting-audit-logging-in-the-cloud-foundry-environment-7cf23b0.md#loio1c31e164ac904e58afc285e77f729f81)
-   [SAP Audit Log Viewer service issues](troubleshooting-audit-logging-in-the-cloud-foundry-environment-7cf23b0.md#loio1616a88b74b64fb9b631d60c6dd0e6b3)

<a name="loio4e7ac27c19794065935ebeca4e650540"/>

<!-- loio4e7ac27c19794065935ebeca4e650540 -->

## Information Resources

Information Resources on Features and Capabilities of SAP BTP Audit Log Service.

-   SAP KBA \#\#[2637286](https://me.sap.com/notes/2637286) - How to get Audit Logs on SAP BTP
-   SAP Help Portal [Audit Log Service Product Page](https://help.sap.com/docs/sap-audit-log)
-   [Audit Logging in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-logging-in-cloud-foundry-environment?locale=en-US)
-   [Audit Log Retrieval API Usage in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retrieval-api-usage-for-subaccounts-in-cloud-foundry-environment?locale=en-US)
-   [Audit Log Retrieval API for Global Accounts in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retrieval-api-for-global-accounts-in-cloud-foundry-environment?locale=en-US)
-   [Audit Log Write API for Customers](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-write-api-for-customers?locale=en-US)
-   [Security Events Logged by the CF Services](https://help.sap.com/docs/btp/sap-business-technology-platform/security-events-logged-by-cf-services?locale=en-US)
-   [Audit Log Viewer](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-viewer-for-cloud-foundry-environment?locale=en-US)
-   [Retention of Audit Data](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retention-for-cloud-foundry-environment?locale=en-US)

<a name="loio2e9facfabe7d443fbb84f749253e4ae2"/>

<!-- loio2e9facfabe7d443fbb84f749253e4ae2 -->

## Audit Categories

Guidelines on which category to use for logging specific event types.

> ### Note:  
> The folowing are general guidelines, and it is up to you as a customer to define the categories depending on your use case.

-   **<audit.data-access\> Log read access to sensitive personal data** - the log reflects which data is disclosed via user interface or at system boundaries. For each data set being subject to logging, the log stores the following information:

    -   The access channel \(for example, RFC, web service, IDOC, file based interfaces, user interface, spool, printing\)

    -   The user accessing the data

    -   The date and time of access

    -   The identifying keys and key values of the data sets

    -   The heading name for the attribute that has been read


-   **<audit.configuration\> Log changes to personal data** - the log reflects which personal data is changed. For each data set being subject to logging, the log stores the following information:

    -   the user who is changing the data

    -   the date and time of change

    -   the identifying keys of the data sets and their values

    -   the heading name for the attribute that is changed


-   **<audit.security-events\> Log security relevant events** - the log reflects at least the following information:

    -   The event ID

    -   The user triggering the event

    -   The date and time of the event

    -   The source IP address \(in case of external access\)

    -   Further data needed to fully understand the security relevant event


-   **< audit.data-modification\> Log changes to configuration data** - the log shall reflect which configuration data has been changed. For each data set being subject to logging, the log shall store the following information:

    -   The user accessing the data

        The date and time of access

        The identifying keys of the data sets and their values

        The new and old values of any attribute changed



<a name="loiod314f9319d834053bfa25d82f5837b66"/>

<!-- loiod314f9319d834053bfa25d82f5837b66 -->

## Audit Logs are Missing or Detailed Information is not Written

The Audit Log service only provides a framework of writing/retrieving APIs and data storage which other services use to put their audit data into. When audit logs are missing or if detailed information is not written for a specific service, that specific service is responcible to provide the data.



<a name="loiod314f9319d834053bfa25d82f5837b66__section_vqy_ggy_q2c"/>

## Events are Missing from the Retrieved Audit Logs

The logs for CF UAA\(Cloud Foundry User Account and Authentication\) and CF API \(Cloud Foundry V3 API\) are single-tenant components and you as a customer can't get access to them. To resolve such issues, see SAP KBA \#\#[3122848](https://me.sap.com/notes/3122848): Some events are missing from the audit log retrieved via Audit Log Retrieval API in BTP Cloud Foundry



<a name="loiod314f9319d834053bfa25d82f5837b66__section_v4q_sfy_q2c"/>

## How to Select the Right Component for Support

To identify which service/application is responsible for missing audit data, see:

-   SAP KBA [3053848](https://me.sap.com/notes/0003053848) - Directory of SAP Cloud Products and Component Areas \(Who to Contact\)

-   [How to select the right component for your incident](https://ga.support.sap.com/dtp/viewer/#/tree/830/actions/9139)


<a name="loioea513a474b4d4438862a9db02e2a473a"/>

<!-- loioea513a474b4d4438862a9db02e2a473a -->

## Unable to Understand the Description of the Retrieved Data

To understand the results retrived with the [Audit Log Retrieval API](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/30ece35bac024ca69de8b16bff79c413.html?locale=en-US&version=Cloud), see SAP KBA \#\#[3165473](https://me.sap.com/notes/3165473): The description of each item in audit log for SAP BTP Cloud Foundry environment account retrieved by Audit Log Retrieval API

To get more details of the service specific logged events, see [Security Events Logged by the CF Services](https://help.sap.com/docs/btp/sap-business-technology-platform/security-events-logged-by-cf-services?locale=en-US) 

> ### Note:  
> The list of services is still not complete and is updated any time more services provide description of their audit event details.

<a name="loio1c31e164ac904e58afc285e77f729f81"/>

<!-- loio1c31e164ac904e58afc285e77f729f81 -->

## Increase the Data Retention Period

The audit log data, generated by SAP BTP applications and services, and securely stored for your account, remains accessible at no extra cost for 90 days before being automatically removed. If you're subscribed to the [premium edition service plan of the Audit Log service](https://discovery-center.cloud.sap/serviceCatalog/audit-log-service?commercialModel=cpea&tab=service_plan&region=all), you can extend your retention period.

To increase your retention period, submit a support ticket with component BC-CP-CF-SEC-AUDITLG and specify:

-   Your BTP Global Account ID and Subaccount ID \(Cloud Foundry Environment\). For more informstion, see SAP KBA \#\#[3298097](https://me.sap.com/notes/3298097) - How to identify the SAP BTP Global Account ID and SAP KBA \#\#[3007643](https://me.sap.com/notes/3007643) - How to find the subaccount ID in SAP BTP Cockpit

-   Why you need the increase.


For more information, see [Audit Log Retention for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retention-for-cloud-foundry-environment?locale=en-US).

> ### Note:  
> If you'd like to purchase a plan, contact your SAP Account Manager. For more information, see SAP Note No. \#\#[2626344](https://me.sap.com/notes/2626344) - Who is the SAP Account Manager for my company? and SAP Note No.\#\#[1660069](https://me.sap.com/notes/1660069) - How to contact SAP Contracts Department for contract-related questions or issues.

<a name="loio1616a88b74b64fb9b631d60c6dd0e6b3"/>

<!-- loio1616a88b74b64fb9b631d60c6dd0e6b3 -->

## SAP Audit Log Viewer service issues

The SAP Audit Log Viewer service displays the audit logs associated with your Cloud Foundry account. These are the activity logs generated by the SAP applications and services to which you are subscribed.

Outcomes:

-   Access issues

-   You are not authorized! Please check that your user has the roles "auditlog-viewer!" and "auditlog-management!"

-   Different results shown in Viewer and API for the same filters

-   Only subaccount logs are visible

-   Cannot find the needed Audit Logs

-   Regex issues




<a name="loio1616a88b74b64fb9b631d60c6dd0e6b3__section_ayh_xwx_q2c"/>

## Access issues

If you get any of the following errors:

-   HTTP 403 error

-   Bearer error="insufficient\_scope", error\_description="The request requires higher privileges than provided by the access token."


See:

-   SAP KBA \#\# [3287339](https://me.sap.com/notes/3287339): 403 error when accessing audit log viewer in Cloud Foundry.

-   [SAP Audit Log Viewer service Access](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-viewer-for-cloud-foundry-environment#sap-audit-log-viewer-service-access)




<a name="loio1616a88b74b64fb9b631d60c6dd0e6b3__section_pfp_rwx_q2c"/>

## You are not authorized! Please check that your user has the roles "auditlog-viewer!" and "auditlog-management!"

For more information, see SAP KBA \#\#[3229265](https://me.sap.com/notes/3229265): Error occurred while trying to retrieve audit logs from Audit Log Viewer for the Cloud Foundry Environment



<a name="loio1616a88b74b64fb9b631d60c6dd0e6b3__section_nq3_kwx_q2c"/>

## Different results shown in Audit Log Viewer and API for the same filters

The Audit Log Retrieval API employs filtering based on the "time" property/field, consistently represented in UTC. while the Audit Log Viewer operates in your local time. For a comprehensive understanding of potential discrepancies with the same filters, see SAP KBA \#\#[3407710](https://me.sap.com/notes/3407710): Audit Log Retrieval API shows different results from the Audit Log Viewer and SAP KBA \#\#[3191508](https://me.sap.com/notes/3191508) - Discrepancy in Audit Log time: SAP BTP.



<a name="loio1616a88b74b64fb9b631d60c6dd0e6b3__section_p5w_yvx_q2c"/>

## Only subaccount logs are visible

The Audit Log Viewer exclusively displays audit logs related to your subaccount. For more details on how to view the Global Account audit logs, see [3431576](https://me.sap.com/notes/3431576) - Unable to view Global Account logs via SAP BTP Audit Log Viewer service.



<a name="loio1616a88b74b64fb9b631d60c6dd0e6b3__section_ojs_wtx_q2c"/>

## Cannot Find the Needed Audit Logs

-   The results are displayed in pages. Use the next page button to see all results.

-   You can use the search field to search among the displayed results on a certain page only and not for the whole specified period. Regex is not supported.

-   If you cannot find the audit logs you're looking for in the first page, specify smaller timeframes.




<a name="loio1616a88b74b64fb9b631d60c6dd0e6b3__section_qkk_ctx_q2c"/>

## Regex Issues

The search filter using Regular expression \(shortened as regex or regexp\) does not work.

This feature is not supported yet. For more details, see [3431578](https://me.sap.com/notes/3431578) - Regex queries not working on SAP BTP Audit Log Viewer

