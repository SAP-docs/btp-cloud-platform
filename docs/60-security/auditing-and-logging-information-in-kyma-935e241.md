<!-- loio935e241ca726412597175bef2add8c57 -->

# Auditing and Logging Information in Kyma

Kyma runtime collects audit and application logs.



<a name="loio935e241ca726412597175bef2add8c57__section_jsc_p14_zkb"/>

## Audit Logs

Audit logs are records that provide evidence of events, actions, or operations. The audit log records the following data:

-   Security and system events that include administrative activities, potential threats, and evidence in the case of a breach.
-   Changes introduced to the system, applications, and components.

Kyma runtime collects audit logs for configuration changes to the runtime setup itself and Kubernetes resources managed by the Kubernetes API server of the runtime. Usually, those logs contain the user account \(technical account or email address\) and the client IP address of the subject who triggered the changes. No other personal data is stored in the audit logs. On average, the logs store the data for 90 days. If you want to store any other personal data, be cautious and bear in mind the recommendations provided in [Data Protection and Privacy](data-protection-and-privacy-7e513d3.md).



<a name="loio935e241ca726412597175bef2add8c57__section_kct_3j4_zkb"/>

## Retrieving Audit Log Entries

As a user, you don't have direct access to the audit logs. If you want to get information stored in the audit log system, open a [support ticket](https://support.sap.com/en/index.html).



<a name="loio935e241ca726412597175bef2add8c57__section_mly_gxv_tzb"/>

## Events Written in Audit Logs

Here you can find a list of the security events that are logged by SAP BTP, Kyma runtime.



**Events Written in Audit Logs**


<table>
<tr>
<th valign="top">

Event grouping

</th>
<th valign="top">

What events are logged

</th>
<th valign="top">

Additional information

</th>
</tr>
<tr>
<td valign="top">

Secrets, ConfigMaps, and TokenReviews

</td>
<td valign="top">

CREATE, UPDATE, PATCH, and DELETE operations on the metadata level

</td>
<td valign="top">

The payload is not logged.

Resources:

-   "secrets"

-   "configmaps"

-   "tokenreviews"




</td>
</tr>
<tr>
<td valign="top">

All standard Kubernetes resources in core and extensions

</td>
<td valign="top">

CREATE, UPDATE, PATCH, and DELETE operations on the request level

</td>
<td valign="top">

Resource groups:

-   "" \# core

-   "admissionregistration.k8s.io"

-   "apiextensions.k8s.io"

-   "apiregistration.k8s.io"

-   "apps"

-   "authentication.k8s.io"

-   "authorization.k8s.io"

-   "autoscaling"

-   "batch"

-   "certificates.k8s.io"

-   "coordination.k8s.io"

-   "extensions"

-   "metrics.k8s.io"

-   "networking.k8s.io"

-   "policy"

-   "rbac.authorization.k8s.io"

-   "scheduling.k8s.io"

-   "settings.k8s.io"

-   "storage.k8s.io"




</td>
</tr>
<tr>
<td valign="top">

All Kyma resources

</td>
<td valign="top">

CREATE, UPDATE, PATCH, and DELETE operations on the request level

</td>
<td valign="top">

Resource groups:

-   "applicationconnector.kyma-project.io"

-   "compass.kyma-project.io"

-   "eventing.kyma-project.io"

-   "gateway.kyma-project.io"

-   "serverless.kyma-project.io"

-   "telemetry.kyma-project.io"

-   "operator.kyma-project.io"




</td>
</tr>
<tr>
<td valign="top">

All resources of Kyma dependencies

</td>
<td valign="top">

CREATE, UPDATE, PATCH, and DELETE operations on the request level

</td>
<td valign="top">

Resource groups:

-   "cert.gardener.cloud"

-   "ory.sh"

-   "services.cloud.sap.com"

-   "extensions.istio.io"

-   "install.istio.io"

-   "networking.istio.io"

-   "security.istio.io"

-   "telemetry.istio.io"




</td>
</tr>
</table>



<a name="loio935e241ca726412597175bef2add8c57__section_uf3_xjv_2lb"/>

## Application Logs of System Components

Kyma runtime collects application logs provided by the Kyma system components. Those logs reflect regular events that occurred in Kyma runtime and must not include any personal or sensitive data. These are typically system-related activities and operations you can analyze to get more information about performance or to inspect potential problems.

**Related Information**  


[https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/](https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/)

[Audit Logging in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f92c86ab11f6474ea5579d839051c334.html)

[Audit Logging in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/02c39712c1064c96b37c1ea5bc9420dc.html)

[Access Kyma Application Logs](../50-administration-and-ops/access-kyma-application-logs-25180f4.md "Get insights into your applications, microservices, and Functions by viewing the respective logs. To check out real-time logs immediately, use the Kubernetes functionalities - either in Kyma dashboard, or with kubectl.")

