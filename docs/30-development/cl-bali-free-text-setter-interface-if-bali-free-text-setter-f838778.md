<!-- loiof8387789309344baafcf9a05bbe8059c -->

# CL\_BALI\_FREE\_TEXT\_SETTER \(Interface IF\_BALI\_FREE\_TEXT\_SETTER\)

To add a new free text to an application log, an object of class `CL_BALI_FREE_TEXT_SETTER` is used. The public interface of the instance methods is `IF_BALI_FREE_TEXT_SETTER`. It contains the interface `IF_BALI_ITEM_SETTER`.

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

Contains fixed value: IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_FREE\_TEXT

</td>
</tr>
</table>

**Public Methods**



Create an instance of the free text class and set the text and the severity:

**CREATE \(static\)**


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

TEXT

</td>
<td valign="top">

Free text

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

FREE\_TEXT

</td>
<td valign="top">

Free text object: A reference to interface IF\_BALI\_FREE\_TEXT\_SETTER

</td>
</tr>
</table>



Set the free text and severity:

**SET\_TEXT**


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

TEXT

</td>
<td valign="top">

Free text

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

NEW\_FREE\_TEXT

</td>
<td valign="top">

Reference to current free text object

</td>
</tr>
</table>



Set the level of detail of the free text:

**SET\_DETAIL\_LEVEL**


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

Detail level of the free text

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

NEW\_FREE\_TEXT

</td>
<td valign="top">

Reference to current free text object

</td>
</tr>
</table>



Get all free text values:

**GET\_ALL\_VALUES**


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

DETAIL\_LEVEL

</td>
<td valign="top">

Detail level of the free text

Number between '1' and '9' or ' '

</td>
</tr>
<tr>
<td valign="top">

SEVERITY

</td>
<td valign="top">

Severity of the free text \('Error', 'Warning', etc\)

</td>
</tr>
<tr>
<td valign="top">

TEXT

</td>
<td valign="top">

Content of the free text

</td>
</tr>
</table>



Check whether the free text can pass an item filter:

**CHECK\_PASSING\_ITEM\_FILTER \(from IF\_BALI\_ITEM\_SETTER\)**


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

If set, the free text can pass the item filter

</td>
</tr>
</table>



> ### Note:  
> If the severity of the free text contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_SEVERITY_DEFAULT`. Allowed values of the severity can be found in interface `IF_BALI_CONSTANTS`.
> 
> If the detail level of the free text contains a value which is not allowed, it is changed to `IF_BALI_CONSTANTS=>C_DETAIL_LEVEL_DEFAULT`. Allowed values of the detail level are a number between '1' and '9' and ' '.

