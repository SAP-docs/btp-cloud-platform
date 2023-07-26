<!-- loio069179d957b345e1bbf3f43da31fa446 -->

# CL\_BALI\_LOG\_DB \(Interface IF\_BALI\_LOG\_DB\)

Class `CL_BALI_LOG_DB` handles all database accesses of the application logs. This includes the reading of one or several logs from the database, writing a log to the database and deleting a log from the database. In addition, it offers methods to set and clear an SAP enqueue on a log. The public interface of the instance methods is `IF_BALI_LOG_DB`.

**Public Methods**



Get an Instance of the Database Handler:

**GET\_INSTANCE \(static\)**


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

DB\_HANDLER



</td>
<td valign="top">

Database handler object: A reference to interface IF\_BALI\_LOG\_DB



</td>
</tr>
</table>



Load a single log from the database into the memory:

**LOAD\_LOG**


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

HANDLE



</td>
<td valign="top">

Handle of the Application Log which shall be read



</td>
</tr>
<tr>
<td valign="top">

READ\_ONLY\_HEADER



</td>
<td valign="top">

\(Optional\): If set, only the header of the log is read \(no items\)

Default: Not set



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

Log which was read from the database: Reference to interface IF\_BALI\_LOG



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

-   The log handle is initial

-   The log was not found in the database




</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE



</td>
<td valign="top">

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED:

    Access to the log object is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>NO\_AUTHORIZATION:

    No authorization to access the log




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
> It is recommended to use method `LOAD_LOG_WITH_ITEMS` if all items should be loaded.
> 
> The following authorization is checked:
> 
> Authorization Object: S\_APPL\_LOG with:
> 
> -   ALG\_OBJECT: Object name of the application log
> 
> -   ALG\_SUBOBJ: Subobject of the application log
> 
> -   ACTVT: 03



Load a single log including all items from the database into the memory:

**LOAD\_LOG\_WITH\_ITEMS**


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

HANDLE



</td>
<td valign="top">

Handle of the application log that should be read



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

Log that was read from the database: Reference to interface IF\_BALI\_LOG



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

-   The log handle is initial

-   The log was not found in the database




</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_POSSIBLE



</td>
<td valign="top">

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>OBJECT\_NOT\_ALLOWED: Access to the log object is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>NO\_AUTHORIZATION: No authorization to access the log




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
> The following authorization is checked:
> 
> Authorization Object: S\_APPL\_LOG with:
> 
> -   ALG\_OBJECT: Object name of the application log
> 
> -   ALG\_SUBOBJ: Subobject of the application log
> 
> -   ACTVT: 03



Load several logs via a filter from the database into the memory:

**LOAD\_LOGS\_VIA\_FILTER**


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

FILTER



</td>
<td valign="top">

Log filter object: Reference to interface IF\_BALI\_LOG\_FILTER



</td>
</tr>
<tr>
<td valign="top">

READ\_ONLY\_HEADER



</td>
<td valign="top">

\(Optional\): If set, only the headers of the logs are read \(no items\)

Default: Not set



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

LOG\_TABLE



</td>
<td valign="top">

Table of logs which were read from the database: Table of references to interface IF\_BALI\_LOG



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

No log can be returned which fits to the filter criteria



</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETERS



</td>
<td valign="top">

-   The filter contains invalid values

-   The filter is initial or empty




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
> It is recommended to use method `LOAD_LOGS_W_ITEMS_VIA_FILTER` if all items should be loaded.
> 
> The following authorization is checked:
> 
> Authorization Object: S\_APPL\_LOG with:
> 
> -   ALG\_OBJECT: Object name of the application log
> 
> -   ALG\_SUBOBJ: Subobject of the application log
> 
> -   ACTVT: 03
> 
> 
> If the object of a log is not allowed or if the log doesn't pass the authorization check, it is removed from the table of logs which is returned. An exception is only raised if the final table is empty.



Load several logs including all items via a filter from the database into the memory:

**LOAD\_LOGs\_W\_ITEMS\_VIA\_FILTER**


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

FILTER



</td>
<td valign="top">

Log filter object: Reference to interface IF\_BALI\_LOG\_FILTER



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Returning parameter**



</td>
</tr>
<tr>
<td valign="top">

LOG\_TABLE



</td>
<td valign="top">

Table of logs which were read from the database: Table of references to interface IF\_BALI\_LOG



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

No log can be returned that fits to the filter criteria



</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_INVALID\_PARAMETERS



</td>
<td valign="top">

-   The filter contains invalid values

-   The filter is initial or empty




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
> The following authorization is checked:
> 
> Authorization Object: S\_APPL\_LOG with:
> 
> -   ALG\_OBJECT: Object name of the application log
> 
> -   ALG\_SUBOBJ: Subobject of the application log
> 
> -   ACTVT: 03
> 
> 
> If the object of a log is not allowed or if the log doesn't pass the authorization check, it's removed from the table of logs that is returned. An exception is only raised if the final table is empty.



Save a single log to the database using the default database connection:

**SAVE\_LOG**


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

LOG



</td>
<td valign="top">

Log that should be saved: Reference to interface IF\_BALI\_LOG



</td>
</tr>
<tr>
<td valign="top">

USE\_2ND\_DB\_CONNECTION



</td>
<td valign="top">

Deprecated: Please use method SAVE\_LOG\_2ND\_DB\_CONNECTION instead



</td>
</tr>
<tr>
<td valign="top">

ASSIGN\_TO\_CURRENT\_APPL\_JOB



</td>
<td valign="top">

\(Optional\): If set, and if the application runs in an application job, a connection between the application log and an application job is established

Default: Not set



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

    Access to the log object is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>SAVE\_NOT\_ALLOWED:

    -   Log object and log subobject are empty

    -   Locking of the log is not possible

    -   Error during saving into the database


-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

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

> ### Note:  
> If parameter LOG is initial, the method returns without exception.



Save a single log to the database using a service connection to the database:

**SAVE\_LOG\_2ND\_DB\_CONNECTION**


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

LOG



</td>
<td valign="top">

Log that should be saved: Reference to interface IF\_BALI\_LOG



</td>
</tr>
<tr>
<td valign="top">

ASSIGN\_TO\_CURRENT\_APPL\_JOB



</td>
<td valign="top">

\(Optional\): If set, and if the application runs in an application job, a connection between the application log and an application job is established

Default: Not set



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

    Access to the log object is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>SAVE\_NOT\_ALLOWED:

    -   Log object and log subobject are empty

    -   Locking of the log is not possible

    -   Error during saving into the database


-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

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

> ### Note:  
> A commit is executed on the service connection after the saving.
> 
> If parameter LOG is initial, the method returns without exception.



Delete a single log from the database:

**DELETE\_LOG**


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

LOG



</td>
<td valign="top">

Log which shall be saved: Reference to interface IF\_BALI\_LOG



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

    Access to the log object is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>NO\_AUTHORIZATION:

    No authorization to access the log

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

    The memory of the log was released. The log can't be used




</td>
</tr>
<tr>
<td valign="top">

CX\_BALI\_NOT\_FOUND



</td>
<td valign="top">

The log was not found in the database



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
> -   If parameter LOG is initial, the method returns without exception.
> 
> -   The following authorization is checked:
> 
>     Authorization Object: S\_APPL\_LOG with:
> 
>     -   ALG\_OBJECT: Object name of the application log
> 
>     -   ALG\_SUBOBJ: Subobject of the application log
> 
>     -   ACTVT: 06



Set an SAP enqueue on a log:

**ENQUEUE**


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

LOG



</td>
<td valign="top">

Log which shall be saved: Reference to interface IF\_BALI\_LOG



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

    Access to the log object is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>ENTRY\_IS\_LOCKED:

    The enqueue can't be set, because the log is already locked

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

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

> ### Note:  
> If parameter LOG is initial, the method returns without exception.



Clear an SAP enqueue from a log:

**DEQUEUE**


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

LOG



</td>
<td valign="top">

Log which shall be saved: Reference to interface IF\_BALI\_LOG



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

    Access to the log object is not allowed

-   ERROR\_CODE: CX\_BALI\_NOT\_POSSIBLE=\>LOG\_WAS\_INVALIDATED:

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

> ### Note:  
> If parameter LOG is initial, the method returns without exception.

