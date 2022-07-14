<!-- loio7112a7d4e84649318334b97e0b7f9041 -->

# OData Request: Read Optional Entity

You want to execute an OData request to read an optional entity using the Client Proxy. An optional entity is an entity accessed via navigation with cardinality \(i.e. the measure of the number of elements in a set\) zero-to-one \(i.e. the accessed entity has either zero or one entries\).



<a name="loio7112a7d4e84649318334b97e0b7f9041__section_e3p_qsf_ttb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

Entities are instances of Entity Types \(for example, Customer or Employee\) which are richly structured records with a key. The structure of an Entity Type is provided by its Properties. An entity key is formed from a subset of the properties of the Entity Type. The key \(for example, CustomerId or EmployeeId\) is a fundamental concept to uniquely identify and persist entity instances and to allow entity instances to participate in relationships or associations. Entities are grouped in Entity Sets; for example, the EntitySet Customers is a set of Customer instances.

A RetrieveEntity Request is used by a client to retrieve an AtomPub Entry Resource, as specified in [RFC5023](https://www.rfc-editor.org/rfc/rfc5023.txt), and potentially related entities that map to EntityType instances \(…\)



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Entities are instances of entity types \(e.g. Customer, Employee, etc.\). Entity types are named structured types with a key. They define the named properties and relationships of an entity. Entity types may derive by single inheritance from other entity types. The key of an entity type is formed from a subset of the primitive properties \(e.g. CustomerId, OrderId, LineId, etc.\) of the entity type.

OData services support requests for data via HTTP GET requests. The path of the URL specifies the target of the request \(for example; the collection of entities, entity, navigation property, structural property, or operation\).



<a name="loio7112a7d4e84649318334b97e0b7f9041__section_hhf_4tf_ttb"/>

## Example Requests



### V4

Get the manager of the Employee with Id ‘0004’ via zero-to-one navigation property ‘Employee2Manager’:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0004')/Employee2Manager
```



### V2

Get the technical info of the Team ‘TEAM\_02’ via zero-to-one navigation property “Technical\_Info”

```
GET/sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Teams('TEAM_02')/Technical_Info
```



<a name="loio7112a7d4e84649318334b97e0b7f9041__section_wh3_ztf_ttb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present general examples on how to read an optional entity.

Starting point for a READ request on an optional entity is an optional entity resource, which can be created via a corresponding zero-to-one navigation. Kindly check the chapter about navigations for further details. On the optional entity resource, it is possible to create an optional read request instance.

Executing the zero-to-one read request finally provides the zero-to-one read response, which can return the business data of the optional READ entity request.



### Example

You want to get the manager of the Employee with Id ‘0004’ via zero-to-one navigation property ‘Employee2Manager’:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0004')/Employee2Manager
```



### Step-by-step

```

  DATA: lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity01,
        lo_read_request    TYPE REF TO /iwbep/if_cp_request_read_01,
        lo_read_response   TYPE REF TO /iwbep/if_cp_response_read_01,
        lt_manager         TYPE STANDARD TABLE OF /iwbep/s_v4_tea_manager.

  lo_read_request = lo_entity_resource->create_request_for_read( ).
  lo_read_response = lo_read_request->execute( ).
  lo_read_response->get_business_data( IMPORTING et_business_data = lt_manager ).
```

**Step 1:** Create the read request instance via the entity resource instance:

```

  DATA: lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity01,
        lo_read_request    TYPE REF TO /iwbep/if_cp_request_read_01.

  lo_read_request = lo_entity_resource->create_request_for_read( ).

```

> ### Note:  
> See the chapter about navigation for further details about how to create an optional entity resource instance.

> ### Note:  
> Instead of a READ request, it would also be possible to set up an UPDATE or DELETE request for the optional entity; however, since these requests do not differ from “normal” UPDATE and DELETE requests, we do not describe this topic further. Kindly refer to the corresponding chapters for more details about handling UPDATE and DELETE requests on entities.

**Step 2:** Execute the read request and fetch the corresponding read response instance:

```

  DATA: lo_read_request  TYPE REF TO /iwbep/if_cp_request_read_01,
        lo_read_response TYPE REF TO /iwbep/if_cp_response_read_01.

  lo_read_response = lo_read_request->execute( ).
```

**Step 3:** Retrieve the business data from the read response instance:

```

  DATA: lo_read_response TYPE REF TO /iwbep/if_cp_response_read_01,
        lt_manager       TYPE STANDARD TABLE OF /iwbep/s_v4_tea_manager.

  lo_read_response->get_business_data( IMPORTING et_business_data = lt_manager ).

```

> ### Note:  
> The response of a zero-to-one read request is always a table containing either zero or one entries.

