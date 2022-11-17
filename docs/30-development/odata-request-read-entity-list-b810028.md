<!-- loiob810028e2fba48ea918c67f88fca18d9 -->

# OData Request: Read Entity List

Create an OData request to read an entity list \(entity collection\) in the Client Proxy instance.



<a name="loiob810028e2fba48ea918c67f88fca18d9__section_mcy_14f_ttb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

A ***RetrieveEntitySet*** Request is used by a client to update the entries in an AtomPub Collection, as specified in [RFC5023](https://www.rfc-editor.org/rfc/rfc5023.txt), that maps to an ***EntitySet*** in the abstract data model.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

OData services support data requests for using HTTP GET requests. The URL path specifies the target of the request \(for example, the collection of entities, entity, navigation property, structural property, or operation\).



<a name="loiob810028e2fba48ea918c67f88fca18d9__section_ykt_q4f_ttb"/>

## Example Requests



### Version 4

Get all entities of entity set “***Employees***”

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees
```



### Version 2

Get all entities of entity set “***Employees***”

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees
```



<a name="loiob810028e2fba48ea918c67f88fca18d9__section_xbr_xpf_ttb"/>

## Read Entity List Request



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to create a ***READ*** request on an entity list.

The starting point for a ***GET*** entity request is the [Client Proxy Examples](client-proxy-examples-7984f71.md). You can create a ***read list request*** based on an ***entity list resource***.

Running the ***read list request*** provides the read list response that can provide the business data of the READ entity list request.



### Example

Fetch all entities of the Version 4 entity set ‘***Employees***':

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees
```

```

  DATA: lo_client_proxy         TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_read_list_request    TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_list_response   TYPE REF TO /iwbep/if_cp_response_read_lst,
        lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list,
        lt_employee             TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee.


  lo_entity_list_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES' ).
  lo_read_list_request = lo_entity_list_resource->create_request_for_read( ).
  lo_read_list_response = lo_read_list_request->execute( ).
  lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).
```



### Steps

**Step 1:** Create the entity list resource for entity set ‘***Employees***’ \(with **internal** name ‘***EMPLOYEES***’\):

```

  DATA: lo_client_proxy         TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

  lo_entity_list_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES' ).

```

**Step 2:** Create the read list request instance on the entity resource:

```

  DATA: lo_read_list_request    TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

  lo_read_list_request = lo_entity_list_resource->create_request_for_read( ).

```

**Step 3:** Run the read list request and get the read list response instance:

```

  DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  lo_read_list_response = lo_read_list_request->execute( ).
```



### **Step 4:** Fetch the business data from the response object:

```

  DATA: lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lt_employee           TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee.

  lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).
```

> ### Note:  
> When you're using the Version 4 local client proxy, the business data you receive from the local consumption response isn't converted again for outbound processing.

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

