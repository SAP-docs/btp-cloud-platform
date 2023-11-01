<!-- loio6d3ef5260f4a4232ad43542ab1441694 -->

# Limits for Technical Artifacts of the SAP Authorization and Trust Management Service

To improve the resiliency of the SAP Authorization and Trust Management service, we have introduced limitations on technical artifacts of the service.



<a name="loio6d3ef5260f4a4232ad43542ab1441694__section_isr_yyq_zyb"/>

## Limits for the Service Broker

We allow a maximum of service instances per subaccount.

There is also a maximum of service bindings and service keys in total per service instance. The service rejects attempts to add more bindings or service keys. For more information, see [Service Instance Secrets](../50-administration-and-ops/service-instance-secrets-5578ec4.md).

**Limits for the Service Broker**


<table>
<tr>
<th valign="top">

Service Broker Resource

</th>
<th valign="top">

Upper Limit

</th>
</tr>
<tr>
<td valign="top">

Service instances per subaccount

</td>
<td valign="top">

1000

</td>
</tr>
<tr>
<td valign="top">

Service bindings and service keys in total per service instances

</td>
<td valign="top">

1000

</td>
</tr>
</table>



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



<a name="loio6d3ef5260f4a4232ad43542ab1441694__section_ygd_s4f_fzb"/>

## Limits for the Global Account

It is possible to configure up to 3 custom identity providers for platform users in a global account.



<a name="loio6d3ef5260f4a4232ad43542ab1441694__section_ddk_bhf_fzb"/>

## Limits for the Subaccount

There are limits that apply to the subaccount. Administrators can use application roles and create their own roles. They can create and manage role collections, add roles to them, and assign the role collections to business users.

For more information, see [Building Roles and Role Collections for Applications](../50-administration-and-ops/building-roles-and-role-collections-for-applications-eaa6a26.md) and [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

**Limits for Security Artifacts**


<table>
<tr>
<th valign="top">

Security Artifact

</th>
<th valign="top">

Upper Limit

</th>
</tr>
<tr>
<td valign="top">

Roles created by administrators

> ### Note:  
> Roles that are automatically generated when a service instance was created or updated are not counted here.



</td>
<td valign="top">

2500

</td>
</tr>
<tr>
<td valign="top">

Role collections created by administrators

</td>
<td valign="top">

5000

</td>
</tr>
</table>

When establishing trust, subaccount administrators must observe the limits for identity providers.

**Limits for Identity Providers**


<table>
<tr>
<th valign="top">

Identity Provider

</th>
<th valign="top">

Upper Limit

</th>
</tr>
<tr>
<td valign="top">

SAML identity providers

</td>
<td valign="top">

50

</td>
</tr>
<tr>
<td valign="top">

User attribute mappings defined in a subaccount

</td>
<td valign="top">

5000

</td>
</tr>
</table>

