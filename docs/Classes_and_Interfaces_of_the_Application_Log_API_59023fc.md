<!-- loio59023fcd95ec459d8259c1e2840b816a -->

# Classes and Interfaces of the Application Log API

The following classes and interfaces are available:

<a name="loio59023fcd95ec459d8259c1e2840b816a__table_srq_yb2_wlb"/>Access the Database


<table>
<tr>
<th>

Class Name



</th>
<th>

Public Interface



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

CL\_BALI\_LOG\_DB



</td>
<td>

IF\_BALI\_LOG\_DB



</td>
<td>

Handles database access like reading or writing of logs in the database.



</td>
</tr>
<tr>
<td>

CL\_BALI\_LOG\_FILTER



</td>
<td>

IF\_BALI\_LOG\_FILTER



</td>
<td>

Defines a filter for reading of logs from the database.



</td>
</tr>
</table>

<a name="loio59023fcd95ec459d8259c1e2840b816a__table_spc_pc2_wlb"/>Access the Content of a Log


<table>
<tr>
<th>

Class Name



</th>
<th>

Public Interface



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

CL\_BALI\_LOG



</td>
<td>

IF\_BALI\_LOG



</td>
<td>

Reads and writes the header and items of a log



</td>
</tr>
</table>

<a name="loio59023fcd95ec459d8259c1e2840b816a__table_fdy_tc2_wlb"/>Writing the Log Header


<table>
<tr>
<th>

Class Name



</th>
<th>

Public Interface



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

CL\_BALI\_HEADER\_SETTER



</td>
<td>

IF\_BALI\_HEADER\_SETTER



</td>
<td>

Log header which can be put into a log



</td>
</tr>
</table>

<a name="loio59023fcd95ec459d8259c1e2840b816a__table_enp_yc2_wlb"/>Reading the Log Header


<table>
<tr>
<th>

Class Name



</th>
<th>

Public Interface



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

 



</td>
<td>

IF\_BALI\_HEADER\_GETTER



</td>
<td>

Log header which was read from the log



</td>
</tr>
</table>

<a name="loio59023fcd95ec459d8259c1e2840b816a__table_hrx_cd2_wlb"/>Writing a Log Item


<table>
<tr>
<th>

Class Name



</th>
<th>

Public Interface



</th>
<th>

Description



</th>
</tr>
<tr>
<td>



</td>
<td>

IF\_BALI\_ITEM\_SETTER



</td>
<td>

Each item contains this interface



</td>
</tr>
<tr>
<td>

CL\_BALI\_MESSAGE\_SETTER



</td>
<td>

IF\_BALI\_MESSAGE\_SETTER



</td>
<td>

Message which can be put into a log



</td>
</tr>
<tr>
<td>

CL\_BALI\_FREE\_TEXT\_SETTER



</td>
<td>

IF\_BALI\_FREE\_TEXT\_SETTER



</td>
<td>

Free text which can be put into a log



</td>
</tr>
<tr>
<td>

CL\_BALI\_EXCEPTION\_SETTER



</td>
<td>

IF\_BALI\_EXCEPTION\_SETTER



</td>
<td>

Exception which can be put into a log



</td>
</tr>
</table>

<a name="loio59023fcd95ec459d8259c1e2840b816a__table_scl_nd2_wlb"/>Reading a Log Item


<table>
<tr>
<th>

Class Name



</th>
<th>

Public Interface



</th>
<th>

Description



</th>
</tr>
<tr>
<td>



</td>
<td>

IF\_BALI\_ITEM\_GETTER



</td>
<td>

Each item contains this interface



</td>
</tr>
<tr>
<td>



</td>
<td>

IF\_BALI\_MESSAGE\_GETTER



</td>
<td>

Message which was read from the log



</td>
</tr>
<tr>
<td>



</td>
<td>

IF\_BALI\_FREE\_TEXT\_GETTER



</td>
<td>

Free text which was read from the log



</td>
</tr>
<tr>
<td>



</td>
<td>

IF\_BALI\_EXCEPTION\_GETTER



</td>
<td>

Exception which was read from the log



</td>
</tr>
</table>

<a name="loio59023fcd95ec459d8259c1e2840b816a__table_rc3_wd2_wlb"/>Other Classes and Interfaces


<table>
<tr>
<th>

Class Name



</th>
<th>

Public Interface



</th>
<th>

Description



</th>
</tr>
<tr>
<td>



</td>
<td>

IF\_BALI\_CONSTANTS



</td>
<td>

Some constants, such as available item categories and severities



</td>
</tr>
</table>

Exception Classes

If one of the class methods cannot be processed or cannot return the requested results, an exception is raised. The following exceptions are possible, each of them inherit from exception class `CX_BALI_RUNTIME`:

<a name="loio59023fcd95ec459d8259c1e2840b816a__table_nnl_1bb_xlb"/>


<table>
<tr>
<th>

Class Name



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

 `CX_BALI_INVALID_PARAMETER` 



</td>
<td>

An input parameter of the method is invalid \(e.g. the log object doesn't exist\).



</td>
</tr>
<tr>
<td>

 `CX_BALI_NOT_FOUND` 



</td>
<td>

The entry which shall be read or changed was not found.



</td>
</tr>
<tr>
<td>

 `CX_BALI_NOT_POSSIBLE` 



</td>
<td>

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
<td>

 `CX_BALI_INTERNAL_ERROR` 



</td>
<td>

Internal error during processing



</td>
</tr>
</table>

> ### Note:  
> Find more information about classes and interfaces of the *Application Log API* in the ABAB Development Tools \(ADT\).

-   **[CL\_BALI\_LOG\_DB \(Interface IF\_BALI\_LOG\_DB\)](CL_BALI_LOG_DB_(Interface_IF_BALI_LOG_DB)_069179d.md "")**  

-   **[CL\_BALI\_LOG\_FILTER \(Interface IF\_BALI\_LOG\_FILTER\)](CL_BALI_LOG_FILTER_(Interface_IF_BALI_LOG_FILTER)_ec89f52.md "")**  

-   **[CL\_BALI\_LOG \(Interface IF\_BALI\_LOG\)](CL_BALI_LOG_(Interface_IF_BALI_LOG)_5e25cf7.md "")**  

-   **[CL\_BALI\_HEADER\_SETTER \(Interface IF\_BALI\_HEADER\_SETTER\)](CL_BALI_HEADER_SETTER_(Interface_IF_BALI_HEADER_SETTER)_83c9ad5.md "")**  

-   **[CL\_BALI\_MESSAGE\_SETTER \(Interface IF\_BALI\_MESSAGE\_SETTER\)](CL_BALI_MESSAGE_SETTER_(Interface_IF_BALI_MESSAGE_SETTER)_e35417e.md "")**  

-   **[CL\_BALI\_FREE\_TEXT\_SETTER \(Interface IF\_BALI\_FREE\_TEXT\_SETTER\)](CL_BALI_FREE_TEXT_SETTER_(Interface_IF_BALI_FREE_TEXT_SETTER)_f838778.md "")**  

-   **[CL\_BALI\_EXCEPTION\_SETTER \(Interface IF\_BALI\_EXCEPTION\_SETTER\)](CL_BALI_EXCEPTION_SETTER_(Interface_IF_BALI_EXCEPTION_SETTER)_f6be5a9.md "")**  

-   **[IF\_BALI\_HEADER\_GETTER](IF_BALI_HEADER_GETTER_759b29b.md "")**  

-   **[IF\_BALI\_EXCEPTION\_GETTER](IF_BALI_EXCEPTION_GETTER_40319b1.md "")**  

-   **[IF\_BALI\_FREE\_TEXT\_GETTER](IF_BALI_FREE_TEXT_GETTER_6921b78.md "")**  

-   **[IF\_BALI\_ITEM\_GETTER](IF_BALI_ITEM_GETTER_5ff735c.md "")**  

-   **[IF\_BALI\_ITEM\_SETTER](IF_BALI_ITEM_SETTER_ec892a2.md "")**  

-   **[IF\_BALI\_MESSAGE\_GETTER](IF_BALI_MESSAGE_GETTER_44f2646.md "")**  


