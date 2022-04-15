<!-- loio1241b144b83b4ca9a317db326e36950d -->

# Double Maintenance of Corrections into Development

For corrections, double maintenance is necessary so that everything that had to be fixed during release testing or usage can be retrofitted into the development system.

As there is no selective picking of transport requests to merge corrections back into the main branch, this is manual effort.

You can use the *Compare Editor* in ABAP Development Tools for Eclipse to merge corrections back to the main branch.

The process would be as follows:

You can compare the latest version of an object in your ABAP Development Tools project in a hotfix system with the latest version of the same object in the development system. If there are newly created objects, you have to create an object manually in the development ABAP system.

To make a comparison, from the context menu of the object in the *Project Explorer* or in the source code editor, choose *Compare With* \> *ABAP project*, where ABAP project is one of the ABAP projects defined in ABAP Development Tools.


<table>
<tr>
<th valign="top">

Step



</th>
<th valign="top">

System



</th>
<th valign="top">

Role



</th>
<th valign="top">

Task



</th>
<th valign="top">

Tool



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

COR



</td>
<td valign="top">

Developer



</td>
<td valign="top">

Select the corrected objects in the transport request and open them.

This can be done selectively object by object.



</td>
<td valign="top">

ABAP Development Tools for Eclipse: Transport Organizer View



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

COR, DEV



</td>
<td valign="top">

Developer



</td>
<td valign="top">

1.  Select the resources in the Project Explorer in correction system COR
2.  From the resource's pop-up menu, select Compare With
3.  Select the ABAP project that points to your development system DEV



</td>
<td valign="top">

ABAP Development Tools for Eclipse: Project Explorer



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Developer



</td>
<td valign="top">

Merge the changes into the DEV system



</td>
<td valign="top">

ABAP Development Tools for Eclipse



</td>
</tr>
</table>

