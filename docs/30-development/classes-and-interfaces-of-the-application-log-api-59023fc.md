<!-- loio59023fcd95ec459d8259c1e2840b816a -->

# Classes and Interfaces of the Application Log API

The following classes and interfaces are available:

**Access the Database**


<table>
<tr>
<th valign="top">

Class Name

</th>
<th valign="top">

Public Interface

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

CL\_BALI\_LOG\_DB

</td>
<td valign="top">

IF\_BALI\_LOG\_DB

</td>
<td valign="top">

Handles database access like reading or writing of logs in the database.

</td>
</tr>
<tr>
<td valign="top">

CL\_BALI\_LOG\_FILTER

</td>
<td valign="top">

IF\_BALI\_LOG\_FILTER

</td>
<td valign="top">

Defines a filter for reading of logs from the database.

</td>
</tr>
</table>

**Access the Content of a Log**


<table>
<tr>
<th valign="top">

Class Name

</th>
<th valign="top">

Public Interface

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

CL\_BALI\_LOG

</td>
<td valign="top">

IF\_BALI\_LOG

</td>
<td valign="top">

Reads and writes the header and items of a log

</td>
</tr>
</table>

**Writing the Log Header**


<table>
<tr>
<th valign="top">

Class Name

</th>
<th valign="top">

Public Interface

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

CL\_BALI\_HEADER\_SETTER

</td>
<td valign="top">

IF\_BALI\_HEADER\_SETTER

</td>
<td valign="top">

Log header which can be put into a log

</td>
</tr>
</table>

**Reading the Log Header**


<table>
<tr>
<th valign="top">

Class Name

</th>
<th valign="top">

Public Interface

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

IF\_BALI\_HEADER\_GETTER

</td>
<td valign="top">

Log header which was read from the log

</td>
</tr>
</table>

**Writing a Log Item**


<table>
<tr>
<th valign="top">

Class Name

</th>
<th valign="top">

Public Interface

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

IF\_BALI\_ITEM\_SETTER

</td>
<td valign="top">

Each item contains this interface

</td>
</tr>
<tr>
<td valign="top">

CL\_BALI\_MESSAGE\_SETTER

</td>
<td valign="top">

IF\_BALI\_MESSAGE\_SETTER

</td>
<td valign="top">

Message which can be put into a log

</td>
</tr>
<tr>
<td valign="top">

CL\_BALI\_FREE\_TEXT\_SETTER

</td>
<td valign="top">

IF\_BALI\_FREE\_TEXT\_SETTER

</td>
<td valign="top">

Free text which can be put into a log

</td>
</tr>
<tr>
<td valign="top">

CL\_BALI\_EXCEPTION\_SETTER

</td>
<td valign="top">

IF\_BALI\_EXCEPTION\_SETTER

</td>
<td valign="top">

Exception which can be put into a log

</td>
</tr>
</table>

**Reading a Log Item**


<table>
<tr>
<th valign="top">

Class Name

</th>
<th valign="top">

Public Interface

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

IF\_BALI\_ITEM\_GETTER

</td>
<td valign="top">

Each item contains this interface

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

IF\_BALI\_MESSAGE\_GETTER

</td>
<td valign="top">

Message which was read from the log

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

IF\_BALI\_FREE\_TEXT\_GETTER

</td>
<td valign="top">

Free text which was read from the log

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

IF\_BALI\_EXCEPTION\_GETTER

</td>
<td valign="top">

Exception which was read from the log

</td>
</tr>
</table>

**Other Classes and Interfaces**


<table>
<tr>
<th valign="top">

Class Name

</th>
<th valign="top">

Public Interface

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

IF\_BALI\_CONSTANTS

</td>
<td valign="top">

Some constants, such as available item categories and severities

</td>
</tr>
<tr>
<td valign="top">

CL\_BALI\_ITEM\_FILTER

</td>
<td valign="top">

IF\_BALI\_ITEM\_FILTER

</td>
<td valign="top">

Define an item filter for adding items to a log

</td>
</tr>
</table>

If one of the class methods can't be processed or can't return the requested results, an exception is raised. The following exceptions are possible, each of them inherit from exception class `CX_BALI_RUNTIME`:

**Exception Classes**


<table>
<tr>
<th valign="top">

Class Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`CX_BALI_INVALID_PARAMETER` 

</td>
<td valign="top">

An input parameter of the method is invalid \(e.g. the log object doesn't exist\).

</td>
</tr>
<tr>
<td valign="top">

`CX_BALI_NOT_FOUND` 

</td>
<td valign="top">

The entry which shall be read or changed was not found.

</td>
</tr>
<tr>
<td valign="top">

`CX_BALI_NOT_POSSIBLE` 

</td>
<td valign="top">

The requested processing is not possible.

Possible values of class attribute `ERROR_CODE`:

-   `CX_BALI_NOT_POSSIBLE=>NO_AUTHORIZATION`: No authorization to access the log

-   `CX_BALI_NOT_POSSIBLE=>OBJECT_NOT_ALLOWED`: Access to the log object is not allowed

-   `CX_BALI_NOT_POSSIBLE=>TOO_MANY_ITEMS`: The maximum number 999999 of items was reached

-   `CX_BALI_NOT_POSSIBLE=>SAVE_NOT_ALLOWED`: Error during saving to the database \(e.g. database error or object is empty\)

-   `CX_BALI_NOT_POSSIBLE=>ENTRY_IS_LOCKED`: The enqueue cannot be set, because the log is already locked




</td>
</tr>
<tr>
<td valign="top">

`CX_BALI_INTERNAL_ERROR` 

</td>
<td valign="top">

Internal error during processing

</td>
</tr>
</table>

> ### Note:  
> Find more information about classes and interfaces of the *Application Log API* in the ABAB Development Tools \(ADT\).

