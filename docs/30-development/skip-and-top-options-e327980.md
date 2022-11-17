<!-- loioe3279805db7e48c99b24b4e53fe9cec5 -->

# $skip and $top Options

Use the $skip or $top system query options to identify a subset of the entities in an entiy collection..



<a name="loioe3279805db7e48c99b24b4e53fe9cec5__section_j5h_j1d_vtb"/>

## OData Specification



### OData Version 2

See [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

A data service URI with:


<table>
<tr>
<th valign="top">

***$skip*** System Query Option



</th>
<th valign="top">

***$top*** System Query Option



</th>
</tr>
<tr>
<td valign="top">

identifies a subset of the entities in an entity collection \(identified by the Resource Path section of the URI\)



</td>
<td valign="top">

identifies a subset of the entities in an entity collection \(identified by the Resource Path section of the URI\)



</td>
</tr>
<tr>
<td valign="top">

the subset is defined by searching ***N*** entities in an collection and selecting **only the remaining entities** \(starting with entity ***N+1***\).



</td>
<td valign="top">

the subset is formed by selecting **only the first** ***N*** items of the set.



</td>
</tr>
<tr>
<td valign="top">

***N*** is a positive integer specified by this query option.



</td>
<td valign="top">

***N*** is a positive integer specified by this query option.



</td>
</tr>
</table>



### OData Version 4

See [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

A data service URI with:


<table>
<tr>
<th valign="top">

***$skip*** System Query Option



</th>
<th valign="top">

***$top*** System Query Option



</th>
</tr>
<tr>
<td valign="top">

specifies a non-negative integer ***n*** that **excludes** the first ***n*** items of the queried collection.



</td>
<td valign="top">

specifies a non-negative integer ***n*** that **limits** the number of items returned from a collection.



</td>
</tr>
<tr>
<td valign="top">

the service returns items starting at position ***n+1***.



</td>
<td valign="top">

the service returns the number of available items up to but not greater than the specified value ***n***.



</td>
</tr>
</table>



<a name="loioe3279805db7e48c99b24b4e53fe9cec5__section_k5h_j1d_vtb"/>

## Example Requests



### Version 4

Skip the first entity in entity set “***TEAMS***” and get the following two ones:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams?$skip=1&$top=2
```



### Version 2

Skip the first entity in entity set “Managers” and get the following two ones:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Managers?$skip=1&$top=2
```



<a name="loioe3279805db7e48c99b24b4e53fe9cec5__section_l5h_j1d_vtb"/>

## $skip and $top Query Options



### Overview

> ### Note:  

As the coding is independent of the OData version, we're presenting a general example on how to use the ***$count*** option.

The starting point for a request with ***$skip*** or ***$top*** option is an entity list read request. You can set both the ***$skip*** and the ***$top*** on the entity list read request.



### Example

Skip the first entity in entity set “***TEAMS***” and get these entities:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams?$skip=1&$top=2
```



### Steps

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

        lo_read_list_request->set_skip( 1 ).
        lo_read_list_request->set_top( 2 ).
```

**Step 1:** Set the ***$skip*** value at the request instance:

```

 DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

 lo_read_list_request->set_skip( 1 ).
```

**Step 2:** Set the ***$top*** value at the request instance:

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

        lo_read_list_request->set_top( 2 ).
```

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Create Entity](odata-request-create-entity-56be82d.md "Create an entity in the Client Proxy instance with insert entity request.")

[OData Request: Read Entity](odata-request-read-entity-9d7dde4.md "To create an OData request to read an entity in the Client Proxy instance.")

