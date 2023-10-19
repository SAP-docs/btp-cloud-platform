<!-- loio6d3ef5260f4a4232ad43542ab1441694 -->

# Limits for Technical Artifacts of the SAP Authorization and Trust Management Service

To improve the resiliency of the SAP Authorization and Trust Management service, we have introduced limitations on technical artifacts of the service.



<a name="loio6d3ef5260f4a4232ad43542ab1441694__section_isr_yyq_zyb"/>

## Limits for the Service Broker

We allow a maximum of 1000 bindings and service keys in total per service instance. The service rejects attempts to add more bindings or service keys.



<a name="loio6d3ef5260f4a4232ad43542ab1441694__section_p33_zyq_zyb"/>

## Limits for the Application Security Descriptor

There are limits that apply when you define properties in the application security descriptor.

You define properties in the `xs-security.json` application security descriptor file for creating or updating service instances. Take care that you don't define more properties than specified in the table.

**Limits for Properties**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Upper Limit



</th>
</tr>
<tr>
<td valign="top">

`attributes` 



</td>
<td valign="top">

50



</td>
</tr>
<tr>
<td valign="top">

`role-collections` 



</td>
<td valign="top">

250



</td>
</tr>
<tr>
<td valign="top">

`role-templates` 



</td>
<td valign="top">

500



</td>
</tr>
<tr>
<td valign="top">

`scopes` 



</td>
<td valign="top">

500



</td>
</tr>
<tr>
<td valign="top">

`scopes` \(granted\)

> ### Note:  
> Granted means that the scope object refers to applications that are specified using `granted-apps` or `grant-as-authority-to-apps` properties



</td>
<td valign="top">

250



</td>
</tr>
</table>

**Related Information**  


[Service Instance Secrets](../50-administration-and-ops/service-instance-secrets-5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and a secret. The client ID and secret are the credentials with which an application authenticates itself to the service instance.")

