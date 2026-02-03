<!-- loio44b00a8f95e2473bb650084fa4e428b9 -->

# Auditing and Logging Information

Here you can find a list of the audit log events that are logged by the SAP Cloud Management service.

**Audit log events written in audit logs**


<table>
<tr>
<th valign="top">

Event grouping

</th>
<th valign="top">

What audit log events are logged

</th>
<th valign="top">

How to identify related audit log events

</th>
<th valign="top">

Additional information

</th>
</tr>
<tr>
<td valign="top" rowspan="7">

Events related to the management of global accounts and the creation and management of directories and subaccounts

\(`Accounts` API\)

</td>
<td valign="top">

Update of a global account

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"UPDATE\"`

-   `\"entity\":\"GlobalAccount`




</td>
<td valign="top" rowspan="7">

To retrieve audit logs for a global account, use the audit log retrieval API. For more information, see [Audit Log Retrieval API for Global Accounts in the Cloud Foundry Environment](audit-log-retrieval-api-for-global-accounts-in-the-cloud-foundry-environment-7db3c9f.md).

</td>
</tr>
<tr>
<td valign="top">

Creation of a directory

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"CREATE\"`

-   `\"entity\":\"Directory`




</td>
</tr>
<tr>
<td valign="top">

Update of a directory

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"UPDATE\"`

-   `\"entity\":\"Directory`




</td>
</tr>
<tr>
<td valign="top">

Deletion of a directory

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"DELETE\"`

-   `\"entity\":\"Directory`




</td>
</tr>
<tr>
<td valign="top">

Creation of a subaccount

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"CREATE\"`

-   `\"entity\":\"Subaccount`




</td>
</tr>
<tr>
<td valign="top">

Update of a subaccount

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"UPDATE\"`

-   `\"entity\":\"Subaccount`




</td>
</tr>
<tr>
<td valign="top">

Deletion of a subaccount

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"DELETE\"`

-   `\"entity\":\"Subaccount`




</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Events related to the creation and management of environment instances

\(`Provisioning` API\)

</td>
<td valign="top">

Creation of an environment instance \(for example, Cloud Foundry\)

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"CREATE\"`

-   The `\"entity\"` attribute contains the text `.ServiceInstance\"`




</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Update of an environment instance

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"UPDATE\"`

-   The `\"entity\"` attribute contains the text `.ServiceInstance\"`




</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Deletion of an environment instance

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"DELETE\"`

-   The `\"entity\"` attribute contains the text `.ServiceInstance\"`




</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="5">

Events related to the management of product entitlements and assignments across your global account, directories, and subaccounts

\(`Entitlements` API\)

</td>
<td valign="top">

Assignment of a service plan to a subaccount

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"CREATE\"` or `\"type\":\"UPDATE\"`

-   The `"entityType"` attribute contains the text `ServicePlanAssignment`.

-   The `"entityId"` attribute contains the subaccount GUID.



</td>
<td valign="top" rowspan="5">

To retrieve audit logs for a global account, use the audit log retrieval API. For more information. see [Audit Log Retrieval API for Global Accounts in the Cloud Foundry Environment](audit-log-retrieval-api-for-global-accounts-in-the-cloud-foundry-environment-7db3c9f.md).

</td>
</tr>
<tr>
<td valign="top">

Removal of a service plan from a subaccount

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"DELETE\"` 

-   The `"entityType"` attribute contains the text `ServicePlanAssignment`.

-   The `"entityId"` attribute contains the subaccount GUID.



</td>
</tr>
<tr>
<td valign="top">

Assignment of an entitlement to a directory

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"CREATE\"` or`\"type\":\"UPDATE\"`

-   The `"entityType"` attribute contains the text `AssignedEntitlement`.

-   The `"entity_Id"` attribute contains the directory GUID in the `"entityGUID"`field and `"entityType":"DIRECTORY"`.



</td>
</tr>
<tr>
<td valign="top">

Update of an assignment of an entitlement to a directory

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"UPDATE\"`

-   `"entityType"` attribute contains the text `AssignedEntitlement`.

-   The `"entityGUID"` attribute contains the directory GUID and updated quota amounts.



</td>
</tr>
<tr>
<td valign="top">

Removal of an entitlement from a directory

</td>
<td valign="top">

The message contains the texts:

-   \\"type\\":\\"DELETE\\"

-   The `"entityType"` attribute contains the text `AssignedEntitlement`.

-   The `"entityGUID"` attribute contains the directory GUID and updated quota amounts.



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Event related to subscriptions of consumers to multitenant applications in the Cloud Foundry environment. The multitenant applications must be registered to the SaaS Provisioning Service. See [Register the Multitenant Application to the SAP SaaS Provisioning Service](../30-development/register-the-multitenant-application-to-the-sap-saas-provisioning-service-3971151.md).

\(SaaS Provisioning Service, technical name: `saas-registry`\)

</td>
<td valign="top">

Creation of a subscription to an application for a subaccount

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"CREATE\"` 

-   `\"entity\":\"RootSubscription` 

-   The `"entity"` attribute contains the subaccount GUID in `"subaccountId"` field, the app name in the `"appName"` field , and subscription state details, including `"state"` and `"code"`\(plan\).




</td>
<td valign="top" rowspan="3">

To retrieve audit logs for subscriptions of applications to subaccounts, use the audit log retrieval API. For more information, see [Audit Log Retrieval API Usage for Subaccounts in the Cloud Foundry Environment](audit-log-retrieval-api-usage-for-subaccounts-in-the-cloud-foundry-environment-30ece35.md).

</td>
</tr>
<tr>
<td valign="top">

Update of a subscription \(when parameters or a plan have been changed\)

</td>
<td valign="top">

-   `\"type\":\"UPDATE\"` 

-   `\"entity\":\"RootSubscription` 

-   The `"entity"` attribute contains the subaccount GUID in `"subaccountId"` field, the app name in the `"appName"` field , and subscription state details, including `"state"` and `"code"`\(plan\).




</td>
</tr>
<tr>
<td valign="top">

Deletion of a subscription

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"UPDATE\"` 

-   `\"entity\":\"RootSubscription` 

-   The `"entity"` attribute contains the subaccount GUID in `"subaccountId"` field, the app name in the `"appName"` field , and subscription state details, including `"state"` and `"code"`\(plan\).




</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Events related to the management of budgets in your global account. See [Managing Budgets in Your Global Account](managing-budgets-in-your-global-account-e115d5f.md#loioe115d5fbe1454f58aabeb3b4b1e7a847).

\(`Budgets` service\)

</td>
<td valign="top">

Creation of a budget

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"CREATE\"`

-   `\"entity\":\"Budget`




</td>
<td valign="top" rowspan="3">

To retrieve audit logs for a global account, use the audit log retrieval API. For more information, see [Audit Log Retrieval API for Global Accounts in the Cloud Foundry Environment](audit-log-retrieval-api-for-global-accounts-in-the-cloud-foundry-environment-7db3c9f.md).

</td>
</tr>
<tr>
<td valign="top">

Update of a budget

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"UPDATE\"`

-   `\"entity\":\"Budget`




</td>
</tr>
<tr>
<td valign="top">

Deletion of a budget

</td>
<td valign="top">

The message contains the texts:

-   `\"type\":\"DELETE\"`

-   `\"entity\":\"Budget`




</td>
</tr>
</table>



The following information is described in the table columns:

-   *Event grouping* - Events that are logged with a similar format or are related to the same entities.

-   *What audit events are logged* - Description of the security or data protection and privacy related event that is logged.

-   *How to identify related log events* - Search criteria or key words, that are specific for a log event that is created along with the logged event.

-   *Additional information* - Any related information that can be helpful.


**Related Information**  


[Audit Logging in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f92c86ab11f6474ea5579d839051c334.html)

