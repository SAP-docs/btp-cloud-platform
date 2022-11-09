<!-- loio02bfcdec55be4365ae8484edbf615879 -->

# Generation APIs

The XCO Generation APIs are the part of the XCO library that allows the programmatic creation, update and deletion of ABAP repository objects. It consists of high-level and strongly typed APIs for the following objects types:

-   BDEF \(Behavior definitions\)

-   CLAS \(Classes\)

-   DCLS \(Access controls\)

-   DDLS \(Data definitions\)

-   DDLX \(Metadata extensions\)

-   DEVC \(Packages\)

-   DOMA \(Domains\)

-   DTEL \(Data elements\)

-   FUGR \(Function groups\)

-   INTF \(Interfaces\)

-   MSAG \(Message classes\)

-   SRVB \(Service bindings\)

-   SRVD \(Service definitions\)

-   TABL \(Structures, database tables and global temporary tables\)

-   TTYP \(Table types\)

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

