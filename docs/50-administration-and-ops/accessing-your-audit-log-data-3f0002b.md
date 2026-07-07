<!-- loio3f0002b5f936402b90f4203b4e344092 -->

# Accessing Your Audit Log Data

Use the credentials stored in your Kyma cluster to query your audit log data using the SAP Audit Log Retrieval API v2.



<a name="loio3f0002b5f936402b90f4203b4e344092__prereq_audit_log_access"/>

## Prerequisites

-   You have a Kyma instance created. See [Creating Kyma Instances](creating-kyma-instances-09dd313.md).

-   You have the *Access to Audit Logs* parameter enabled. See [Access to Audit Logs](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_access_to_audit_logs).




<a name="loio3f0002b5f936402b90f4203b4e344092__context_audit_log_access"/>

## Context

When you enable the *Access to Audit Logs* parameter, Kyma stores the audit log read credentials in a Kubernetes Secret named `auditlog-read-credentials` in the `kyma-system` namespace of your cluster. The Secret contains the following fields:


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`url`

</td>
<td valign="top">

Base URL of the SAP Audit Log Retrieval API

</td>
</tr>
<tr>
<td valign="top">

`clientID`

</td>
<td valign="top">

OAuth 2.0 client ID

</td>
</tr>
<tr>
<td valign="top">

`clientSecret`

</td>
<td valign="top">

OAuth 2.0 client secret

</td>
</tr>
<tr>
<td valign="top">

`tokenUrl`

</td>
<td valign="top">

OAuth 2.0 token endpoint

</td>
</tr>
</table>

> ### Caution:  
> Enabling *Access to Audit Logs* is irreversible. Once you enable the feature, you cannot disable it.



## Procedure

1.  Connect to your Kyma cluster using kubectl. See [Access a Kyma Instance Using kubectl](https://help.sap.com/docs/btp/sap-business-technology-platform/access-kyma-instance-using-kubectl?locale=en-US&version=Cloud).

2.  To retrieve the Secret, run:

    ```
    kubectl get secret -n kyma-system auditlog-read-credentials -o yaml
    ```

3.  Use the credentials from the Secret to authenticate against the SAP Audit Log Retrieval API v2 using OAuth 2.0 client credentials and retrieve your audit log records.

    For full API details — including query parameters, pagination, response format, and rate limits — see [Audit Log Retrieval API for Global Accounts in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retrieval-api-for-global-accounts-in-cloud-foundry-environment?locale=en-US).




<a name="loio3f0002b5f936402b90f4203b4e344092__result_audit_log_access"/>

## Results

You can read your audit log data from the SAP Audit Log Retrieval API v2 using the credentials stored in the `auditlog-read-credentials` Secret.

**Related Information**  


[Audit Log Retrieval API for Global Accounts in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retrieval-api-for-global-accounts-in-cloud-foundry-environment?locale=en-US)

[Retrieve Adit Log Data Using Audit Log CLI](https://github.com/SAP-samples/kyma-runtime-samples/blob/main/retrieve-auditlog-data/README.md)

