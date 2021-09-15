<!-- loio5e25cf7682d9432b840aa11144f2c2ac -->

# CL\_BALI\_LOG \(Interface IF\_BALI\_LOG\)

Class `CL_BALI_LOG` handles all read and change operations on a single application log. It contains methods to read and change the log header. In addition, it allows to read items from the log and to add items to the log. The public interface of the instance methods is `IF_BALI_LOG`.

**Public Methods**



Create an instance of the log class:

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_pyx_h3b_xlb"/>**CREATE \(static\)**


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

LOG



</td>
<td>

Log object: A reference to interface IF\_BALI\_LOG



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_INTERNAL\_ERROR



</td>
<td>

Internal error during processing



</td>
</tr>
</table>



Create an instance of the log class and set the header:

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_xkf_sjb_xlb"/>**CREATE\_WITH\_HEADER \(static\)**


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

HEADER



</td>
<td>

Header which is put into the log: Reference to interface IF\_BALI\_HEADER\_SETTER



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

LOG



</td>
<td>

Log object: A reference to interface IF\_BALI\_LOG



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_POSSIBLE



</td>
<td>

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object of the header is not allowed



</td>
</tr>
<tr>
<td>

CX\_BALI\_INVALID\_PARAMETER



</td>
<td>

The log object or subobject of the header don't exist



</td>
</tr>
<tr>
<td>

CX\_BALI\_INTERNAL\_ERROR



</td>
<td>

Internal error during processing



</td>
</tr>
</table>



Get the log handle which is the unique identifier of the log:

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_hl3_rvh_xlb"/>**GET\_HANDLE**


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

HANDLE



</td>
<td>

Log handle



</td>
</tr>
</table>



Get the log header:

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_gqx_wvh_xlb"/>**GET\_HEADER**


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

HEADER



</td>
<td>

Log header: References to interface IF\_BALI\_HEADER\_GETTER



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_INTERNAL\_ERROR



</td>
<td>

Internal error during processing



</td>
</tr>
</table>



Set the log header:

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_q1k_dwh_xlb"/>**SET\_HEADER**


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

HEADER



</td>
<td>

Header which is put into the log: References to interface IF\_BALI\_HEADER\_SETTER



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_POSSIBLE



</td>
<td>

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object of the header is not allowed



</td>
</tr>
<tr>
<td>

CX\_BALI\_INVALID\_PARAMETER



</td>
<td>

The log object or subobject of the header don't exist



</td>
</tr>
<tr>
<td>

CX\_BALI\_INTERNAL\_ERROR



</td>
<td>

Internal error during processing



</td>
</tr>
</table>



Add an item \(e.g. a message\) to the log:

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_ww2_nwh_xlb"/>**ADD\_ITEM**


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

ITEM



</td>
<td>

Item which is added: Reference to interface IF\_BALI\_ITEM\_SETTER



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_POSSIBLE



</td>
<td>

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object of the header is not allowed



</td>
</tr>
<tr>
<td>

CX\_BALI\_INVALID\_PARAMETER



</td>
<td>

The log object or subobject of the header don't exist



</td>
</tr>
<tr>
<td>

CX\_BALI\_INTERNAL\_ERROR



</td>
<td>

Internal error during processing



</td>
</tr>
</table>

> ### Note:  
> An exception may contain a message. This means that the ABAP exception class contains interface `IF_T100_MESSAGE`, or it contains at least the attributes `T100_MSGID` and `T100_MSGNO`. In this case, the exception is internally converted into a message before it is added to the log.



If the item is a message, it is checked whether the log already contains another message with identical message attributes. These are the attributes: severity, message ID, message number and message variable 1 - 4. If this message exist, the message counter of the message is increased by 1. Otherwise, a new message is added to the log. Also free texts and exceptions are always added to the log without cumulation.

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_sgn_xwh_xlb"/>**CUMULATE\_ITEM**


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

ITEM



</td>
<td>

Item which is cumulated or added: Reference to interface IF\_BALI\_ITEM\_SETTER



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_POSSIBLE



</td>
<td>

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object of the header is not allowed



</td>
</tr>
<tr>
<td>

CX\_BALI\_INVALID\_PARAMETER



</td>
<td>

The log object or subobject of the header don't exist



</td>
</tr>
<tr>
<td>

CX\_BALI\_INTERNAL\_ERROR



</td>
<td>

Internal error during processing



</td>
</tr>
</table>

> ### Note:  
> An exception may contain a message. This means that the ABAP exception class contains interface `IF_T100_MESSAGE`, or it contains at least the attributes `T100_MSGID` and `T100_MSGNO`. In this case, the exception is internally converted to a message before it is added to the log \(but this message is not cumulated to an already existing message\).



Add all messages from an internal table of type `BAPIRETTAB` table to the log:

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_vhr_jxh_xlb"/>**ADD\_MESSAGES\_FROM\_BAPIRETTAB**


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

MESSAGE\_TABLE



</td>
<td>

An internal table with messages which use type BAPIRETTAB



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_POSSIBLE



</td>
<td>

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>TOO\_MANY\_ITEMS:

The maximum number 999999 of items was reached



</td>
</tr>
<tr>
<td>

CX\_BALI\_INVALID\_PARAMETER



</td>
<td>

The message ID of one of the messages is initial



</td>
</tr>
<tr>
<td>

CX\_BALI\_INTERNAL\_ERROR



</td>
<td>

Internal error during processing



</td>
</tr>
</table>

> ### Note:  
> If a message of the message table cannot be added to the log, it is skipped and the processing continues until the end of the table is reached. Afterwards, an exception is raised to notify the caller that some of the messages could not be added to the log.



Get a single item from the log:

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_smp_5xh_xlb"/>**GET\_ITEM**


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

LOG\_ITEM\_NUMBER



</td>
<td>

Serial number of the item which shall be read \(it is the position of the item in the log\)



</td>
</tr>
<tr>
<td colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td>

ITEM



</td>
<td>

Item which was read: Reference to interface IF\_BALI\_ITEM\_GETTER



</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_FOUND



</td>
<td>

An item with the requested log item number does not exist



</td>
</tr>
<tr>
<td>

CX\_BALI\_INTERNAL\_ERROR



</td>
<td>

Internal error during processing



</td>
</tr>
</table>



Get all items from the log:

<a name="loio5e25cf7682d9432b840aa11144f2c2ac__table_lbp_cyh_xlb"/>**GET\_ALL\_ITEMS**


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

ITEM\_TABLE



</td>
<td>

Table of all items which are stored in the log. The table has the following structure:

-   LOG\_ITEM\_NUMBER: The serial number of the item in the log

-   ITEM: Item object: Reference to interface IF\_BALI\_ITEM\_GETTER




</td>
</tr>
<tr>
<td colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**



</td>
</tr>
<tr>
<td>

CX\_BALI\_NOT\_FOUND



</td>
<td>

No item was found in the log



</td>
</tr>
<tr>
<td>

CX\_BALI\_INTERNAL\_ERROR



</td>
<td>

Internal error during processing



</td>
</tr>
</table>

