<!-- loio02bfcdec55be4365ae8484edbf615879 -->

# Generation

XCO Generation is the part of the XCO library that allows the programmatic creation, update and deletion of ABAP repository objects. It consists of high-level and strongly typed APIs for the following objects types:

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


The following kinds of operations are supported:

-   POST Create the object according to a provided specification

-   PUT Create or update the object according to a provided specification

-   PATCH Update the object according to a provided specification

-   DELETE Delete the object


The matrix below shows which kinds of operations are supported for which object types:

<a name="loio02bfcdec55be4365ae8484edbf615879__table_yyp_csn_gpb"/>


<table>
<tr>
<th>

 



</th>
<th>

PUT



</th>
<th>

POST



</th>
<th>

PATCH



</th>
<th>

DELETE



</th>
</tr>
<tr>
<td>

BDEF



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

CLAS



</td>
<td>

X



</td>
<td>

 



</td>
<td>

X



</td>
<td>

X



</td>
</tr>
<tr>
<td>

DCLS



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

DDLS



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

DDLX



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

DEVC



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

DOMA



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

DTEL



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

FUGR



</td>
<td>

 



</td>
<td>

X



</td>
<td>

X



</td>
<td>

X



</td>
</tr>
<tr>
<td>

INTF



</td>
<td>

X



</td>
<td>

 



</td>
<td>

X



</td>
<td>

X



</td>
</tr>
<tr>
<td>

MSAG



</td>
<td>

X



</td>
<td>

 



</td>
<td>

X



</td>
<td>

X



</td>
</tr>
<tr>
<td>

SRVB



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

SRVD



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

TABL



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
<tr>
<td>

TTYP



</td>
<td>

X



</td>
<td>

 



</td>
<td>

 



</td>
<td>

X



</td>
</tr>
</table>

-   **[Design of the XCO Generation APIs](Design_of_the_XCO_Generation_APIs_d01859f.md "")**  


