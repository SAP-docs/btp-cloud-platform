<!-- loio40319b1d61284004ad309c42786056f5 -->

# IF\_BALI\_EXCEPTION\_GETTER

If an exception is read from an application log, an object instance of interface `IF_BALI_EXCEPTION_GETTER` is returned. It contains the interface `IF_BALI_ITEM_GETTER`.

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

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_EXCEPTION



</td>
</tr>
<tr>
<td>

LOG\_ITEM\_NUMBER

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td>

Serial number which is the position of the exception in the log



</td>
</tr>
<tr>
<td>

SEVERITY

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td>

Severity of the exception \('Error', 'Warning', etc\)



</td>
</tr>
<tr>
<td>

DETAIL\_LEVEL

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td>

Detail level of the exception \(number between '1' and '9' or ' '\)



</td>
</tr>
<tr>
<td>

TIMESTAMP

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td>

UTC time stamp of the exception creation



</td>
</tr>
<tr>
<td>

EXCEPTION\_CLASS



</td>
<td>

Name of the ABAP exception class



</td>
</tr>
<tr>
<td>

EXCEPTION\_ID\_NAME



</td>
<td>

Name of the Text ID of the ABAP exception



</td>
</tr>
</table>

**Public Methods**



Get the message short text of the exception \(the output of method GET\_TEXT of the ABAP exception object\):

<a name="loio40319b1d61284004ad309c42786056f5__table_xkf_sjb_xlb"/>**GET\_MESSAGE\_TEXT \(from interface IF\_BALI\_ITEM\_GETTER\)**


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

Message short text of the exception in the logon language



</td>
</tr>
</table>

