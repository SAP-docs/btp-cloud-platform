<!-- loiodd5259cde2a24f1d808a71e8fd46be82 -->

# $orderby Option

Use the $orderby system query option to determine what values are used to order the entities in the EntitySet.



<a name="loiodd5259cde2a24f1d808a71e8fd46be82__section_iwz_mz2_ttb"/>

## OData Specification



### OData Version 2

See [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

A data service URI with the `$orderby` System Query Option specifies an expression for determining what values are used to order the entities in the EntitySet \(identified by the Resource Path section of the URI\).



### OData Version 4

See [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

The `$orderby` System Query option specifies the order that items are returned from the service. The value of the `$orderby` System Query option is a comma-separated list of expressions that use the primitive result values to sort the items. The expression can include the suffix `asc` for ascending or `desc` for descending that you separate from the property name by one or more spaces.



<a name="loiodd5259cde2a24f1d808a71e8fd46be82__section_nn3_d1f_ttb"/>

## Example Requests



### Version 4

Get all entities of entity set “`Employees`” and sort the response descending to property “`Cityname`” and ascending to property “`Age`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees?$orderby=Location/City/Cityname desc, Age
```



### Version 2

Get all entities of entity set “`Employees`” and sort the response ascending to property “`Id`” and descending to property “`Name`”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees?$orderby=Id, Name asc
```



<a name="loiodd5259cde2a24f1d808a71e8fd46be82__section_avf_m1f_ttb"/>

## $orderby System Query Option



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to use the `$orderby` option.

The starting point for a request with the `$orderby` option is an entity list read request. You can set the `$orderby` on the entity list read request.



### Example

Get all entities of entity set “`Employees`” and sort the response descending to property “`Cityname`” \(in complex property “`City`”, which is part of complex property “`Location`”\) and ascending to property “`Age`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees?$orderby=Location/City/Cityname desc, Age
```



### Steps

**Step 1:** Set the `$orderby` values at the request instance:


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
</table>

```

 DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.
       lo_read_list_request-> set_orderby( value #(( property_path = ‘LOCATION-CITY-CITYNAME’ 
													 descending = abap_true )
                                                   ( property_path = ‘AGE’                    
													 descending = abap_false ) ) ).

```

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Read Entity](odata-request-read-entity-9d7dde4.md "To create an OData request to read an entity in the Client Proxy instance.")

[OData Request: Read Entity List](odata-request-read-entity-list-b810028.md "Create an OData request to read an entity list (entity collection) in the Client Proxy instance.")

