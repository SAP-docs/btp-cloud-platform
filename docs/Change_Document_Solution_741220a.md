<!-- loio741220a1097d4b6ebff3a09c0dd35627 -->

# Change Document Solution

You can document changes made to a commercial object, such as the time, the content and the way changes are made, by logging these changes in a change document.

> ### Example:  
> You can use the change document to simplify the change history analysis for auditing in *Financial Accounting*.

Every application object type has its own change document object type, which is called the *Change Document Object*. To log changes to a commercial object in a change document, you must define the *Change Document Object* for the commercial object type. The *Change Document Object* definition contains the tables which represent a commercial object in the system.

> ### Note:  
> -   Specifiy for each table, whether a commercial object contains only one \(single case\) or several \(multiple case\) records. For example, an order contains an order header and several order items. In general, one record for the order header and several records for the order items are passed to the change document creation when an order is changed.
> 
> -   If a table contains fields with values referring to units and currency fields, the associated table, containing these units and currencies, can also be specified.
> 
> -   The object ID identifies a given commercial object. You can retrieve all changes made to a commercial object using this key.

**Change Document Structure**

-   Change Document Header

    The change document header is the part of the change document which contains general information about the changes made. The document header is identified by object class name, the object ID and a change document number \(automatically provided by the runtime system\). The change document header contains information about who made the changes, when they were made, what type of changes were made \(update, insert or delete operation\) and if they were real or planned changes. Starting with Release 6.20 information about the system language and the length of the table key of the documented table are saved here as well. The header data is stored in table `CDHDR`.

-   Change Document Item

    The change document item contains the old and new values of a field for a particular change, and a change flag, that presents the kind of change. The change flag can take the following values:

    -   U = Update

        Changed data. \(Log entry for each changed field which was flagged in the Dictionary as *change document relevant*.

    -   I = Insert

        Data Inserted.

        Changes: Log entry for the whole table record.

        Planned changes: Log entry for each table record field.

    -   D = Delete

        Data were deleted \(log entry for the whole table record\).

    -   E = Individual field documentation at Delete

        Delete a table record with field documentation.

        One log entry per field of the deleted table entry.

    -   J = Individual field documentation at Insert

        Insert a table record with field documentation.

        One log entry per field of the inserted table entry.


-   **[Authorization Checks](Authorization_Checks_40294a1.md "")**  

-   **[Managing Change Document Objects](Managing_Change_Document_Objects_0d84bb3.md "")**  

-   **[Writing Change Documents](Writing_Change_Documents_bf7a980.md "")**  

-   **[Reading Change Documents](Reading_Change_Documents_c34f02d.md "")**  

-   **[How to Use the Fiori Reuse Library for Change Document Solution](How_to_Use_the_Fiori_Reuse_Library_for_Change_Document_Solution_9cea375.md "You can use the Reuse Library to implement a reusable component
		that can display change documents.")**  
You can use the *Reuse Library* to implement a reusable component that can display change documents.

