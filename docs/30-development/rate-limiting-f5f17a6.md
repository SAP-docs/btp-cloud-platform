<!-- loiof5f17a69b7b845e2996256eff8d0a252 -->

# Rate Limiting

The SAP Cloud Deployment service limits how frequently operations can be started to protect service availability and ensure consistent performance across environments.

Rate limits apply when you **start** a new operation. Requests that exceed a limit are rejected before the operation begins. Operations already running are not affected.

> ### Remember:  
> An operation is any action that modifies the state of a multitarget application \(MTA\) in your Cloud Foundry space, such as deploying, undeploying, or updating an MTA.

Limits are enforced at two levels simultaneously:

-   **Per space**: All users in the same Cloud Foundry space share a single allowance. Heavy usage by one user can exhaust the shared allowance.
-   **Per user**: Each user has an individual allowance within the space, independent of other users.

These limits are checked every time you start an operation. If your request exceeds any limit, the service returns `HTTP 429 Too Many Requests`.



## Limits



### Concurrent Operation Limit

The maximum number of operations that can be active at the same time:


<table>
<tr>
<th valign="top">

Scope

</th>
<th valign="top">

Concurrent Operations Limit

</th>
</tr>
<tr>
<td valign="top">

Per space

</td>
<td valign="top">

500 operations

</td>
</tr>
<tr>
<td valign="top">

Per user

</td>
<td valign="top">

200 operations

</td>
</tr>
</table>



### Operation Start Rate

The maximum number of new operations that can be started within a rolling time window:


<table>
<tr>
<th valign="top">

Scope

</th>
<th valign="top">

New Operations Limit

</th>
</tr>
<tr>
<td valign="top">

Per space

</td>
<td valign="top">

Approximately 300 operations

</td>
</tr>
<tr>
<td valign="top">

Per user

</td>
<td valign="top">

Approximately 150 operations

</td>
</tr>
</table>

> ### Note:  
> Each operation start consumes one unit from both the space and the user allowances. Allowances refill automatically over the rolling time window.

**Related Information**  


[Integrating with SAP Cloud Deployment Service](integrating-with-sap-cloud-deployment-service-d4a82c0.md "Implement the SAP Cloud Deployment service API to provide capabilities for deployment and management of multitarget applications in your service.")

