<!-- loio9d7dde4d63784eb898a02efd3ee486a6 -->

# OData Request: Read Entity

You want to execute an OData request to read an entity using the Client Proxy.



<a name="loio9d7dde4d63784eb898a02efd3ee486a6__section_cz3_f3f_ttb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

Entities are instances of Entity Types \(for example, Customer or Employee\) which are richly structured records with a key. The structure of an Entity Type is provided by its Properties. An entity key is formed from a subset of the properties of the Entity Type. The key \(for example, CustomerId or EmployeeId\) is a fundamental concept to uniquely identify and persist entity instances and to allow entity instances to participate in relationships or associations. Entities are grouped in Entity Sets; for example, the EntitySet Customers is a set of Customer instances.

A RetrieveEntity Request is used by a client to retrieve an AtomPub Entry Resource, as specified in [RFC5023](https://www.rfc-editor.org/rfc/rfc5023.txt), and potentially related entities that map to EntityType instances \(…\)



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Entities are instances of entity types \(e.g. Customer, Employee, etc.\). Entity types are named structured types with a key. They define the named properties and relationships of an entity. Entity types may derive by single inheritance from other entity types. The key of an entity type is formed from a subset of the primitive properties \(e.g. CustomerId, OrderId, LineId, etc.\) of the entity type.

OData services support requests for data via HTTP GET requests. The path of the URL specifies the target of the request \(for example; the collection of entities, entity, navigation property, structural property, or operation\).



<a name="loio9d7dde4d63784eb898a02efd3ee486a6__section_py3_v3f_ttb"/>

## Example Requests



### V4

Get the employee with id ‘007’ of entity set “Employees”

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’)
```



### V2

Get the employee with id ‘007’ of entity set “Employees”

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees(‘007’)
```



<a name="loio9d7dde4d63784eb898a02efd3ee486a6__section_yh5_fjf_ttb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present one general example on how to create a READ request on an entity.

Starting point for a GET request on an entity is the Client Proxy instance. There, it is possible to create an entity resource based on an entity list resource, which can then be used to create a read request.

Executing the read request finally provides the read response, which can return the business data of the READ entity request.



### Example

You want to fetch the employee with key “id = ‘007’” of the V4 entity set ‘Employees’:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’)
```

```

  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_read_request    TYPE REF TO /iwbep/if_cp_request_read,
        lo_read_response   TYPE REF TO /iwbep/if_cp_response_read,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity,
        ls_employee        TYPE /iwbep/s_v4_tea_employee.


  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key( VALUE /iwbep/if_v4_tea_busi_types=>ty_s_employee_key( id = ‘007’) ).
  lo_read_request = lo_entity_resource->create_request( ).
  lo_read_response = lo_read_request->execute( ).
  lo_read_response->get_business_data( IMPORTING es_business_data = ls_employee ).
```



### Step-by-step

**Step 1:** Creation of the entity resource for the employee with the key “Id=‘007’” of entity set ‘Employees’ \(with **internal** name ‘EMPLOYEES’\). Type “ty\_s\_employee\_key” in interface /iwbep/if\_v4\_tea\_busi\_types” is a structure containing the key property “id”:

```

  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key( VALUE /iwbep/if_v4_tea_busi_types=>ty_s_employee_key( id = ‘007’) ).
```

**Step 2:** Now you create the read request instance. This is done on the entity resource:

```

  DATA: lo_read_request    TYPE REF TO /iwbep/if_cp_request_read,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_read_request = lo_entity_resource->create_request( ).
```

**Step 3:** You execute the read request and gain the read response instance:

```

  DATA: lo_read_request  TYPE REF TO /iwbep/if_cp_request_read,
        lo_read_response TYPE REF TO /iwbep/if_cp_response_read.

  lo_read_response = lo_read_request->execute( ).
```

**Step 4:** You fetch the business data from the response object:

```

  DATA: lo_read_response TYPE REF TO /iwbep/if_cp_response_read,
        ls_employee      TYPE /iwbep/s_v4_tea_employee.

  lo_read_response->get_business_data( IMPORTING es_business_data = ls_employee ).

```

> ### Note:  
> When using the V4 local client proxy, the business data received from the \(local consumption\) response will not be re-converted for outbound processing.

