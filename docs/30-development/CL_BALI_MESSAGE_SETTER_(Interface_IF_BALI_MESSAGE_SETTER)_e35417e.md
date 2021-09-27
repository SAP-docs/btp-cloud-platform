<!-- loioe35417e877b84d3aab807c3a99c136e4 -->

# CL\_BALI\_MESSAGE\_SETTER \(Interface IF\_BALI\_MESSAGE\_SETTER\)

To add a new message to an application log an object of class *CL\_BALI\_MESSAGE\_SETTER* is used. The public interface of the instance methods is *IF\_BALI\_MESSAGE\_SETTER*. It contains the interface *IF\_BALI\_ITEM\_SETTER*.

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

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_MESSAGE



</td>
</tr>
</table>

**Public Methods**



Create a message class instance and set the message attributes:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_xkf_sjb_xlb"/>**CREATE \(static\)**


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

ID



</td>
<td>

Message ID



</td>
</tr>
<tr>
<td>

NUMBER



</td>
<td>

Message number



</td>
</tr>
<tr>
<td>

VARIABLE\_1



</td>
<td>

\(Optional\): Message variable 1



</td>
</tr>
<tr>
<td>

VARIABLE\_2



</td>
<td>

\(Optional\): Message variable 2



</td>
</tr>
<tr>
<td>

VARIABLE\_3



</td>
<td>

\(Optional\): Message variable 3



</td>
</tr>
<tr>
<td>

VARIABLE\_4



</td>
<td>

\(Optional\): Message variable 4



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

MESSAGE



</td>
<td>

Message object: A reference to interface IF\_BALI\_MESSAGE\_SETTER



</td>
</tr>
</table>



Create a message class instance. The message attributes are read from the fields of structure SY \(like SY-MSGID\):

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_egp_ww3_xlb"/>**CREATE\_FROM\_SY \(static\)**


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

**Returning parameter**



</td>
</tr>
<tr>
<td>

MESSAGE



</td>
<td>

Message object: A reference to interface IF\_BALI\_MESSAGE\_SETTER



</td>
</tr>
</table>



Create a message class instance. The message attributes are read from a structure of type BAPIRET2:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_xmm_cx3_xlb"/>**CREATE\_FROM\_BAPIRET2 \(static\)**


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

MESSAGE\_DATA



</td>
<td>

Message attributes \(a structure of type BAPIRET2\)



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

MESSAGE



</td>
<td>

Message object: A reference to interface IF\_BALI\_MESSAGE\_SETTER



</td>
</tr>
</table>



Set attributes of the message:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_rjp_mx3_xlb"/>**SET\_ATTRIBUTES**


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

ID



</td>
<td>

Message ID



</td>
</tr>
<tr>
<td>

NUMBER



</td>
<td>

Message number



</td>
</tr>
<tr>
<td>

VARIABLE\_1



</td>
<td>

\(Optional\): Message variable 1



</td>
</tr>
<tr>
<td>

VARIABLE\_2



</td>
<td>

\(Optional\): Message variable 2



</td>
</tr>
<tr>
<td>

VARIABLE\_3



</td>
<td>

\(Optional\): Message variable 3



</td>
</tr>
<tr>
<td>

VARIABLE\_4



</td>
<td>

\(Optional\): Message variable 4



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_MESSAGE



</td>
<td>

Reference to current message object



</td>
</tr>
</table>



Set message attributes from the fields of structure SY \(like SY-MSGID\):

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_a3b_tx3_xlb"/>**SET\_FROM\_SY**


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

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_MESSAGE



</td>
<td>

Reference to current message object



</td>
</tr>
</table>



Set message attributes from structure BAPIRET2:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_wtt_dy3_xlb"/>**SET\_FROM\_BAPIRET2**


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

MESSAGE\_DATA



</td>
<td>

Message attributes \(a structure of type BAPIRET2\)



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

MESSAGE



</td>
<td>

Reference to current message object



</td>
</tr>
</table>



Set the level of detail of the item:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_nhn_3y3_xlb"/>**SET\_DETAIL\_LEVEL**


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

Detail level of the item

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

MESSAGE



</td>
<td>

Reference to current message object



</td>
</tr>
</table>



Get all message values:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_i4j_ny3_xlb"/>**GET\_ALL\_VALUES**


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

DETAIL\_LEVELDETAIL\_LEVEL



</td>
<td>

Detail Level of the item \(number between '1' and '9' or ' '\)



</td>
</tr>
<tr>
<td>

SEVERITY



</td>
<td>

Severity of the message \('Error', 'Warning', etc\)



</td>
</tr>
<tr>
<td>

ID



</td>
<td>

Message ID



</td>
</tr>
<tr>
<td>

NUMBER



</td>
<td>

Message number



</td>
</tr>
<tr>
<td>

VARIABLE\_1



</td>
<td>

\(Optional\): Message variable 1



</td>
</tr>
<tr>
<td>

VARIABLE\_2



</td>
<td>

\(Optional\): Message variable 2



</td>
</tr>
<tr>
<td>

VARIABLE\_3



</td>
<td>

\(Optional\): Message variable 3



</td>
</tr>
<tr>
<td>

VARIABLE\_4



</td>
<td>

\(Optional\): Message variable 4



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

NEW\_MESSAGE



</td>
<td>

Reference to current message object



</td>
</tr>
</table>



> ### Note:  
> If the severity of the message contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_SEVERITY_DEFAULT`. Allowed values of the severity can be found in interface`IF_BALI_CONSTANTS`.
> 
> If the detail level of the message contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_DETAIL_LEVEL_DEFAULT`. Allowed values of the detail level are a number between '1' and '9' and ' '.
> 
> If the message attributes are set from structure `BAPIRET2`, only the fields TYPE, ID, NUMBER, MESSAGE\_V1, MESSAGE\_V2, MESSAGE\_V3 and MESSAGE\_V4 of the structure are considered.

