<!-- loiodd2e141e959f47e4893be7430b549af0 -->

# $select Option

Use the $select system query option to return a subset for the returned properties of the URI without a $select query option.



<a name="loiodd2e141e959f47e4893be7430b549af0__section_v5g_vzv_5tb"/>

## OData Specification



### OData Version 2

See [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

A data service URI **with** a `$select` System Query Option identifies the same set of entities as a URI **without** a `$select` query option. If you have a `$select` query option, the data service response returns a subset \(identified by the `$select` query option\) for the returned properties of the URI that didn't include a `$select` query option.



### OData Version 4

See [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

The `$select` system query option requests that the service return only the properties, dynamic properties, actions, and functions explicitly requested by the client. The service returns the specified content \(if available\) and any available expanded navigation or stream properties. It can also return additional information.



<a name="loiodd2e141e959f47e4893be7430b549af0__section_vxd_w1w_5tb"/>

## Example Requests



### Version 4

Get the employee with Id ‘`0002`’ of entity set “`Employees`” and return only properties “`Name`” and “`Age`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0002')?$select=Name,Age
```



### Version 2

Get all entities of entity set “`Managers`” and return only properties “`Name`” and “`Age`”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Managers?$select=Name,Age
```



<a name="loiodd2e141e959f47e4893be7430b549af0__section_wwg_kbw_5tb"/>

## $select System Query Option



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to use the `$select` option.

The starting point for a request with `$select` is a read request on an entity list. You can set the selected properties on the entity list read request.



### Example

Set the properties “`Age`”, “`Name`” and “`Cityname`” for the employee with Id ‘`0002`’ for the entity set “`Employees`”. “`Cityname`” is in the complex property “`City`”, which is of the complex property “`Location`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0002')?$select=Name,Age,Location/City/Cityname
```



### Steps

**Step 1:** Set the properties you want to select at the read request instance:


<table>
<tr>
<th valign="top">

Properties

</th>
<th valign="top">

Internal Names

</th>
</tr>
<tr>
<td valign="top">

Age

</td>
<td valign="top">

`AGE`

</td>
</tr>
<tr>
<td valign="top">

Location

</td>
<td valign="top">

`LOCATION`

</td>
</tr>
<tr>
<td valign="top">

City

</td>
<td valign="top">

`CITY`

</td>
</tr>
<tr>
<td valign="top">

Cityname

</td>
<td valign="top">

`CITYNAME`

</td>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

`NAME`

</td>
</tr>
</table>

```


DATA: lo_read_request TYPE REF TO /iwbep/if_cp_request_read.

	  lo_read_request->set_select_properties( VALUE #( ( CONV #('AGE’) )

											 ( CONV #('LOCATION-CITY-CITYNAME') )

										     ( CONV #('NAME’) ) ) ).

```

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Create Entity](odata-request-create-entity-56be82d.md "Create an entity in the Client Proxy instance with insert entity request.")

[OData Request: Read Entity](odata-request-read-entity-9d7dde4.md "To create an OData request to read an entity in the Client Proxy instance.")

