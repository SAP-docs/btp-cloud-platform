<!-- loiodd5259cde2a24f1d808a71e8fd46be82 -->

# OData Request: System Query Option $orderby

You want to execute an OData request using the system query option $orderby within the Client Proxy.



<a name="loiodd5259cde2a24f1d808a71e8fd46be82__section_iwz_mz2_ttb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

A data service URI with a $orderby System Query Option specifies an expression for determining what values are used to order the entities in the EntitySet, identified by the Resource Path section of the URI.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

The $orderby System Query option specifies the order in which items are returned from the service. The value of the $orderby System Query option contains a comma-separated list of expressions whose primitive result values are used to sort the items. \(…\) The expression can include the suffix asc for ascending or desc for descending, separated from the property name by one or more spaces. \(…\)



<a name="loiodd5259cde2a24f1d808a71e8fd46be82__section_nn3_d1f_ttb"/>

## Example Requests



### V4

Get all entities of entity set “Employees” and sort the response descending to property “Cityname” and ascending to property “Age”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees?$orderby=Location/City/Cityname desc, Age
```



### V2

Get all entities of entity set “Employees” and sort the response ascending to property “Id” and descending to property “Name”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees?$orderby=Id, Name asc
```



<a name="loiodd5259cde2a24f1d808a71e8fd46be82__section_avf_m1f_ttb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present general examples on how to use $orderby.

Starting point for a request with $orderby is an entity list read request. Kindly check e.g. the chapter about reading an entity list on how to create an entity list read request instance. On the entity list read request, it is possible to set the $orderby.



### Example

You want to get all entities of entity set “Employees” and sort the response descending to property “Cityname” \(located in complex property “City”, which itself is part of complex property “Location”\) and ascending to property “Age”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees?$orderby=Location/City/Cityname desc, Age
```



### Step-by-step

**Step 1:** Set the orderby values directly at the request instance. “AGE”, “LOCATION”, “CITY” and “CITYNAME” are the **internal** names of properties “Age”, “Location”, “City” and “Cityname”:

```

 DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.
       lo_read_list_request-> set_orderby( value #(( property_path = ‘LOCATION-CITY-CITYNAME’ 
													 descending = abap_true )
                                                   ( property_path = ‘AGE’                    
													 descending = abap_false ) ) ).

```

> ### Note:  
> See the chapter about reading an entity list for further details about how to create a read list request instance.

