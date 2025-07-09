<!-- loioeb7320841d1c40bfa2bc8e6bdc02d6bb -->

# $count Option

Use the $count or $inlinecount system query option to indicate a certain number or total count of entities in the EntitySet.



<a name="loioeb7320841d1c40bfa2bc8e6bdc02d6bb__section_jd5_vrh_ptb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

`$inlinecount`: For a value of "`allpages`", the `$inlinecount` option indicates the response to the request must include the number of entities count in the EntitySet. The number of entities count is identified by the Resource Path section of the URI after all `$filter` System Query Options are applied.

If the value is "`none`", this option indicates the response to the request MUST NOT include the count value.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

The `$count` system query option with a value of `true` specifies that the total item count in a collection that matches the request is returned with the result.

The `$count` system query option ignores `$top`, `$skip`, or `$expand` query options, and returns the total results count across all pages \(including only the results that match any specified `$filter` and `$search`\). The count returned inline might not equal the actual number of items returned. This happens due to latency between calculating the count and enumerating the last value or due to inexact calculations on the service.



<a name="loioeb7320841d1c40bfa2bc8e6bdc02d6bb__section_pqh_wsh_ptb"/>

## Example Requests



### Version 4

Get the number of entities in entity set “`TEAMS`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/TEAMS/$count
```

Get all Equipment entities associated with "`Employee 1`" and the total count of associated items:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES('1')/EMPLOYEE_2_EQUIPMENTS?$count=true
```



### Version 2

Get the number of entities in entity set “`EquipmentSet`”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/EquipmentSet/$count
```

Get all Team Member entities associated with Team “`TEAM_01`” and the total count of associated members:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Teams('TEAM_01')/Team_Members?$inlinecount=allpages
```



<a name="loioeb7320841d1c40bfa2bc8e6bdc02d6bb__section_tjq_pvh_ptb"/>

## $count System Query Option



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to use the `$count` option.

The starting point for a request with the `$count` option is an entity list read request. You can set the `$count` on the entity list read request.

You can fetch the `$count` result from the entity list read response instance.

> ### Note:  
> The actual “flavor” of the `$count` that the Client Proxy sets depends on the request type:
> 
> -   `$count` if no business data is requested.
> 
> -   `$count=true` for OData Version 4 requests if business data is requested.
> 
> -   `$inlinecount=allpages` for OData Version 2 if business data is requested.



### Example 1

Get the number of entities in entity set “`TEAMS`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/TEAMS/$count
```



### Steps

```

  DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lv_count              TYPE REF TO int8.

  lo_read_list_request-> request_no_business_data( ).
  lo_read_list_request->request_count( ).
  lo_read_list_response = lo_read_list_request->execute( ).
  lv_count = lo_read_list_response->get_count( ).
```

**Step 1:** Set the request to NOT fetch the entity list \(for example, `request_no_business_data`\):

```

  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request-> request_no_business_data( ).
```

**Step 2:** Request the `$count` at the request instance:

```


  DATA: lo_read_list_request TYPE REF TO /iwbep/if_cp_request_read_list.

  lo_read_list_request->request_count( ).
```

**Step 3:** Run the request and fetch the count value from the read list response instance:

```

  DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lv_count              TYPE REF TO int8.

  lo_read_list_response = lo_read_list_request->execute( ).
  lv_count = lo_read_list_response->get_count( ).
```



### Example 2

Get all `Equipment` entities associated with "`Employee 1`" and the total count of associated items:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES('1')/EMPLOYEE_2_EQUIPMENTS?$count=true
```



### Steps

```

 DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,
       lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
       lv_count              TYPE REF TO int8.

  lo_read_list_request->request_count( ).
  lo_read_list_response = lo_read_list_request->execute( ).
  lv_count = lo_read_list_response->get_count( ).
```

> ### Note:  
> The steps for this example are identical to the first example, except that you do **NOT** request to not return any business data \(you skip step 1 in the first example\).
> 
> See example one for a the steps.

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Read Entity](odata-request-read-entity-9d7dde4.md "To create an OData request to read an entity in the Client Proxy instance.")

[OData Request: Read Entity List](odata-request-read-entity-list-b810028.md "Create an OData request to read an entity list (entity collection) in the Client Proxy instance.")

