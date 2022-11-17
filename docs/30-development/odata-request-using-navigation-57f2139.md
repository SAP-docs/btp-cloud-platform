<!-- loio57f2139773734539991e2afeef477666 -->

# OData Request: Using Navigation

Create an OData request using a navigation in the Client Proxy instance.



<a name="loio57f2139773734539991e2afeef477666__section_nyn_kxd_ttb"/>

## OData Specification



### OData Version 2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

A unidirectional \(one-way\) relationship \(for example, a Link\) is when two entity types are related by association, but only one of the entity types defines a ***NavigationProperty*** that binds to the association.



### OData Version 4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

Relationships from one entity to another are represented as navigation properties. Navigation properties are defined as part of an entity type, but can also appear on entity instances as undeclared dynamic navigation properties. Each relationship has a cardinality.



<a name="loio57f2139773734539991e2afeef477666__section_tgw_yxd_ttb"/>

## Example Requests



### Version 4

Get all employees associated with Team ‘***TEAM\_01***’ via navigation property ‘***Team2Employees***’:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams('TEAM_01')/Team2Employees
```



### Version 2

Get the team of the employee with Id ‘***0005***’ via navigation property “***My\_Team***”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees(Id='0005')/My_Team
```



<a name="loio57f2139773734539991e2afeef477666__section_j5x_kyd_ttb"/>

## Using Navigation Request



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to use navigations.

The starting point for a request using a navigation is an entity resource. On the entity resource, you can create a resource for the corresponding navigation target.



### Example 1

Navigate to an entity list with Navigation Property “***Department2Teams***”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Departments(Id='1',Sector='Consulting')/Department2Teams
```



### Steps

**Step 1:** Create the target resource on the entity resource using the **internal** name of the navigation property \(“***DEPARTMENT\_2\_TEAMS***”\):

```

  DATA: lo_entity_resource      TYPE REF TO /iwbep/if_cp_resource_entity,
        lo_target_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

  lo_target_list_resource = lo_entity_resource->navigate_to_many( ‘department_2_teams’ ).
```

> ### Note:  
> You can use the target resource to create a READ request.



### Example 2

Navigate to a single entity using the Navigation Property “***Team2Manager***”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams('TEAM_01')/Team2Manager
```



### Steps

**Step 1:** Create the target resource on the entity resource using the **internal** name of the navigation property \(“***TEAM\_2\_MANAGER***”\):

```

  DATA: lo_entity_resource        TYPE REF TO /iwbep/if_cp_resource_entity,
        lo_target_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_target_entity_resource = lo_entity_resource-> navigate_to_single( ‘team_2_manager’ ).
```

> ### Note:  
> You can use the target resource to create a READ request.



### Example 3

Navigate to an optional \(for example. zero-to-one navigation\) entity using the Navigation Property “***Employee2Manager***”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0004')/Employee2Manager
```



### Step-by-step

**Step 1:** Create the target resource on the entity resource using the **internal** name of the navigation property \(“***EMPLOYEE\_2\_MANAGER***”\):

```

  DATA: lo_entity_resource        TYPE REF TO /iwbep/if_cp_resource_entity,
        lo_target_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity01.

  lo_target_entity_resource = lo_entity_resource-> navigate_to_optional( ‘employee_2_manager’ ). 
```

> ### Note:  
> You can use the target resource to create an optional READ request.

**Related Information**  


[OData Request: Read Entity](odata-request-read-entity-9d7dde4.md "To create an OData request to read an entity in the Client Proxy instance.")

[OData Request Terms](odata-request-terms-a3b0e95.md "An overview of some OData Request terminology.")

[OData Request: Create Entity](odata-request-create-entity-56be82d.md "Create an entity in the Client Proxy instance with insert entity request.")

