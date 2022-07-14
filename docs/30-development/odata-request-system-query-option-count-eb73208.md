<!-- loioeb7320841d1c40bfa2bc8e6bdc02d6bb -->

# OData Request: System Query Option $count

You want to execute an OData request using the system query option $count or $inlinecount within the Client Proxy.



<a name="loioeb7320841d1c40bfa2bc8e6bdc02d6bb__section_jd5_vrh_ptb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

$inlinecount: For a value of "allpages", this option indicates that the response to the request MUST include the count of the number of entities in the EntitySet, identified by the Resource Path section of the URI after all $filter System Query Options have been applied.

For a value of "none", this option indicates that the response to the request MUST NOT include the count value.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

The $count system query option with a value of true specifies that the total count of items within a collection matching the request be returned along with the result. \(…\)

The $count system query option ignores any $top, $skip, or $expand query options, and returns the total count of results across all pages including only those results matching any specified $filter and $search. Clients should be aware that the count returned inline may not exactly equal the actual number of items returned, due to latency between calculating the count and enumerating the last value or due to inexact calculations on the service.



<a name="loioeb7320841d1c40bfa2bc8e6bdc02d6bb__section_pqh_wsh_ptb"/>

## Example Requests



### V4

Get the number of entities in entity set “TEAMS”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/TEAMS/$count
```

Get all Equipment entities associated with Employee 1 together with the total count of associated items:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES('1')/EMPLOYEE_2_EQUIPMENTS?$count=true
```



### V2

Get the number of entities in entity set “EquipmentSet”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/EquipmentSet/$count
```

Get all Team Member entities associated with Team “TEAM\_01” together with the total count of associated members:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Teams('TEAM_01')/Team_Members?$inlinecount=allpages
```



<a name="loioeb7320841d1c40bfa2bc8e6bdc02d6bb__section_tjq_pvh_ptb"/>

## How-to



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present general examples on how to use $count.

Starting point for a request with $count is an entity list read request. Kindly check e.g. the chapter about reading an entity list on how to create an entity list read request instance. On the entity list read request, it is possible to set the $count.

On the entity list read response instance, the $count result can be fetched. More details on how to create an entity list read response instance is given in the corresponding chapter about reading an entity list.

> ### Note:  
> The actual “flavor” of the $count that will be set by the Client Proxy depends on the underlying request kind:
> 
> -   $count if no business data is requested
> 
> -   $count=true for OData V4 requests if business data is requested
> 
> -   $inlinecount=allpages for OData V2 if business data is requested



### Example 1

You want to get the number of entities in entity set “TEAMS”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/TEAMS/$count
```



### Step-by-step

```

  DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lv_count              TYPE REF TO int8.

  lo_read_list_request-> request_no_business_data( ).
  lo_read_list_request->request_count( ).
  lo_read_list_response = lo_read_list_request->execute( ).
  lv_count = lo_read_list_response->get_count( ).
```

> ### Note:  
> See the chapter about reading an entity list for further details about how to create a read list request instance.

**Step 1:** Set the request to not fetch the entity list itself \(i.e. to not request business data\)

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request-> request_no_business_data( ).
```

**Step 2:** Now you request the $count at the request instance:

```


  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request->request_count( ).
```

**Step 3:** Execute the request and fetch the count value from the read list response instance:

```

  DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lv_count              TYPE REF TO int8.

  lo_read_list_response = lo_read_list_request->execute( ).
  lv_count = lo_read_list_response->get_count( ).
```



### Example 2

You want to get all Equipment entities associated with Employee 1 together with the total count of associated items:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES('1')/EMPLOYEE_2_EQUIPMENTS?$count=true
```



### Step-by-step

```

 DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,
       lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
       lv_count              TYPE REF TO int8.

  lo_read_list_request->request_count( ).
  lo_read_list_response = lo_read_list_request->execute( ).
  lv_count = lo_read_list_response->get_count( ).
```

> ### Note:  
> The steps are identical to the first example, except that you do **not** request to not return any business data \(i.e. you skip step 1 of the first example\).
> 
> See example one for a detailed description of the individual steps.

