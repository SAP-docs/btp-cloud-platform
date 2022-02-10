<!-- loioe35417e877b84d3aab807c3a99c136e4 -->

# CL\_BALI\_MESSAGE\_SETTER \(Interface IF\_BALI\_MESSAGE\_SETTER\)

To add a new message to an application log an object of class *CL\_BALI\_MESSAGE\_SETTER* is used. The public interface of the instance methods is *IF\_BALI\_MESSAGE\_SETTER*. It contains the interface *IF\_BALI\_ITEM\_SETTER*.

**Public Attributes**


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

\(from IF\_BALI\_ITEM\_SETTER\)



</td>
<td valign="top">

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
<th valign="top">

Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Importing parameters**



</td>
</tr>
<tr>
<td valign="top">

SEVERITY



</td>
<td valign="top">

\(Optional\): Severity of the message \('Error', 'Warning', etc\)

Default: IF\_BALI\_CONSTANTS=\>C\_SEVERITY\_STATUS



</td>
</tr>
<tr>
<td valign="top">

ID



</td>
<td valign="top">

Message ID



</td>
</tr>
<tr>
<td valign="top">

NUMBER



</td>
<td valign="top">

Message number



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_1



</td>
<td valign="top">

\(Optional\): Message variable 1



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_2



</td>
<td valign="top">

\(Optional\): Message variable 2



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_3



</td>
<td valign="top">

\(Optional\): Message variable 3



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_4



</td>
<td valign="top">

\(Optional\): Message variable 4



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

MESSAGE



</td>
<td valign="top">

Message object: A reference to interface IF\_BALI\_MESSAGE\_SETTER



</td>
</tr>
</table>



Create a message class instance. The message attributes are read from the fields of structure SY \(like SY-MSGID\):

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_egp_ww3_xlb"/>**CREATE\_FROM\_SY \(static\)**


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

MESSAGE



</td>
<td valign="top">

Message object: A reference to interface IF\_BALI\_MESSAGE\_SETTER



</td>
</tr>
</table>



Create a message class instance. The message attributes are read from a structure of type BAPIRET2:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_xmm_cx3_xlb"/>**CREATE\_FROM\_BAPIRET2 \(static\)**


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

MESSAGE\_DATA



</td>
<td valign="top">

Message attributes \(a structure of type BAPIRET2\)



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

MESSAGE



</td>
<td valign="top">

Message object: A reference to interface IF\_BALI\_MESSAGE\_SETTER



</td>
</tr>
</table>



Set attributes of the message:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_rjp_mx3_xlb"/>**SET\_ATTRIBUTES**


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

**Importing parameters**



</td>
</tr>
<tr>
<td valign="top">

SEVERITY



</td>
<td valign="top">

\(Optional\): Severity of the message \('Error', 'Warning', etc\)

Default: IF\_BALI\_CONSTANTS=\>C\_SEVERITY\_STATUS



</td>
</tr>
<tr>
<td valign="top">

ID



</td>
<td valign="top">

Message ID



</td>
</tr>
<tr>
<td valign="top">

NUMBER



</td>
<td valign="top">

Message number



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_1



</td>
<td valign="top">

\(Optional\): Message variable 1



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_2



</td>
<td valign="top">

\(Optional\): Message variable 2



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_3



</td>
<td valign="top">

\(Optional\): Message variable 3



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_4



</td>
<td valign="top">

\(Optional\): Message variable 4



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

NEW\_MESSAGE



</td>
<td valign="top">

Reference to current message object



</td>
</tr>
</table>



Set message attributes from the fields of structure SY \(like SY-MSGID\):

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_a3b_tx3_xlb"/>**SET\_FROM\_SY**


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

NEW\_MESSAGE



</td>
<td valign="top">

Reference to current message object



</td>
</tr>
</table>



Set message attributes from structure BAPIRET2:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_wtt_dy3_xlb"/>**SET\_FROM\_BAPIRET2**


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

MESSAGE\_DATA



</td>
<td valign="top">

Message attributes \(a structure of type BAPIRET2\)



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

MESSAGE



</td>
<td valign="top">

Reference to current message object



</td>
</tr>
</table>



Set the level of detail of the item:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_nhn_3y3_xlb"/>**SET\_DETAIL\_LEVEL**


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

DETAIL\_LEVEL



</td>
<td valign="top">

Detail level of the item

Allowed values: Number between '1' and '9' or ' '



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

MESSAGE



</td>
<td valign="top">

Reference to current message object



</td>
</tr>
</table>



Get all message values:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_i4j_ny3_xlb"/>**GET\_ALL\_VALUES**


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

**Exporting parameters**



</td>
</tr>
<tr>
<td valign="top">

DETAIL\_LEVELDETAIL\_LEVEL



</td>
<td valign="top">

Detail Level of the item \(number between '1' and '9' or ' '\)



</td>
</tr>
<tr>
<td valign="top">

SEVERITY



</td>
<td valign="top">

Severity of the message \('Error', 'Warning', etc\)



</td>
</tr>
<tr>
<td valign="top">

ID



</td>
<td valign="top">

Message ID



</td>
</tr>
<tr>
<td valign="top">

NUMBER



</td>
<td valign="top">

Message number



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_1



</td>
<td valign="top">

\(Optional\): Message variable 1



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_2



</td>
<td valign="top">

\(Optional\): Message variable 2



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_3



</td>
<td valign="top">

\(Optional\): Message variable 3



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_4



</td>
<td valign="top">

\(Optional\): Message variable 4



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

NEW\_MESSAGE



</td>
<td valign="top">

Reference to current message object



</td>
</tr>
</table>



Check whether the message can pass an item filter:

<a name="loioe35417e877b84d3aab807c3a99c136e4__table_a4v_d2r_lsb"/>CHECK\_PASSING\_ITEM\_FILTER \(from IF\_BALI\_ITEM\_SETTER\)


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

If set, the message can pass the item filter



</td>
</tr>
</table>



> ### Note:  
> If the severity of the message contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_SEVERITY_DEFAULT`. Allowed values of the severity can be found in interface`IF_BALI_CONSTANTS`.
> 
> If the detail level of the message contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_DETAIL_LEVEL_DEFAULT`. Allowed values of the detail level are a number between '1' and '9' and ' '.
> 
> If the message attributes are set from structure `BAPIRET2`, only the fields TYPE, ID, NUMBER, MESSAGE\_V1, MESSAGE\_V2, MESSAGE\_V3 and MESSAGE\_V4 of the structure are considered.

