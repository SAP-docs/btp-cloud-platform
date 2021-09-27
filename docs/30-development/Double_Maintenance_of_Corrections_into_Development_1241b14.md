<!-- loio1241b144b83b4ca9a317db326e36950d -->

# Double Maintenance of Corrections into Development

For corrections, double maintenance is necessary so that everything that had to be fixed during release testing or usage can be retrofitted into the development ABAP system.

As there is no selective picking of transport requests to merge corrections back into the main branch, this is manual effort.

You can use the *Compare Editor* in ADT to merge corrections back to the main branch.

The process would be as follows:

You can compare the latest version of an object in your ADT project in a hotfix ABAP system with the latest version of the same object in the development ABAP system. If there are new created objects, you have to create an object manually in the development ABAP system.

To make a comparison, from the context menu of the object in the *Project Explorer* or in the source code editor, choose *Compare With* \> *ABAP project*, where ABAP project is one of the ABAP projects defined in your ADT.


<table>
<tr>
<th>

Step



</th>
<th>

System



</th>
<th>

Role



</th>
<th>

Task



</th>
<th>

Tool



</th>
</tr>
<tr>
<td>

1



</td>
<td>

COR



</td>
<td>

Developer



</td>
<td>

Select the corrected objects in the transport request and open them.

This can be done selectively object by object.



</td>
<td>

ADT for Eclipse: Transport Organizer View



</td>
</tr>
<tr>
<td>

2



</td>
<td>

COR, DEV



</td>
<td>

Developer



</td>
<td>

1.  Select the resources in the Project Explorer in the correction ABAP system COR
2.  From the resource's pop-up menu, select Compare With
3.  Select the ABAP project that points to your development ABAP system DEV



</td>
<td>

ADT for Eclipse: Project Explorer



</td>
</tr>
<tr>
<td>

3



</td>
<td>

DEV



</td>
<td>

Developer



</td>
<td>

Merge the changes into the ABAP system DEV



</td>
<td>

ADT for Eclipse



</td>
</tr>
</table>

