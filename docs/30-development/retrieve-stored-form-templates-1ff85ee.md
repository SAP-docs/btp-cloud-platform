<!-- loio1ff85ee73c784dd1ae9abe72e2c43003 -->

# Retrieve Stored Form Templates

Using ABAP development tools for Eclipse, you can upload form templates designed with the Adobe LiveCycle Designer directly to the system. See [Working with Forms](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/working-with-forms).

The class `CL_FP_FORM_READER` enables the usage of uploaded form templates during runtime.



<a name="loio1ff85ee73c784dd1ae9abe72e2c43003__section_ls2_23c_3fc"/>

## Initiate the Form Template Reader

Initiate the class by providing the name of the uploaded form template.

> ### Sample Code:  
> ```
> data(lo_reader) = cl_fp_form_reader=>create_form_reader( 'MY_FORM' ).
> ```



<a name="loio1ff85ee73c784dd1ae9abe72e2c43003__section_ent_h3c_3fc"/>

## Read Stored Attributes

The reader class offers the following read-only methods to retrieve the stored attributes.

****


<table>
<tr>
<th valign="top">

Method Name

</th>
<th valign="top">

Output Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

get\_data\_optimized

</td>
<td valign="top">

fpoptimize

</td>
<td valign="top">

Is data optimization enabled for the connected Form Data Provider?

</td>
</tr>
<tr>
<td valign="top">

get\_font\_embed

</td>
<td valign="top">

fpfntemb

</td>
<td valign="top">

Is font embedding automatically enabled when rendering the form?

</td>
</tr>
<tr>
<td valign="top">

get\_fdp\_name

</td>
<td valign="top">

fpdpname

</td>
<td valign="top">

The name of the connected Form Data Provider

</td>
</tr>
</table>

All of these methods do not support any additional import parameters.



<a name="loio1ff85ee73c784dd1ae9abe72e2c43003__section_nqv_t3c_3fc"/>

## Read Layout Content to be Used by ADS Rendering Call

The reader class also enables you to retrieve the layout.

The `GET_LAYOUT` method has the following returning parameters:

****


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Definition

</th>
</tr>
<tr>
<td valign="top">

RV\_LAYOUT

</td>
<td valign="top">

Resulting XML as XSTRING

</td>
</tr>
</table>

