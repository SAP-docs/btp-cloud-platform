<!-- loio02bfcdec55be4365ae8484edbf615879 -->

# Generation APIs

The XCO Generation APIs are the part of the XCO library that allows the programmatic creation, update and deletion of ABAP repository objects. It consists of high-level and strongly typed APIs for the following objects types:

-   BDEF \(Behavior Definitions\)

-   CLAS \(Classes\)

-   DCLS \(Access Controls\)

-   DDLS \(Data Definitions\)

-   DDLX \(Metadata Extensions\)

-   DEVC \(Packages\)

-   DOMA \(Domains\)

-   DRTY \(CDS Type Definitions\)

-   DTEL \(Data Elements\)

-   EVTB \(Event Bindings\)

-   FUGR \(Function Groups\)

-   INTF \(Interfaces\)

-   MSAG \(Message Classes\)

-   SRVB \(Service Bindings\)

-   SRVD \(Service Definitions\)

-   TABL \(Structures, Database Tables and Global Temporary Tables\)

-   TTYP \(Table Types\)

-   XSLT \(Transformations\)


The following kinds of operations are supported:

-   POST Create the object according to a provided specification

-   PUT Create or update the object according to a provided specification

-   PATCH Update the object according to a provided specification

-   DELETE Delete the object


The matrix below shows which kinds of operations are supported for which object types:

****


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

PUT



</th>
<th valign="top">

POST



</th>
<th valign="top">

PATCH



</th>
<th valign="top">

DELETE



</th>
</tr>
<tr>
<td valign="top">

BDEF



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

CLAS



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

DCLS



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

DDLS



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

DDLX



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

DEVC



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

DOMA



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

DRTY



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

DTEL



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

EVTB



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

FUGR



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
<td valign="top">

X



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

INTF



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

MSAG



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

SRVB



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

SRVD



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

TABL



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

TTYP



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
<tr>
<td valign="top">

XSLT



</td>
<td valign="top">

X



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

X



</td>
</tr>
</table>

