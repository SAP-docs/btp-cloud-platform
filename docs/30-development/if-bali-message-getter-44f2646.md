<!-- loio44f264691e504fa5b1552e5dcf4f3338 -->

# IF\_BALI\_MESSAGE\_GETTER

If a message is read from an application log, an object instance of interface `IF_BALI_MESSAGE_GETTER` is returned. It contains the interface `IF_BALI_ITEM_GETTER`.

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

\(from IF\_BALI\_ITEM\_GETTER\)

</td>
<td valign="top">

Category of the item

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_MESSAGE

</td>
</tr>
<tr>
<td valign="top">

LOG\_ITEM\_NUMBER

\(from IF\_BALI\_ITEM\_GETTER\)

</td>
<td valign="top">

Serial number which is the position of the message in the log

</td>
</tr>
<tr>
<td valign="top">

SEVERITY

\(from IF\_BALI\_ITEM\_GETTER\)

</td>
<td valign="top">

Severity of the message \('Error', 'Warning', etc\)

</td>
</tr>
<tr>
<td valign="top">

DETAIL\_LEVEL

\(from IF\_BALI\_ITEM\_GETTER\)

</td>
<td valign="top">

Detail level of the message \(number between '1' and '9' or ' '\)

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

\(from IF\_BALI\_ITEM\_GETTER\)

</td>
<td valign="top">

UTC time stamp of the message creation

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

Message variable 1

</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_2

</td>
<td valign="top">

Message variable 2

</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_3

</td>
<td valign="top">

Message variable 3

</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_4

</td>
<td valign="top">

Message variable 4

</td>
</tr>
<tr>
<td valign="top">

COUNT

</td>
<td valign="top">

Count of cumulated messages

</td>
</tr>
</table>



Get the message text of the message \(the output of ABAP command `MESSAGE`\):

**GET\_MESSAGE\_TEXT \(from interface IF\_BALI\_ITEM\_GETTER\):**


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

MESSAGE\_TEXT

</td>
<td valign="top">

Text of the message in the logon language

</td>
</tr>
</table>

