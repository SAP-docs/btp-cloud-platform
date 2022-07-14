<!-- loiob810028e2fba48ea918c67f88fca18d9 -->

# OData Request: Read Entity List

You want to execute an OData request to read an entity list \(a.k.a. an entity collection\) using the Client Proxy.



<a name="loiob810028e2fba48ea918c67f88fca18d9__section_mcy_14f_ttb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

Entities are instances of Entity Types \(for example, Customer or Employee\) which are richly structured records with a key. The structure of an Entity Type is provided by its Properties. An entity key is formed from a subset of the properties of the Entity Type. The key \(for example, CustomerId or EmployeeId\) is a fundamental concept to uniquely identify and persist entity instances and to allow entity instances to participate in relationships or associations. Entities are grouped in Entity Sets; for example, the EntitySet Customers is a set of Customer instances.

A RetrieveEntitySet Request is used by a client to retrieve the entries in an AtomPub Collection, as specified in [RFC5023](https://www.rfc-editor.org/rfc/rfc5023.txt), that maps to an EntitySet in the abstract data model \(…\).



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Entity sets are named collections of entities \(e.g. Customers is an entity set containing Customer entities\). An entity's key uniquely identifies the entity within an entity set. If multiple entity sets use the same entity type, the same combination of key values can appear in more than one entity set and identifies different entities, one per entity set where this key combination appears. Each of these entities has a different entity-id. Entity sets provide entry points into the data model.

OData services support requests for data via HTTP GET requests. The path of the URL specifies the target of the request \(for example; the collection of entities, entity, navigation property, structural property, or operation\).



<a name="loiob810028e2fba48ea918c67f88fca18d9__section_ykt_q4f_ttb"/>

## Example Requests



### V4

Get all entities of entity set “Employees”

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees
```



### V2

Get all entities of entity set “Employees”

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees
```



<a name="loiob810028e2fba48ea918c67f88fca18d9__section_xbr_xpf_ttb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present one general example on how to create a READ request on an entity list.

Starting point for a GET request on an entity list is the Client Proxy instance. There, it is possible to create an entity list resource, which can then be used to create a read list request.

Executing the read list request finally provides the read list response, which can return the business data of the READ entity list request.



### Example

You want to fetch all entities of the V4 entity set ‘Employees’:

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



### Step-by-step

**Step 1:** Creation of the entity list resource for entity set ‘Employees’ \(with **internal** name ‘EMPLOYEES’\):

```

  DATA: lo_client_proxy         TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

  lo_entity_list_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES' ).

```

**Step 2:** Now you create the read list request instance. This is done on the entity resource:

```

  DATA: lo_read_list_request    TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_entity_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

  lo_read_list_request = lo_entity_list_resource->create_request_for_read( ).

```

**Step 3:** You execute the read list request and gain the read list response instance:

```

  DATA: lo_read_list_request  TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst.

  lo_read_list_response = lo_read_list_request->execute( ).
```



### **Step 4:** You fetch the business data from the response object:

```

  DATA: lo_read_list_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lt_employee           TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee.

  lo_read_list_response->get_business_data( IMPORTING et_business_data = lt_employee ).
```

> ### Note:  
> When using the V4 local client proxy, the business data received from the \(local consumption\) response will not be re-converted for outbound processing.

