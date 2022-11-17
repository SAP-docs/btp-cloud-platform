<!-- loio7112a7d4e84649318334b97e0b7f9041 -->

# OData Request: Read Optional Entity

Create an OData request to read an optional entity in the Client Proxy instance.

An optional entity is accessed using navigation with cardinality \(for example, the measure of the number of elements in a set\) zero-to-one \(for example, the accessed entity has either zero or one entry\).



<a name="loio7112a7d4e84649318334b97e0b7f9041__section_e3p_qsf_ttb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

The client uses a ***RetrieveEntity*** Request to retrieve an AtomPub Entry Resource, as specified in [RFC5023](https://www.rfc-editor.org/rfc/rfc5023.txt), and potentially related entities that map to EntityType instances.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

OData services support requests for data with HTTP GET requests. The URL path specifies thespecifies the target of the request \(for example, the collection of entities, entity, navigation property, structural property, or operation\).



<a name="loio7112a7d4e84649318334b97e0b7f9041__section_hhf_4tf_ttb"/>

## Example Requests



### Version 4

Get the manager of the Employee with Id ‘***0004***’ via zero-to-one navigation property ‘***Employee2Manager***’:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0004')/Employee2Manager
```



### Version 2

Get the technical info of the Team ‘***TEAM\_02***’ via zero-to-one navigation property “***Technical\_Info***”

```
GET/sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Teams('TEAM_02')/Technical_Info
```



<a name="loio7112a7d4e84649318334b97e0b7f9041__section_wh3_ztf_ttb"/>

## Read Optional Entity Request



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to read a an optional entity .

The starting point for a ***$read*** optional entity request is an optional entity in the Client Proxy instance. It's possible to create a ***$read*** request with a corresponding zero-to-one navigation.

On the optional entity resource, it's possible to create an optional read request instance.

Running the zero-to-one read request provides the zero-to-one read response, which can return the business data of the optional READ entity request.



### Example

Get the manager of the Employee with Id ‘***0004***’ via zero-to-one navigation property ‘***Employee2Manager***’:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0004')/Employee2Manager
```



### Steps

```

  DATA: lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity01,
        lo_read_request    TYPE REF TO /iwbep/if_cp_request_read_01,
        lo_read_response   TYPE REF TO /iwbep/if_cp_response_read_01,
        lt_manager         TYPE STANDARD TABLE OF /iwbep/s_v4_tea_manager.

  lo_read_request = lo_entity_resource->create_request_for_read( ).
  lo_read_response = lo_read_request->execute( ).
  lo_read_response->get_business_data( IMPORTING et_business_data = lt_manager ).
```

**Step 1:** Create the read request instance using the entity resource instance:

```

  DATA: lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity01,
        lo_read_request    TYPE REF TO /iwbep/if_cp_request_read_01.

  lo_read_request = lo_entity_resource->create_request_for_read( ).

```

> ### Note:  
> See [OData Request: Using Navigation](odata-request-using-navigation-57f2139.md) for more information about how to create an optional entity resource instance.

> ### Note:  
> Instead of a ***READ*** request, you can also to set up an ***UPDATE*** or ***DELETE*** request for the optional entity.

**Step 2:** Execute the ***read*** request and fetch the corresponding read response instance:

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
> The zero-to-one read request response is always a table that contains either zero or one entry.

**Related Information**  


[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Using Navigation](odata-request-using-navigation-57f2139.md "Create an OData request using a navigation in the Client Proxy instance.")

