<!-- loio0882b7f82736431d8b145913af17b532 -->

# Manage Git Repository

The Manage Git Repository API allows you to manage software components \(Git repositories\) on an SAP BTP ABAP Environment system.



<a name="loio0882b7f82736431d8b145913af17b532__section_nn5_vg4_bpb"/>

## Overview

On an ABAP Environment system, software components, which represent Git repositories, can be controlled with Git operations. This includes cloning to an ABAP Environment system, pulling updates and working with branches \(create, delete, checkout\). These operations can be used with this API.

**Technical Name**: MANAGE\_GIT\_REPOSITORY

**OData Version**: 2.0

**Root URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY





### Permissions

In order to access this service, you need to:

-   Create a *Communication User* as described in [How to Create Communication Users](../50_administration_and_ops/how-to-create-communication-users-0377ade.md).

-   Create a *Communication System* as described in [How to Create Communication Systems](../50_administration_and_ops/how-to-create-communication-systems-c2234ac.md)
-   Create a *Communication Arrangement* as described in [How to Create a Communication Arrangement](../50_administration_and_ops/how-to-create-a-communication-arrangement-a0771f6.md).

-   Select the communication scenario **SAP\_COM\_0510** for your communication arrangement and have mapped it to your communication system.



### Service Structure

**Service Metadata URI**: sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/$metadata



### Service Entities

<a name="loio0882b7f82736431d8b145913af17b532__table_dqx_vkx_cpb"/>


<table>
<tr>
<th valign="top">

Service Entity



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

[Branches](branches-bbaf3c1.md)



</td>
<td valign="top">

Branches of a software component



</td>
</tr>
<tr>
<td valign="top">

[Clones](clones-9cfbb42.md)



</td>
<td valign="top">

Clone job of a software component



</td>
</tr>
<tr>
<td valign="top">

[Execution Log](execution-log-3c1ec56.md)



</td>
<td valign="top">

Execution Log of a software component



</td>
</tr>
<tr>
<td valign="top">

[Pull](pull-3198c2a.md)



</td>
<td valign="top">

Pull job of a software component



</td>
</tr>
<tr>
<td valign="top">

[Transport Log](transport-log-ed88be1.md)



</td>
<td valign="top">

Transport log of an impored transport



</td>
</tr>
</table>

