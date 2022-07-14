<!-- loiodd2e141e959f47e4893be7430b549af0 -->

# OData Request: System Query Option $select

You want to execute an OData request using the system query option $select within the Client Proxy.



<a name="loiodd2e141e959f47e4893be7430b549af0__section_v5g_vzv_5tb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

A data service URI with a $select System Query Option identifies the same set of entities as a URI without a $select query option; however, the presence of a $select query option specifies that a response from the data service should return a subset, as identified by the value of the $select query option, of the properties that would have been returned had the URI not included a $select query option.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

The $select system query option requests that the service return only the properties, dynamic properties, actions and functions explicitly requested by the client. The service returns the specified content, if available, along with any available expanded navigation or stream properties, and MAY return additional information.



<a name="loiodd2e141e959f47e4893be7430b549af0__section_vxd_w1w_5tb"/>

## Example Requests



### V4

Get the employee with Id ‘0002’ of entity set “Employees” and return only properties “Name” and “Age”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0002')?$select=Name,Age
```



### V2

Get all entities of entity set “Managers” and return only properties “Name” and “Age”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Managers?$select=Name,Age
```



<a name="loiodd2e141e959f47e4893be7430b549af0__section_wwg_kbw_5tb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present general examples on how to use $select.

Starting point for a request with $select is a read request, either on an or an entity list. Kindly check e.g. the chapter about reading an entity \(list\) on how to create an entity \(list\) read request instance. On the entity \(list\) read request, it is possible to set the selected properties.



### Example

You want to get the properties “Age”, “Name” and “Cityname” of the employee with Id ‘0002’ of entity set “Employees”. “Cityname” is located in the complex property “City”, which itself is part of the complex property “Location”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0002')?$select=Name,Age, Location/City/Cityname
```



### Step-by-step

**Step 1:** Set the properties to be selected at the read request instance. “AGE”, “LOCATION”, “CITY”, “CITYNAME” and “NAME” are the **internal** names of the properties “Age”, “Location”, “City”, “Cityname” and “Name”.

```


DATA: lo_read_request TYPE REF TO /iwbep/if_cp_request_read.

	  lo_read_request->set_select_properties( VALUE #( ( CONV #('AGE’) )

											 ( CONV #('LOCATION-CITY-CITYNAME') )

										     ( CONV #('NAME’) ) ) ).

```

> ### Note:  
> See the chapter about reading an entity for further details about how to create a read request instance.

