<!-- loiof6be5a9b0d124920b51c626f2e7669cf -->

# CL\_BALI\_EXCEPTION\_SETTER \(Interface IF\_BALI\_EXCEPTION\_SETTER\)

To add a new exception to an application log, an object of class `CL_BALI_EXCEPTION_SETTER` is used. The public interface of the instance methods is `IF_BALI_EXCEPTION_SETTER`. It contains the interface `IF_BALI_ITEM_SETTER`.

**Public Attributes**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

CATEGORY

\(from IF\_BALI\_ITEM\_SETTER\)



</td>
<td>

Category of the item

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_EXCEPTION



</td>
</tr>
</table>

**Public Methods**



Create an instance of the exception class. Set the reference of the ABAP exception which is stored in the exception item and its severity:

<a name="loiof6be5a9b0d124920b51c626f2e7669cf__table_xkf_sjb_xlb"/>**CREATE \(static\)**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td>

SEVERITY



</td>
<td>

\(Optional\): Severity of the message \('Error', 'Warning', etc\)

Default: IF\_BALI\_CONSTANTS=\>C\_SEVERITY\_STATUS



</td>
</tr>
<tr>
<td>

EXCEPTION



</td>
<td>

Reference to ABAP exception class instance



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

EXCEPTION\_OBJ



</td>
<td>

Exception object: A reference to interface IF\_BALI\_EXCEPTION\_SETTER



</td>
</tr>
</table>



Set the ABAP exception class instance and severity:

<a name="loiof6be5a9b0d124920b51c626f2e7669cf__table_k35_3xn_xlb"/>**SET\_EXCEPTION**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td>

SEVERITY



</td>
<td>

\(Optional\): Severity of the message \('Error', 'Warning', etc\)

Default: IF\_BALI\_CONSTANTS=\>C\_SEVERITY\_STATUS



</td>
</tr>
<tr>
<td>

EXCEPTION



</td>
<td>

Reference to ABAP exception class instance



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_EXCEPTION\_OBJ



</td>
<td>

Reference to current application log exception object



</td>
</tr>
</table>



Set the level of detail of the exception:

<a name="loiof6be5a9b0d124920b51c626f2e7669cf__table_on2_4xn_xlb"/>**SET\_DETAIL\_LEVEL**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Importing parameter**



</td>
</tr>
<tr>
<td>

DETAIL\_LEVEL



</td>
<td>

Detail level of the exception

Allowed values: Number between '1' and '9' or ' '



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_EXCEPTION\_OBJ



</td>
<td>

Reference to current application log exception object



</td>
</tr>
</table>



Get all exception values:



<a name="loiof6be5a9b0d124920b51c626f2e7669cf__table_qfw_xvn_xlb"/>**GET\_ALL\_VALUES**


<table>
<tr>
<th>

Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td colspan="2">

**Exporting parameters**



</td>
</tr>
<tr>
<td>

DETAIL\_LEVEL



</td>
<td>

Detail level of the exception \(number between '1' and '9' or ' '\)



</td>
</tr>
<tr>
<td>

SEVERITY



</td>
<td>

Severity of the exception \('Error', 'Warning', etc\)



</td>
</tr>
<tr>
<td>

EXCEPTION



</td>
<td>

Reference to ABAP exception class instance



</td>
</tr>
</table>



> ### Note:  
> If the severity of the exception contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_SEVERITY_DEFAULT`. Allowed values of the severity can be found in interface `IF_BALI_CONSTANTS`.
> 
> If the detail level of the exception contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_DETAIL_LEVEL_DEFAULT`. Allowed values of the detail level are a number between '1' and '9' and ' '.

