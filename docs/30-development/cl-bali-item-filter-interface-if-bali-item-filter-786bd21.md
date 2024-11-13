<!-- loio786bd211c1454cf093a10e818eb38973 -->

# CL\_BALI\_ITEM\_FILTER \(Interface IF\_BALI\_ITEM\_FILTER\)

The class `CL_BALI_ITEM_FILTER` allows you to define an item filter. You can use it if it's necessary to restrict which items are added to an application log. The public interface of the instance methods is `IF_BALI_ITEM_FILTER`.

**Public Methods**



Create an instance of the filter class:

**CREATE \(static\)**


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

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

FILTER

</td>
<td valign="top">

Reference to the interface `IF_BALI_ITEM_FILTER` 

</td>
</tr>
</table>



Set a table of all severity values that pass the filter. It overwrites all previous filter settings related to the severity:

**SET\_SEVERITY**


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

SEVERITY\_TABLE

</td>
<td valign="top">

Table with severity values \(such as *Error* or *Warning*\)

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

NEW\_FILTER

</td>
<td valign="top">

Reference to the current filter object

</td>
</tr>
</table>

> ### Note:  
> -   Valid values of the severity can be found in the interface `IF_BALI_CONSTANTS`
> 
> -   If the parameter `SEVERITY_TABLE` doesn't contain an entry, all severity values pass the filter
> 
> -   If the parameter `SEVERITY_TABLE` only contains invalid entries, no severity passes the filter



Apply the filter to a set of log item attributes and check whether it passes the filter:

**APPLY\_FILTER**


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

SEVERITY

</td>
<td valign="top">

Severity of the log item that is checked

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

If set, the set of attributes passes the item filter

</td>
</tr>
</table>

