<!-- loio9d7dde4d63784eb898a02efd3ee486a6 -->

# OData Request: Read Entity

To create an OData request to read an entity in the Client Proxy instance.



<a name="loio9d7dde4d63784eb898a02efd3ee486a6__section_cz3_f3f_ttb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

A client uses a RetrieveEntity request to retrieve an AtomPub Entry Resource. See [RFC5023: Atom Publishing Protocol](https://www.rfc-editor.org/rfc/rfc5023.txt) for more information on the Atom Publishing Protocol.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

OData services support requests for data using HTTP GET requests. The URL path includes the request target \(for example, the collection of entities, entity, navigation property, structural property, or operation\).



<a name="loio9d7dde4d63784eb898a02efd3ee486a6__section_py3_v3f_ttb"/>

## Example Requests



### Version 4

Get the employee with id ‘***007***' from the “***Employees***” entity set.

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘007’)
```



### Version 2

Get the employee with id ‘***007***’ from the “***Employees***” entity set.

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees(‘007’)
```



<a name="loio9d7dde4d63784eb898a02efd3ee486a6__section_yh5_fjf_ttb"/>

## OData Request: Read Entity



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to create a ***READ*** request on an entity.

The starting point for a ***GET*** entity request is the Client Proxy instance. You can create an entity resource based on an entity list resource, which can use create an entity resource based on an entity list resource. Use the entity resource to create a read request.

Running the read request provides a response, which can return the business data of the ***READ*** entity request.



### Example

From the Version 4 entity set ‘***Employees’***, fetch the employee with key id ‘***007’***:

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



### Steps

To run an OData request to read an entity:

**Step 1:** Create the entity resource for the employee with the key ***Id***=‘***007***' from the entity set ‘Employees’ \(with **internal** name ‘***EMPLOYEES’***\). Use type ***ty\_s\_employee\_key*** in interface ***/iwbep/if\_v4\_tea\_busi\_types*** that includes the key property ***id***:

```

  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key( VALUE /iwbep/if_v4_tea_busi_types=>ty_s_employee_key( id = ‘007’) ).
```

**Step 2:** Create the read request instance on the entity resource:

```

  DATA: lo_read_request    TYPE REF TO /iwbep/if_cp_request_read,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_read_request = lo_entity_resource->create_request( ).
```

**Step 3:** Execute the read request and get the read response instance:

```

  DATA: lo_read_request  TYPE REF TO /iwbep/if_cp_request_read,
        lo_read_response TYPE REF TO /iwbep/if_cp_response_read.

  lo_read_response = lo_read_request->execute( ).
```

**Step 4:** Fetch the business data from the response object:

```

  DATA: lo_read_response TYPE REF TO /iwbep/if_cp_response_read,
        ls_employee      TYPE /iwbep/s_v4_tea_employee.

  lo_read_response->get_business_data( IMPORTING es_business_data = ls_employee ).

```

> ### Note:  
> When you're using the Version 4 local client proxy, the business data you receive from the local consumption response isn't converted again for outbound processing.

**Related Information**  




