<!-- loio57f2139773734539991e2afeef477666 -->

# OData Request: Using Navigation

You want to execute an OData request using a navigation within the Client Proxy.



<a name="loio57f2139773734539991e2afeef477666__section_nyn_kxd_ttb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

A unidirectional relationship \(for example, a Link\), which occurs when two EntityTypes are related via an association, but only one of the EntityTypes defines a NavigationProperty bound to the association.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Relationships from one entity to another are represented as navigation properties. Navigation properties are generally defined as part of an entity type, but can also appear on entity instances as undeclared dynamic navigation properties. Each relationship has a cardinality.



<a name="loio57f2139773734539991e2afeef477666__section_tgw_yxd_ttb"/>

## Example Requests



### V4

Get all employees associated with Team ‘TEAM\_01’ via navigation property ‘Team2Employees’:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams('TEAM_01')/Team2Employees
```



### V2

Get the team of the employee with Id ‘0005’ via navigation property “My\_Team”:

```
GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/Employees(Id='0005')/My_Team
```



<a name="loio57f2139773734539991e2afeef477666__section_j5x_kyd_ttb"/>

## How-To



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present general examples on how to use navigations.

Starting point for a request using a navigation is an entity resource. Kindly check e.g. the chapter about reading an entity on how to create an entity resource instance. On the entity resource, it is possible to create a resource for the corresponding navigation target.



### Example 1

You want to navigate to an entity list via Navigation Property “Department2Teams”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Departments(Id='1',Sector='Consulting')/Department2Teams
```



### Step-by-step

**Step 1:** Create the target resource on the entity resource by using the **internal** name of the navigation property \(“DEPARTMENT\_2\_TEAMS”\):

```

  DATA: lo_entity_resource      TYPE REF TO /iwbep/if_cp_resource_entity,
        lo_target_list_resource TYPE REF TO /iwbep/if_cp_resource_list.

  lo_target_list_resource = lo_entity_resource->navigate_to_many( ‘department_2_teams’ ).
```

> ### Note:  
> See the chapter about reading an entity for further details about how to create an entity resource instance.

> ### Note:  
> The target resource can then be used to create e.g. a READ request. See the corresponding chapter on how to create a READ request for further details.



### Example 2

You want to navigate to a single entity via Navigation Property “Team2Manager”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Teams('TEAM_01')/Team2Manager
```



### Step-by-step

**Step 1:** Create the target resource on the entity resource by using the **internal** name of the navigation property \(“TEAM\_2\_MANAGER”\):

```

  DATA: lo_entity_resource        TYPE REF TO /iwbep/if_cp_resource_entity,
        lo_target_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity.

  lo_target_entity_resource = lo_entity_resource-> navigate_to_single( ‘team_2_manager’ ).
```

> ### Note:  
> See the chapter about reading an entity for further details about how to create an entity resource instance.

> ### Note:  
> The target resource can then be used to create e.g. a READ request. See the corresponding chapter on how to create a READ request for further details.



### Example 3

You want to navigate to an optional \(i.e. zero-to-one navigation\) entity via Navigation Property “Employee2Manager”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees('0004')/Employee2Manager
```



### Step-by-step

**Step 1:** Create the target resource on the entity resource by using the **internal** name of the navigation property \(“EMPLOYEE\_2\_MANAGER”\):

```

  DATA: lo_entity_resource        TYPE REF TO /iwbep/if_cp_resource_entity,
        lo_target_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity01.

  lo_target_entity_resource = lo_entity_resource-> navigate_to_optional( ‘employee_2_manager’ ). 
```

> ### Note:  
> See the chapter about reading an entity for further details about how to create an entity resource instance.

> ### Note:  
> The target resource can then be used to create e.g. an optional READ request. See the corresponding chapter on how to create an optional READ request for further details.

