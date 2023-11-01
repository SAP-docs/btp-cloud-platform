<!-- loioe3251557f960469d9b9282bf18fb94d4 -->

# Classes and Interfaces of the Design Time API

You can use the `CL_BALI_OBJECT_HANDLER` class as *Application Log Design Time API* to create, change, read, or delete application log objects or subobjects. It uses the public interface `IF_BALI_OBJECT_HANDLER`.

**Public Methods**

**GET\_INSTANCE \(static\)**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

RO\_OBJ\_HANDLER

</td>
<td valign="top">

Returning

</td>
<td valign="top">

Create, change or delete application log objects

</td>
</tr>
</table>

Create a new application log object, optionally with subobjects.

**IF\_BALI\_OBJECT\_HANDLER~CREATE\_OBJECT**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

IV\_OBJECT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

New application log object

</td>
</tr>
<tr>
<td valign="top">

IV\_OBJECT\_TEXT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Description for new application log object

</td>
</tr>
<tr>
<td valign="top">

IT\_SUBOBJECTS

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Table of new application log subobjects

</td>
</tr>
<tr>
<td valign="top">

IV\_PACKAGE

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Package

</td>
</tr>
<tr>
<td valign="top">

IV\_TRANSPORT\_REQUEST

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Transport request

</td>
</tr>
</table>

> ### Note:  
> The input of a table of subobjects for parameter `IT_SUBOBJECTS` is optional. If parameters `IV_PACKAGE` and `IV_TRANSPORT_REQUEST` are not provided, it is assumed that a local object shall be created.

Delete an application log object and all of its subobjects.

**IF\_BALI\_OBJECT\_HANDLER~DELETE\_OBJECT**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

IV\_OBJECT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Application log object

</td>
</tr>
<tr>
<td valign="top">

IV\_TRANSPORT\_REQUEST

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Transport request

</td>
</tr>
</table>

Add a new subobject to an existing application log object.

**IF\_BALI\_OBJECT\_HANDLER~ADD\_SUBOBJECT**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

IV\_OBJECT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Application log object

</td>
</tr>
<tr>
<td valign="top">

IV\_SUBOBJECT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

New application log subobject

</td>
</tr>
<tr>
<td valign="top">

IV\_SUBOBJECT\_TEXT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Description for new application log subobject

</td>
</tr>
<tr>
<td valign="top">

IV\_TRANSPORT\_REQUEST

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Transport request

</td>
</tr>
</table>

Delete a subobject from an application log object.

**IF\_BALI\_OBJECT\_HANDLER~DELETE\_SUBOBJECT**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

IV\_OBJECT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Application log object

</td>
</tr>
<tr>
<td valign="top">

IV\_SUBOBJECT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Application log subobject

</td>
</tr>
<tr>
<td valign="top">

IV\_TRANSPORT\_REQUEST

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Transport request

</td>
</tr>
</table>

Read an application log object and all of its subobjects

**IF\_BALI\_OBJECT\_HANDLER~READ\_OBJECT**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

IV\_OBJECT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Application log object

</td>
</tr>
<tr>
<td valign="top">

EV\_OBJECT\_TEXT

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Description for an application log object

</td>
</tr>
<tr>
<td valign="top">

ET\_SUBOBJECTS

</td>
<td valign="top">

Importing

</td>
<td valign="top">

Table of application log subobjects

</td>
</tr>
</table>

> ### Note:  
> For all methods, `IV_TRANSPORT_REQUEST` is not required for local objects.
> 
> All methods of `IF_BALI_OBJECT_HANDLER` include exception `CX_BALI_OBJECTS`.

