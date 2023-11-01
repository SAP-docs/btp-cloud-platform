<!-- loioec892a29c5d0426f981b509cbe7e8ae4 -->

# IF\_BALI\_ITEM\_SETTER



<a name="loioec892a29c5d0426f981b509cbe7e8ae4__section_lwp_nfr_lsb"/>

## Context

If a new item, such as a message or an exception, is added to an application log, its object instance contains the interface IF\_BALI\_ITEM\_SETTER.



<a name="loioec892a29c5d0426f981b509cbe7e8ae4__section_pqj_4fr_lsb"/>

## Public Attributes


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

CATEGORY

</td>
<td valign="top">

Category of the item

Possible values:

-   IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_MESSAGE: Item is a message

-   IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_FREE\_TEXT: Item is a free text

-   IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_EXCEPTION: Item is an exception




</td>
</tr>
</table>



## Public Methods

Check whether the item can pass an item filter:

**CHECK\_PASSING\_ITEM\_FILTER**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameter**

</td>
</tr>
<tr>
<td valign="top">

ITEM\_FILTER

</td>
<td valign="top">

Reference to the item filter that is being checked

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

FILTER\_PASSED

</td>
<td valign="top">

If set, the item can pass the item filter

</td>
</tr>
</table>

