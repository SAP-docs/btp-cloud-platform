<!-- loio5e25cf7682d9432b840aa11144f2c2ac -->

# CL\_BALI\_LOG \(Interface IF\_BALI\_LOG\)

Class `CL_BALI_LOG` handles all read and change operations on a single application log. It contains methods to read and change the log header. In addition, it allows to read items from the log and to add items to the log. The public interface of the instance methods is `IF_BALI_LOG`.

**Public Methods**



Create an instance of the log class:

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

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

LOG

</td>
<td valign="top">

Log object: A reference to interface IF\_BALI\_LOG

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>



Create an instance of the log class and set the header:

**CREATE\_WITH\_HEADER \(static\)**


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

HEADER

</td>
<td valign="top">

Header which is put into the log: Reference to interface IF\_BALI\_HEADER\_SETTER

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

LOG

</td>
<td valign="top">

Log object: A reference to interface IF\_BALI\_LOG

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

Access to the log object of the header is not allowed

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

The log object or subobject of the header don't exist

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>



Get the log handle which is the unique identifier of the log:

**GET\_HANDLE**


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

HANDLE

</td>
<td valign="top">

Log handle

</td>
</tr>
</table>



Get the log header:

**GET\_HEADER**


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

HEADER

</td>
<td valign="top">

Log header: References to interface IF\_BALI\_HEADER\_GETTER

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

The memory of the log was released. The log can't be used

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>



Set the log header:

**SET\_HEADER**


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

HEADER

</td>
<td valign="top">

Header which is put into the log: References to interface IF\_BALI\_HEADER\_SETTER

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

    Access to the log object of the header is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

    The memory of the log was released. The log can't be used




</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

The log object or subobject of the header don't exist

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>



Add an item \(e.g. a message\) to the log:

**ADD\_ITEM**


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

ITEM

</td>
<td valign="top">

Item which is added: Reference to interface IF\_BALI\_ITEM\_SETTER

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

    Access to the log object of the header is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

    The memory of the log was released. The log can't be used




</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

The log object or subobject of the header don't exist

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>

> ### Note:  
> An exception may contain a message. This means that the ABAP exception class contains interface `IF_T100_MESSAGE`, or it contains at least the attributes `T100_MSGID` and `T100_MSGNO`. In this case, the exception is internally converted into a message before it is added to the log.



If the item is a message, it's checked whether the log already contains another message with identical message attributes. These are the attributes: severity, message ID, message number and message variable 1 - 4. If this message exist, the message counter of the message is increased by 1. Otherwise, a new message is added to the log. Also free texts and exceptions are always added to the log without cumulation.

**CUMULATE\_ITEM**


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

ITEM

</td>
<td valign="top">

Item which is cumulated or added: Reference to interface IF\_BALI\_ITEM\_SETTER

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

    Access to the log object of the header is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

    The memory of the log was released. The log can't be used




</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

The log object or subobject of the header don't exist

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>

> ### Note:  
> An exception may contain a message. This means that the ABAP exception class contains interface `IF_T100_MESSAGE`, or it contains at least the attributes `T100_MSGID` and `T100_MSGNO`. In this case, the exception is internally converted to a message before it is added to the log \(but this message is not cumulated to an already existing message\).



Add all messages from an internal table of type `BAPIRETTAB` table to the log:

**ADD\_MESSAGES\_FROM\_BAPIRETTAB**


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

MESSAGE\_TABLE

</td>
<td valign="top">

An internal table with messages which use type BAPIRETTAB

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>TOO\_MANY\_ITEMS:

    The maximum number 999999 of items was reached

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

    The memory of the log was released. The log can't be used




</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

The message ID of one of the messages is initial

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>

> ### Note:  
> If a message of the message table can't be added to the log, it's skipped and the processing continues until the end of the table is reached. Afterwards, an exception is raised to notify the caller that some of the messages couldn't be added to the log.



Add a message from the ABAP Restful Application Programming Model \(interface IF\_ABAP\_BEHV\_MESSAGE\) to the log:

**ADD\_ABAP\_BEHAVIOR\_MESSAGE**


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

MESSAGE

</td>
<td valign="top">

A reference to the interface IF\_ABAP\_BEHV\_MESSAGE

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>TOO\_MANY\_ITEMS: The maximum number 999999 of items was reached

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED: The memory of the log was released. The log can't be used




</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

The message ID of the messages is initial

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>



Add all items from another log to this log:

**ADD\_ALL\_ITEMS\_FROM\_OTHER\_LOG**


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

SOURCE\_LOG

</td>
<td valign="top">

Reference to the log whose items are to be copied

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>TOO\_MANY\_ITEMS: The maximum number of 999999 items was reached

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED: The memory of the log was released. The log can't be used




</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETER

</td>
<td valign="top">

The source log is invalid. It contains a log handle which doesn't exist

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>

> ### Note:  
> If the parameter `SOURCE_LOG` is initial, the processing is skipped and no exception is raised.



Add an item filter to the log. The item filter is checked before an item is added to the log using the methods ADD\_ITEM, CUMULATE\_ITEM, ADD\_MESSAGES\_FROM\_BAPIRETTAB, or ADD\_ABAP\_BEHAVIOR\_MESSAGE. If an item doesn't pass the filter, it's ignored.

**SET\_FILTER\_FOR\_ADD\_ITEM**


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

FILTER

</td>
<td valign="top">

A reference to the item filter

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED: The memory of the log was released. The log can't be used

</td>
</tr>
</table>

> ### Note:  
> -   If FILTER is initial, any item filter is removed from the log. The log then no longer uses an item filter.
> 
> -   Since the method ADD\_ALL\_ITEMS\_FROM\_OTHER\_LOG is intended for the mass-processing of items, it ignores the item filter because of performance reasons.
> 
> -   The filter is only used by methods of the class CL\_BALI\_LOG. If an application uses the application log function modules to add an item to the log, the filter is ignored.



Get the item filter which was set using SET\_FILTER\_FOR\_ADD\_ITEM.

**GET\_FILTER\_FOR\_ADD\_ITEM**


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

FILTER

</td>
<td valign="top">

A reference to the item filter which is currently used by the log

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED: The memory of the log was released. The log can't be used

</td>
</tr>
</table>



Get a single item from the log:

**GET\_ITEM**


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

LOG\_ITEM\_NUMBER

</td>
<td valign="top">

Serial number of the item which shall be read \(it is the position of the item in the log\)

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**

</td>
</tr>
<tr>
<td valign="top">

ITEM

</td>
<td valign="top">

Item which was read: Reference to interface IF\_BALI\_ITEM\_GETTER

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_FOUND

</td>
<td valign="top">

An item with the requested log item number does not exist

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED: The memory of the log was released. The log can't be used

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>



Get all items from the log:

**GET\_ALL\_ITEMS**


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

ITEM\_TABLE

</td>
<td valign="top">

Table of all items which are stored in the log. The table has the following structure:

-   LOG\_ITEM\_NUMBER: The serial number of the item in the log

-   ITEM: Item object: Reference to interface IF\_BALI\_ITEM\_GETTER




</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Exceptions \(inherit from CX\_BALI\_RUNTIME\)**

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_FOUND

</td>
<td valign="top">

No item was found in the log

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE

</td>
<td valign="top">

ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED: The memory of the log was released. The log can't be used

</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INTERNAL\_ERROR

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>





### RELEASE\_MEMORY:

Remove the log from the memory. After this, the log is invalidated and can no longer be used.



Check whether the memory of the log was released in order to verify that the log is invalidated and can no longer be used.

**IS\_INVALIDATED**


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

IS\_INVALIDATED

</td>
<td valign="top">

If set, the log is invalidated and can no longer be used

</td>
</tr>
</table>

