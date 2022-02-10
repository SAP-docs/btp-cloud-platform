<!-- loio7e3cd149955c4f3483d33c21d5c128f9 -->

# CL\_BALI\_ITEM\_FILTER \(Interface IF\_BALI\_ITEM\_FILTER\)

The class `CL_BALI_ITEM_FILTER` allows to define an item filter. It can be used in case it's necessary to restrict which items are added to a log. The public interface of the instance methods is `IF_BALI_ITEM_FILTER`.



<a name="loio7e3cd149955c4f3483d33c21d5c128f9__section_qtp_sxr_lsb"/>

## Public Methods

Create an instance of the filter class:

<a name="loio7e3cd149955c4f3483d33c21d5c128f9__table_rqx_5xr_lsb"/>CREATE \(static\)


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

Filter object: A reference to the interface `IF_BALI_ITEM_FILTER` 



</td>
</tr>
</table>

Set a table of all severity values which pass the filter. It overwrites all previous filter settings that were linked to severity:

<a name="loio7e3cd149955c4f3483d33c21d5c128f9__table_xvw_jyr_lsb"/>SET\_SEVERITY


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

Table with severity values \(such as 'Error' or 'Warning'\)



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
> -   Valid values of severity can be found in the interface `IF_BALI_CONSTANTS`.
> 
> -   If parameter `SEVERITY_TABLE` contains no entry, all severity values pass the filter.
> 
> -   If parameter `SEVERITY_TABLE` only contains invalid entries, no severity passes the filter.

Apply the filter to a set of log item attributes and check whether it passes the filter:

<a name="loio7e3cd149955c4f3483d33c21d5c128f9__table_phx_gzr_lsb"/>APPLY\_FILTER


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

Severity of the log item that is being checked



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

