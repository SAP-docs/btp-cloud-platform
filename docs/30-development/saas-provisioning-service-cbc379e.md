<!-- loiocbc379ef476e460c87934d0e496b7850 -->

# Saas Provisioning Service



> ### Sample Code:  
> ```
> - name: saas-registry
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service: saas-registry
>       service-plan: application 
>       service-name: saas-registry
>       config:
>         xsappname: ${appname}
>         appName: ${appname}
>         appUrls:
>           getDependencies: https://cis${route-prefix}.${app-domain}/callback/v1.0/dependencies
>           onSubscription: https://cis${route-prefix}.${app-domain}/callback/v1.0/tenants/{tenantId}
>         displayName: ${saas-display-name}
>         description: ${saas-description}
> 
> ```

The `SaaS Provisioning` service allows application providers to register multitenant applications and services in the Cloud Foundry environment in SAP Business Technology Platform.



### SaaS Provisioning Service Paramters


<table>
<tr>
<td valign="top">

xsappname



</td>
<td valign="top">

The xsappname configured in the security descriptor file used to create the XSUAA instance.



</td>
</tr>
<tr>
<td valign="top">

getDependencies



</td>
<td valign="top">

**\(Optional\)** Any URL that the application exposes for GET dependencies. If the application does not have dependencies and the callback is not implemented, it should not be declared. **Note:** The JSON response of the callback must be encoded as either UTF8, UTF16, or UTF32, otherwise an error is returned. Important: You can either provide your own getDependencies Callback or use the default implementation of the AppRouter \(recommended if no special logic is needed\). **But:** If an own implementation is provided you have to make sure that the ABAP Solution instance is returned as a dependency.

The path is: /callback/v1.0/dependencies



</td>
</tr>
<tr>
<td valign="top">

onSubscription



</td>
<td valign="top">

Any URL that the application exposes via PUT and DELETE subscription. It must end with /\{tenantId\}. The tenant for the subscription is passed to this callback as a path parameter. You must keep \{tenantId\} as a parameter in the URL so that it is replaced at real time with the tenant calling the subscription. This callback URL is called when a subscription between a multitenant application and a consumer tenant is created \(PUT\) and when the subscription is removed \(DELETE\). **Important:** You can either provide your own onSubscription Callback or use the default implementation of the approuter \(recommended if no special logic is needed\).

The path is: /callback/v1.0/tenants/\{tenantId\}



</td>
</tr>
<tr>
<td valign="top">

displayName



</td>
<td valign="top">

**\(Optional\)** The display name of the application when viewed in the cockpit. For example, in the application's tile. If left empty, takes the application's technical name.



</td>
</tr>
<tr>
<td valign="top">

description



</td>
<td valign="top">

**\(Optional\)** The description of the application when viewed in the cockpit. For example, in the application's tile. If left empty, takes the application's display name.



</td>
</tr>
<tr>
<td valign="top">

category



</td>
<td valign="top">

**\(Optional\)** The category to which the application is grouped in the Subscriptions page in the cockpit. If left empty, gets assigned to the default category.



</td>
</tr>
</table>





### Callback APIs

Callback URLs defined in parameters *getDependencies* and *onSubscription* are called during the subscription flow and need to be callable via a consumer-independent URL. For this purpose, a dedicated URL that matches the `TENANT_HOST_PATTERN` of the approuter application should be defined as part for the MTA project.

Depending on the phase of the multitenant application, a different `TENANT_HOST_PATTERN` is defined:

-   **During development phase:**

    `TENANT_HOST_PATTERN: ^(.*)-abap-saas-app.cfapps.eu10.hana.ondemand.com`

    Define a route cis-abap-saas-app.cfapps.eu10.hana.ondemand.com for SaaS Provisioning service callback URLs

-   **During production phase:**

    `TENANT_HOST_PATTERN: ^(.*).mydomain.com`

    Define a route cis.mydomain.com for SaaS Provisioning service callback URLs




### Subscription Management Dashboard

With Subscription Management Dashboard as the dashboard UI of SaaS Provisioning Service, the application provider can centrally manage subscriptions, e.g. unsubscribe existing application consumer subscriptions. See [Using the Subscription Management Dashboard.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/434be695f9e946ccb4c28911dd1e16d0.html)

