<!-- loio1697387c02e74e66a55cf21a05678167 -->

# ABAP Solution Service



> ### Sample Code:  
> ```
> 
>   - name: abap-solution
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service: abap-solution
>       service-plan: standard
>       service-name: ${appname}-abap-solution
>       config:
>         name: ${appname}
>         consumer_id_pattern: ${consumer-id-pattern}
>         plans:
>           - plan_name: ${plan-name}
>             addon_product_name: ${addon-product-name}
>             size_of_runtime: ${size-of-runtime}
>             size_of_persistence: ${size-of-persistence}
>             provider_admin_email: ${provider-admin-email}
>             consumer_tenant_limit: ${consumer-tenant-limit}
>             sap_system_name: ${sap-system-name}
>             usage: ${usage-mode}
>         xs-security:
>           xsappname: xs-app-${appname}
> 			
> ```

ABAP Solution Service is used to enable multitenancy for ABAP Environment systems: Instead of creating the ABAP system manually it is created by the ABAP Solution service during the first subscription of an application consumer or once the consumer tenant limit for all viable systems has been reached.

Credentials provided in the ASP\_CC destination are used by ABAP Solution Service to authenticate at the Cloud Foundry Cloud Controller API endpoint and to create required ABAP service instances.

The service plan used for created ABAP service instances is depending on the `addon_product_name` parameter: `abap/standard` is used for a system without add-on, `abap/saas_oem` is used for a system with installed add-on. Provisioning parameters like `sap_system_name`, `provider_admin_email` and sizing-relevant parameters can be defined.

After a new system is created, a tenant for the application consumer is provisioned. The business type \(see [Tenant Business Types](https://help.sap.com/docs/BTP/60f1b283f0fd4d0aa7b3f8cea4d73d1d/018e8bd109d64140ade5429c3a9dbef0.html?state=DRAFT&version=Internal)\) used for provisioning of the tenant depends on the `usage` parameter: In case of `usage = test`, the tenant is created as `Partner Customer Test` tenant. Whereas with `usage = prod`, the tenant is created as `Partner Customer Production` tenant. Parameter `tenant_mode` controls if per subscription a new tenant is created in the same system and with `consumer_tenant_limit` the number of tenants per system is configured.



### ABAP System: saas\_oem plan

This service plan is like the standard service plan of the ABAP service \(see [Create an ABAP System](https://help.sap.com/docs/BTP/60f1b283f0fd4d0aa7b3f8cea4d73d1d/50b32f144e184154987a06e4b55ce447.html?state=DRAFT&version=Internal&q=create%20an%20abap%20system)\), but it is used as "backing service" for a partner-provided SaaS solution. In comparison to a standard service plan of the ABAP service, there is one main differences: An add-on product \(see [The Add-on product](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#the-add-on-product)\) which is installed during system provisioning can be specified.

-   Parameter: `addon_product_name`

    \(specifies which ABAP add-on to install during provisioning\)

-   Parameter: `addon_product_version`

    \(if - for testing purpose - another add-on version instead of the most recent released version shall be installed\)




### ABAP Solution Service Parameters


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
<th valign="top">

Purpose



</th>
<th valign="top">

Updateable



</th>
</tr>
<tr>
<td valign="top">

name



</td>
<td valign="top">

string



</td>
<td valign="top">

Name of the solution as defined by the provider. Must be unique in the scope of the Global Account \(or globally if this information is not available\)



</td>
<td valign="top">

Used to identify the solution and will be passed through to ABAP System \(saas\_oem plan\)



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

sap\_system\_name

\(optional\)



</td>
<td valign="top">

string



</td>
<td valign="top">

Name of the system as defined by the provider. If a value is supplied, the new system\(s\) will be created with this parameter.



</td>
<td valign="top">

Passed through ABAP System



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

addon\_product\_name

\(optional\)



</td>
<td valign="top">

string



</td>
<td valign="top">

Registered name of the add-on product



</td>
<td valign="top">

Passed through ABAP System \(saas\_oem plan\)



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

addon\_product\_version

\(optional\)



</td>
<td valign="top">

string



</td>
<td valign="top">

Version of the add-on product to be installed. A released product version needs to be defined. If you do not specify the parameter, the latest released product version will be used during the add-on installation. If you specify other versions than allowed, the add-on installation and therefore also the system provisioning and consumer subscription will be unsuccessful.



</td>
<td valign="top">

Passed through ABAP System \(saas\_oem plan\)



</td>
<td valign="top">

Yes \(updated value applies for new systems only\)



</td>
</tr>
<tr>
<td valign="top">

consumer\_tenant\_limit



</td>
<td valign="top">

int



</td>
<td valign="top">

Maximum number of consumer tenants in the multitenant ABAP system. If the consumer tenant limit is exceeded, a new multitenant system will be created.

consumer\_tenant\_limit \>= 1

> ### Note:  
> A recently deleted tenant will be counted towards the limit, in case it is restored during the grace period. After the 30-day grace period is up, it will no longer be considered for the limit.



</td>
<td valign="top">

Passed through ABAP System \(saas\_oem plan\)



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

size\_of\_runtime



</td>
<td valign="top">

int



</td>
<td valign="top">

Default sizing \(ABAP runtime\) of abap system\(s\) created/provisioned by solution



</td>
<td valign="top">

Passed through to ABAP System



</td>
<td valign="top">

Yes \(updated value applies for new systems only\)



</td>
</tr>
<tr>
<td valign="top">

size\_of\_persistence



</td>
<td valign="top">

int



</td>
<td valign="top">

Default sizing \(ABAP persistence \[HANA\]\) of abap system\(s\) created/provisioned by solution



</td>
<td valign="top">

Passed through to ABAP System



</td>
<td valign="top">

Yes \(updated value applies for new systems only\)



</td>
</tr>
<tr>
<td valign="top">

tenant\_mode

\(deprecated\)



</td>
<td valign="top">

enum \(string\):

\- single

\- multi



</td>
<td valign="top">

Tenant Mode of the solution



</td>
<td valign="top">

Decides whether a customer will have a tenant in

\- a dedicated system \(single\)

\- a shared system \(multi\)

**single:** will trigger a system creation and a tenant onboarding

**multi** will trigger a system creation \(only if necessary\) and a tenant onboarding

The parameter will be passed through to ABAP System \(saas\_oem plan\).



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

consumer\_id\_pattern



</td>
<td valign="top">

string \(regex\)



</td>
<td valign="top">

String containing a regular expression with a capturing group. The **subdomain of the consumer** is matched against this regular expression. The value of the first capturing group is used as consumer id.



</td>
<td valign="top">

To allow the provider to group his consumer subaccounts based on a self-chosen consumer identifier: e.g. the subdomains of consumer subaccounts always include a static part that identifies the application consumer, then event if there are multiple test & production consumer subaccounts, the application consumer can be identified in Landscape Portal.



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

provider\_admin\_email



</td>
<td valign="top">

email



</td>
<td valign="top">

Email address of initial provider user



</td>
<td valign="top">

Passed through to ABAP System \(saas\_oem plan\).



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

xs-security/xsappname

\(optional\)



</td>
<td valign="top">

tring



</td>
<td valign="top">

xsappname used for the OAuth clone during instance creation. Will be visible in the security section of SAP BTP Cockpit when assigning the initial onboarder role. Will be the "Application Name" shown in the Roles UI.

**Default:** Service Instance GUID

**Recommendation:** Provide the same value as defined in the xs-security.json of the XSUAA Instance of your application



</td>
<td valign="top">

Allows providing a meaningful application name to assign the onboarding roles.



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

usage



</td>
<td valign="top">

enum \(string\):

\- test

\- prod



</td>
<td valign="top">

Specifies whether it is a test or production solution.



</td>
<td valign="top">

In case of usage = test a Partner Customer Test tenant is created, whereas with usage = prod, a Partner Customer Production tenant is provisioned.



</td>
<td valign="top">

No



</td>
</tr>
</table>

