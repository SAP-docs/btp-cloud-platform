<!-- loio5310fc31caad4707be9126377e144627 -->

# Multitenancy

Each multitenant application has to deploy its own application router, and the application router handles requests of all tenants to the application. The application router is able to determine the tenant identifier out of the URL and then forwards the authentication request to the tenant User Account and Authentication \(UAA\) service and the related identity zone.

To use a multitenant application router, you must have a shared UAA service and the version of the application router has to be greater than 2.3.1.

The application router must determine the tenant-specific subdomain for the UAA that in turn determines the identity zone, used for authentication. This determination is done by using a regular expression defined in the environment variable `TENANT_HOST_PATTERN`.

`TENANT_HOST_PATTERN` is a string containing a regular expression with a capturing group. The request host is matched against this regular expression. The value of the first capturing group is used as the tenant subdomain.

If you have multiple routes to the same application, for example:

`tenant1.<application domain>` and `tenant2.<application domain>`

The `TENANT_HOST_PATTERN` could be:

`TENANT_HOST_PATTERN: "^(.*).<application domain>"`

With this configuration, the application router extracts the tenant subdomain, which is used for authentication against a multitenant UAA.



<a name="loio5310fc31caad4707be9126377e144627__section_a4v_m4y_1jb"/>

## Register an Application \(SaaS Registry Configuration\)

Create a service instance of the SaaS Provisioning service with a configuration JSON file in the Cloud Foundry sub-account space where the multitenant business application is deployed.

The configuration JSON file must use the following format and set these properties:

```json
{
   "xsappname" : "<xsappname>",
   "appUrls": {
      "getDependencies" : "<approuter-host>/<getDependenciesPath>/{tenantId}",
      "onSubscription" : ""<approuter-host>/<onSubscriptionPath>/{tenantId}"
   },
   "displayName" : "<displayName>",
   "description" : "<description>",
   "category" : "<category>"
}
```

Specify the following parameters:


<table>
<tr>
<th valign="top">

Parameters



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`xsappname`



</td>
<td valign="top">

The `xsappname` configured in the security descriptor file used to create the XSUAA instance \(see [Develop the Multitenant Application](develop-the-multitenant-application-ff54047.md)\).



</td>
</tr>
<tr>
<td valign="top">

`getDependenciesPath`



</td>
<td valign="top">

\(Optional\) Any URL that the application exposes for `GET` dependencies. If the application doesn’t have dependencies and the callback isn’t implemented, it mustn't be declared.



</td>
</tr>
<tr>
<td valign="top">

`onSubscriptionPath`



</td>
<td valign="top">

This parameter must end with `/{tenantId}`. The tenant for the subscription is passed to this callback as a path parameter. You must keep `{tenantId}` as a parameter in the URL so that it’s replaced at runtime with the tenant calling the subscription. This callback URL is called when a subscription between a multitenant application and a consumer tenant is created `(PUT)` and when the subscription is removed `(DELETE)`.



</td>
</tr>
<tr>
<td valign="top">

`displayName`



</td>
<td valign="top">

\(Optional\) The display name of the application when viewed in the cockpit. For example, in the application's tile. If left empty, takes the application's technical name.



</td>
</tr>
<tr>
<td valign="top">

`description`



</td>
<td valign="top">

\(Optional\) The description of the application when viewed in the cockpit. For example, in the application's tile. If left empty, takes the application's display name.



</td>
</tr>
<tr>
<td valign="top">

`category`



</td>
<td valign="top">

\(Optional\) The category to which the application is grouped in the *Subscriptions* page in the cockpit. If this parameter is left empty, it’s assigned to the default category.



</td>
</tr>
</table>

> ### Note:  
> For information about how to model the security settings for activating the `saas-registry` callbacks, see [Develop the Multitenant Application](develop-the-multitenant-application-ff54047.md).

**Related Information**  


[Developing Multitenant Applications in the Cloud Foundry Environment](developing-multitenant-applications-in-the-cloud-foundry-environment-5e8a2b7.md "In the Cloud Foundry environment, you can develop and run multitenant applications, and share them with multiple consumers simultaneously on SAP BTP.")

[Register the Multitenant Application to the SAP SaaS Provisioning Service](register-the-multitenant-application-to-the-sap-saas-provisioning-service-3971151.md "To make a multitenant application available for subscription to SaaS consumer tenants, you (the application provider) must register the application in the Cloud Foundry environment via the SaaS Provisioning Service (technical name: saas-registry).")

