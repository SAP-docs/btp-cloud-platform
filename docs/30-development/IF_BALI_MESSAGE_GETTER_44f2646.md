<!-- loio44f264691e504fa5b1552e5dcf4f3338 -->

# IF\_BALI\_MESSAGE\_GETTER

If a message is read from an application log, an object instance of interface `IF_BALI_MESSAGE_GETTER` is returned. It contains the interface `IF_BALI_ITEM_GETTER`.

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

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td>

Category of the item

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_MESSAGE



</td>
</tr>
<tr>
<td>

LOG\_ITEM\_NUMBER

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td>

Serial number which is the position of the message in the log



</td>
</tr>
<tr>
<td>

SEVERITY

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td>

Severity of the message \('Error', 'Warning', etc\)



</td>
</tr>
<tr>
<td>

DETAIL\_LEVEL

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td>

Detail level of the message \(number between '1' and '9' or ' '\)



</td>
</tr>
<tr>
<td>

TIMESTAMP

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td>

UTC time stamp of the message creation



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

Message variable 1



</td>
</tr>
<tr>
<td>

VARIABLE\_2



</td>
<td>

Message variable 2



</td>
</tr>
<tr>
<td>

VARIABLE\_3



</td>
<td>

Message variable 3



</td>
</tr>
<tr>
<td>

VARIABLE\_4



</td>
<td>

Message variable 4



</td>
</tr>
<tr>
<td>

COUNT



</td>
<td>

Count of cumulated messages



</td>
</tr>
</table>



Get the message text of the message \(the output of ABAP command ***MESSAGE***\):

<a name="loio44f264691e504fa5b1552e5dcf4f3338__table_xkf_sjb_xlb"/>**GET\_MESSAGE\_TEXT \(from interface IF\_BALI\_ITEM\_GETTER\):**


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

MESSAGE\_TEXT



</td>
<td>

Text of the message in the logon language



</td>
</tr>
</table>

