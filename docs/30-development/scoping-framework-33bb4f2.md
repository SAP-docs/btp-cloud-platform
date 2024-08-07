<!-- loio33bb4f2815cc47ed84a7db2c47ca313f -->

# Scoping Framework

Learn how to use the scoping API.

Scoping is a mechanism that determines the visibility of certain development object types at configuration time. Depending on your decisions, some object types may be hidden or displayed in the current client.

For instance, in the Business Roles app, not all business catalogs shall be available for the administrator user, because their usage is subject to additional license constraints.

To scope the relevant objects, you can use the API `IF_APS_BC_SCOPE_CHANGE_API`. The interface provides mass-enabled methods for setting the scope state of scoping-enabled `TADIR` objects in the current client.

> ### Note:  
> The objects to be scoped must be in the same software component as the caller.

The following `TADIR` types are supported:

**List of TADIR Objects That Can Be Scoped**


<table>
<tr>
<th valign="top">

Constant

</th>
<th valign="top">

`TADIR` Object

</th>
</tr>
<tr>
<td valign="top">

`CMHC`

</td>
<td valign="top">

Cloud Management Health Check

</td>
</tr>
<tr>
<td valign="top">

`ESH1`

</td>
<td valign="top">

ESH: CDS Search Model

</td>
</tr>
<tr>
<td valign="top">

`JOBD`

</td>
<td valign="top">

Technical Job Definition

</td>
</tr>
<tr>
<td valign="top">

`PCFN`

</td>
<td valign="top">

Predefined Field: Extensible Node

</td>
</tr>
<tr>
<td valign="top">

`SAJC`

</td>
<td valign="top">

Application Job Catalog Entry

</td>
</tr>
<tr>
<td valign="top">

`SCO1`

</td>
<td valign="top">

Communication Scenario

</td>
</tr>
<tr>
<td valign="top">

`SIA1`

</td>
<td valign="top">

Business Catalog

</td>
</tr>
<tr>
<td valign="top">

`SIA6`

</td>
<td valign="top">

IAM App

</td>
</tr>
<tr>
<td valign="top">

`SIA8`

</td>
<td valign="top">

Business Role Template

</td>
</tr>
<tr>
<td valign="top">

`UIST`

</td>
<td valign="top">

Fiori Launchpad Space Template

</td>
</tr>
<tr>
<td valign="top">

`UIPG`

</td>
<td valign="top">

Fiori Launchpad Page Template

</td>
</tr>
</table>

To scope one of these objects, you have to provide the object type, object name, and the desired scoping state \(`ON` or `OFF`\).

> ### Note:  
> Objects that are set to scoping state `ON` should not be set to `OFF`. The object must remain available to the customer to guarantee further access to the data maintained via the object.

For further information, see the long text documentation of the API `IF_APS_BC_SCOPE_CHANGE_API`.

