<!-- loio5ff735cf11874b31abc0a8130baaffb8 -->

# IF\_BALI\_ITEM\_GETTER

If an item like a message or exception is read from an application log, its object instance contains the interface `IF_BALI_ITEM_GETTER`. So, interface `IF_BALI_ITEM_GETTER` contains all attributes and methods which are available for all items which are read from the log.

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



</td>
<td valign="top">

Category of the item

Possible values:

-   IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_MESSAGE: Item is a message

-   IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_FREE\_TEXT: Item is a free text

-   IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_EXCEPTION: Item is an exception




</td>
</tr>
<tr>
<td valign="top">

LOG\_ITEM\_NUMBER



</td>
<td valign="top">

Serial number which is the position of the item in the log



</td>
</tr>
<tr>
<td valign="top">

SEVERITY



</td>
<td valign="top">

Severity of the item \('Error', 'Warning', etc\)



</td>
</tr>
<tr>
<td valign="top">

DETAIL\_LEVEL



</td>
<td valign="top">

Detail level of the item \(number between '1' and '9' or ' '\)



</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

\(from IF\_BALI\_ITEM\_GETTER\)



</td>
<td valign="top">

UTC time stamp of the item creation



</td>
</tr>
</table>

**Public Methods**



Get the message text of the item. It is:

-   The output of ABAP command ***MESSAGE*** for a message item

-   The text of a free text item

-   The output of method `GET_TEXT` of the ABAP exception object for an exception item


**GET\_MESSAGE\_TEXT**


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

ext of the item message in the logon language



</td>
</tr>
</table>

