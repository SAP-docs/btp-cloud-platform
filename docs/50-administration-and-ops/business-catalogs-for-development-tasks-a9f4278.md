<!-- loioa9f42789fd5743edbf1de20d6c571cb2 -->

# Business Catalogs for Development Tasks

Get an overview of available business catalogs for development tasks and their restrictions.



You assign business catalogs to business roles that are assigned to business users. Business catalogs contain authorizations that define what a business user with a certain business role is allowed to do.

Certain business catalogs are only available in development systems (see [Creating an ABAP System](../20-getting-started/creating-an-abap-system-50b32f1.md)).

**Business Catalogs for Development Tasks**


<table>
<tr>
<th valign="top">

Business Catalog



</th>
<th valign="top">

Authorizations



</th>
<th valign="top">

Restrictions



</th>
</tr>
<tr>
<td valign="top">

*Development - ABAP Development Tools*

SAP\_A4C\_BC\_DEV\_PC



</td>
<td valign="top">

ADT Development



</td>
<td valign="top">

No transport request management \(transport tasks only\)

Available only in development systems


</td>
</tr>
<tr>
<td valign="top">

*Development - Analysis and Support*

SAP\_A4C\_BC\_DEV\_SUP\_PC



</td>
<td valign="top">

Troubleshooting tools such as logs, traces, and the debugger.

> ### Note:  
> To enable debugging authorization, set the access category Write, Read, Value Help to *Unrestricted*. Upon creation of the business role, the value is set by default to *No Access*. See [How to Define Authorizations Based on Restrictions](how-to-define-authorizations-based-on-restrictions-c926d69.md).



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

*Development - API Test*

SAP\_A4C\_BC\_DEV\_TST\_PC



</td>
<td valign="top">

Testing ABAP-based APIs released by SAP

</td>
<td valign="top">

Available only in development systems



</td>
</tr>
<tr>
<td valign="top">

*Development - Class Runner Execution*

SAP\_A4C\_BC\_DEV\_CLA\_RUN\_PC



</td>
<td valign="top">

Executing class runners in ABAP Development Tools



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

*Development - Data Preview - Released Objects*

SAP\_A4C\_BC\_DEV\_DAT\_PRV\_PC



</td>
<td valign="top">

Using data preview in ABAP Development Tools



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

*Development - Development Objects Display*

SAP\_A4C\_BC\_DEV\_OBJ\_DIS\_PC



</td>
<td valign="top">

Viewing \(read-only\) development objects in ABAP Development Tools



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

*Development - Transport Management*

SAP\_A4C\_BC\_TRN\_MNG\_PC



</td>
<td valign="top">

ADT Transport Management



</td>
<td valign="top">

No release of transport requests and no customizing requests

Available only in development systems

</td>
</tr>
<tr>
<td valign="top">

*Development - Transport Release Management*

SAP\_A4C\_BC\_TRN\_REL\_PC



</td>
<td valign="top">

ADT Transport Release Management



</td>
<td valign="top">

No customizing requests

Available only in development systems


</td>
</tr>
<tr>
<td valign="top">

*Development - UI Deployment*

SAP\_A4C\_BC\_DEV\_UID\_PC

</td>
<td valign="top">

Deployment of UIs into the ABAP system repository



</td>
<td valign="top">

Available only in development systems



</td>
</tr>
<tr>
<td valign="top">

*Development Support - Data Preview - Business Data*

SAP\_A4C\_BC\_DAT\_PRV\_DFT\_PC



</td>
<td valign="top">

Usage of the data preview in ABAP Development Tools for objects that are considered to contain business data:

-   CDS views in language version 5
-   Client-dependent tables in language version 5 with delivery class A and L

Data of CDS views can be viewed with or without application of the DCL.



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

*Development Support - Data Preview - Cross-Client and Customizing Data*

SAP\_A4C\_BC\_DAT\_PRV\_RDO\_PC



</td>
<td valign="top">

Usage of the data preview in ABAP Development Tools for objects that are considered to contain customizing and cross-client data:

-   Client-independent tables in language version 5 with delivery class A and L
-   Tables in language version 5 with delivery class S, E, and W \(metadata\)
-   Tables in language version 5 with delivery class C and G \(customizing\)



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

*Extensibility - Custom Apps and Services*

SAP\_CORE\_BC\_EXT\_TST


</td>
<td valign="top">

-   Previewing UIs in SAP Business Application Studio and Microsoft Visual Studio Code
-   Previewing service bindings
-   Testing custom apps and custom services



</td>
<td valign="top">

Only services that have their original in the current system
  
Available only in development systems


</td>
</tr>
</table>

