<!-- loioe3251557f960469d9b9282bf18fb94d4 -->

# Classes and Interfaces of the Design Time API

You can use the `CL_BALI_OBJECT_HANDLER` class as *Application Log Design Time API* to create, change, read, or delete application log objects or subobjects. It uses the public interface `IF_BALI_OBJECT_HANDLER`.

**Public Methods**

<a name="loioe3251557f960469d9b9282bf18fb94d4__table_xc4_gls_wlb"/>GET\_INSTANCE \(static\)


<table>
<tr>
<th>

Parameter



</th>
<th>

Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

RO\_OBJ\_HANDLER



</td>
<td>

Returning



</td>
<td>

Create, change or delete application log objects



</td>
</tr>
</table>

Create a new application log object, optionally with subobjects.

<a name="loioe3251557f960469d9b9282bf18fb94d4__table_ghf_4ls_wlb"/>IF\_BALI\_OBJECT\_HANDLER~CREATE\_OBJECT


<table>
<tr>
<th>

Parameter



</th>
<th>

Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

IV\_OBJECT



</td>
<td>

Importing



</td>
<td>

New application log object



</td>
</tr>
<tr>
<td>

IV\_OBJECT\_TEXT



</td>
<td>

Importing



</td>
<td>

Description for new application log object



</td>
</tr>
<tr>
<td>

IT\_SUBOBJECTS



</td>
<td>

Importing



</td>
<td>

Table of new application log subobjects



</td>
</tr>
<tr>
<td>

IV\_PACKAGE



</td>
<td>

Importing



</td>
<td>

Package



</td>
</tr>
<tr>
<td>

IV\_TRANSPORT\_REQUEST



</td>
<td>

Importing



</td>
<td>

Transport request



</td>
</tr>
</table>

> ### Note:  
> The input of a table of subobjects for parameter `IT_SUBOBJECTS` is optional. If parameters `IV_PACKAGE` and `IV_TRANSPORT_REQUEST` are not provided, it is assumed that a local object shall be created.

Delete an application log object and all of its subobjects.

<a name="loioe3251557f960469d9b9282bf18fb94d4__table_msz_kms_wlb"/>IF\_BALI\_OBJECT\_HANDLER~DELETE\_OBJECT


<table>
<tr>
<th>

Parameter



</th>
<th>

Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

IV\_OBJECT



</td>
<td>

Importing



</td>
<td>

Application log object



</td>
</tr>
<tr>
<td>

IV\_TRANSPORT\_REQUEST



</td>
<td>

Importing



</td>
<td>

Transport request



</td>
</tr>
</table>

Add a new subobject to an existing application log object.

<a name="loioe3251557f960469d9b9282bf18fb94d4__table_sfj_sms_wlb"/>IF\_BALI\_OBJECT\_HANDLER~ADD\_SUBOBJECT


<table>
<tr>
<th>

Parameter



</th>
<th>

Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

IV\_OBJECT



</td>
<td>

Importing



</td>
<td>

Application log object



</td>
</tr>
<tr>
<td>

IV\_SUBOBJECT



</td>
<td>

Importing



</td>
<td>

New application log subobject



</td>
</tr>
<tr>
<td>

IV\_SUBOBJECT\_TEXT



</td>
<td>

Importing



</td>
<td>

Description for new application log subobject



</td>
</tr>
<tr>
<td>

IV\_TRANSPORT\_REQUEST



</td>
<td>

Importing



</td>
<td>

Transport request



</td>
</tr>
</table>

Delete a subobject from an application log object.

<a name="loioe3251557f960469d9b9282bf18fb94d4__table_dlh_dns_wlb"/>IF\_BALI\_OBJECT\_HANDLER~DELETE\_SUBOBJECT


<table>
<tr>
<th>

Parameter



</th>
<th>

Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

IV\_OBJECT



</td>
<td>

Importing



</td>
<td>

Application log object



</td>
</tr>
<tr>
<td>

IV\_SUBOBJECT



</td>
<td>

Importing



</td>
<td>

Application log subobject



</td>
</tr>
<tr>
<td>

IV\_TRANSPORT\_REQUEST



</td>
<td>

Importing



</td>
<td>

Transport request



</td>
</tr>
</table>

Read an application log object and all of its subobjects

<a name="loioe3251557f960469d9b9282bf18fb94d4__table_ffl_3ns_wlb"/>IF\_BALI\_OBJECT\_HANDLER~READ\_OBJECT


<table>
<tr>
<th>

Parameter



</th>
<th>

Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

IV\_OBJECT



</td>
<td>

Importing



</td>
<td>

Application log object



</td>
</tr>
<tr>
<td>

EV\_OBJECT\_TEXT



</td>
<td>

Importing



</td>
<td>

Description for an application log object



</td>
</tr>
<tr>
<td>

ET\_SUBOBJECTS



</td>
<td>

Importing



</td>
<td>

Table of application log subobjects



</td>
</tr>
</table>

> ### Note:  
> For all methods, `IV_TRANSPORT_REQUEST` is not required for local objects.
> 
> All methods of `IF_BALI_OBJECT_HANDLER` include exception `CX_BALI_OBJECTS`.

