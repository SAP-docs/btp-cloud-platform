<!-- loio986855193ceb4e06862ac78466327928 -->

# Runtime API

You can activate a business configuration set using a class-based API by specifying the relevant activation options. Activation options are certain parameters that can be specified pertaining to the activation of the Business Configuration Set.

The following steps are involved in activating a business configuration set:

1.  [Accessing the Activation Handler](accessing-the-activation-handler-e082053.md)
2.  [Specifying the Activation Options](specifying-the-activation-options-cc4c06c.md)
3.  [Activating the Business Configuration Set](activating-the-business-configuration-set-2ae05a5.md)
4.  [Accessing the Activation Results](accessing-the-activation-results-97e7b42.md)

The class `CL_SCPR_CD_BCSET_ACTIVATION` enables the activation of a Business Configuration set.

**Class CL\_SCPR\_CD\_BCSET\_ACTIVATION**


<table>
<tr>
<th valign="top">

Method

</th>
<th valign="top">

Interface

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`OF`

</td>
<td valign="top">

 

</td>
<td valign="top">

Instantiate the activation API

</td>
</tr>
<tr>
<td valign="top">

`OPTIONS`

</td>
<td valign="top">

 

</td>
<td valign="top">

Access the activation options

</td>
</tr>
<tr>
<td valign="top">

`GET_ACTIVATE_HANDLER`

</td>
<td valign="top">

`IF_SCPR_CD_BCSET_ACTIVATION`

</td>
<td valign="top">

Access the activation handler

</td>
</tr>
</table>

**Exception Class**


<table>
<tr>
<th valign="top">

Class Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`CX_SCPR_OBJECT_NOT_PERMITTED`

</td>
<td valign="top">

The Activation of the specified business configuration set is not permitted.

Possible reasons :

-   `CX_SCPR_OBJECT_NOT_PERMITTED=>BC_SET_NOT_FOUND` 

    The specified business configuration set does not exist.

-   `CX_SCPR_OBJECT_NOT_PERMITTED=>BC_SET_NOT_PERMITTED`

    The specified business configuration set is not permitted to be activated based on the object restrictions or language version check.




</td>
</tr>
</table>

