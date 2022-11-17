<!-- loio6c29b98fa23e47919ea7cedce1a3e1e2 -->

# Bound Operation



<a name="loio6c29b98fa23e47919ea7cedce1a3e1e2__section_ekq_r1z_4tb"/>

## Bound Operation



### Overview

The starting point for invoking a bound operation is the corresponding operation resource. This resource is not created directly at the client proxy instance. It is created at the resource object the operation is bound to \(for example, an entity resource or an entity list resource\). You can use the resource instance to create a request instance. You can use the response instance to retrieve the response business data for the successfully executed request and can be fetched from the request instance.

> ### Note:  
> Bound Operations are only available for OData Version 4 requests. All Operation related OData Version 2 requests must be created as Function Import requests.



### Example

Invoke the Version 4 bound action ‘***IncreaseSalary***’ with the non-binding \(for example, input\) parameters “***NewSalary=5000***” and “***Currency=***’***EUR***’”. The action is bound to one entity of the entity set “***Employees***”:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/Employees(‘0006’) /com.sap.gateway.default.iwbep.tea_busi.v0003.IncreaseSalary
```

```


  WITH the request body

  {
  "NewSalary" : 5000, "Currency" : "EUR" 
  }

```

```

  TYPES:

  BEGIN OF tys_parameter,
  new_salary TYPE i,
  currency TYPE c LENGTH 3,
  END OF tys_parameter,
  
  BEGIN OF tys_key,
  id TYPE /iwbep/v4_tea_employee_id,
  END OF tys_key.

  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_action_request  TYPE REF TO /iwbep/if_cp_request_action,
        lo_action_resource TYPE REF TO /iwbep/if_cp_resource_action,
        lo_action_response TYPE REF TO /iwbep/if_cp_response_action,

        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity,
        ls_parameter       TYPE tys_parameter,
        ls_employee        TYPE /iwbep/s_v4_tea_employee,
        ls_key             TYPE tys_key.

  ls_key = VALUE #( id = ‘0006’ ).

  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key( ls_key ).

  lo_action_resource = lo_entity_resource->bind_action( 'INCREASE_SALARY' ).
  lo_action_request = lo_action_resource->create_request( ).

  ls_parameter = VALUE #( new_salary = 5000 currency = ‘eur’ ).

  lo_action_request->set_parameter( ls_parameter ).
  lo_action_request->set_if_match( '1234' ).
  lo_action_response = lo_action_request->execute( ).

  CHECK lo_action_response->has_business_data( ) = abap_true.
  lo_action_response->get_business_data( IMPORTING ea_business_data = ls_employee ).
```



### Steps

**Step 1:** Create the entity resource with the employee ***Id*** ‘***0006***’ of the entity set ‘***Employees***’ \(with **internal** name ‘***EMPLOYEES’***\):

```

  TYPES:
    BEGIN OF tys_key,
      id TYPE /iwbep/v4_tea_employee_id,
    END OF tys_key.

  DATA: lo_client_proxy    TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity,
        ls_key             TYPE tys_key.

  ls_key = VALUE #( id = ‘0006’ ).

  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES')->navigate_with_key( ls_key ).
```

**Step 2:** Create the action resource instance on the instance the action is bound to \(In this example, an entity of entity set ‘***Employees***’\). ‘***INCREASE\_SALARY***’ is the **internal** name of action ‘***IncreaseSalary’***:

```

  DATA: lo_action_resource TYPE REF TO /iwbep/if_cp_resource_action.

  lo_action_resource = lo_entity_resource->bind_action( 'INCREASE_SALARY' ).
```

**Step 3:** Create an action request instance with the action resource:

```

  DATA: lo_action_request TYPE REF TO /iwbep/if_cp_request_action.

  lo_action_request = lo_action_resource->create_request( ).
```

**Step 4:** Set the non-binding \(for example, input\) parameters of the bound action on the action request:

```

  TYPES:
  BEGIN OF tys_parameter,
  new_salary TYPE i,
  currency   TYPE c LENGTH 3,
  END OF tys_parameter,

  DATA: ls_parameter TYPE tys_parameter.

  ls_parameter = VALUE #( new_salary = 5000 currency = ‘eur’ ).
  lo_action_request->set_parameter( ls_parameter ).
```

**Step 5:** Set the ***If-Match*** header to provide an ETag \(if needed for this request\) on the action request. In this example, the corresponding request header is ***if-match***: W/"***2407***", the required input for ***SET\_IF\_MATCH*** is ‘***2407***’:

```
Lo_action_request->set_if_match( ‘2407’ )
```

> ### Note:  
> Only remote consumption supports the ***If-Match*** header.

**Step 6:** Create the action request and get the action response instance:

```

  DATA: lo_action_response TYPE REF TO /iwbep/if_cp_response_action.

  lo_action_response = lo_action_request->execute( ).
```

**Step 7:** Check if the response object contains business data. This is especially useful for nullable operations, where the operation might not return data \(compare to HTTP return code ***204 – No Content***\):

```
CHECK lo_action_response->has_business_data( ) = abap_true.
```

**Step 8:** Fetch the business data from the response object \(if the corresponding action **does** return business data\):

```

  DATA: ls_employee TYPE /iwbep/s_v4_tea_employee.

  lo_action_response->get_business_data( IMPORTING ea_business_data = ls_employee
```

> ### Note:  
> -   When using the Version 4 local client proxy, the business data you enter isn't converted for inbound processing. The data provider receives the exact data you entered in the request. The business data received from the \(local consumption\) response is also not re-converted for outbound processing.
> 
> -   Invoking an OData Version 4 bound function works the same way. Use method***BIND\_FUNCTION*** instead of ***BIND\_ACTION***.



<a name="loio6c29b98fa23e47919ea7cedce1a3e1e2__section_on1_jfz_4tb"/>

## Constraints

-   If-Match header is only supported for **remote** consumption.

-   For function imports, the If-Match header is only supported for OData **Version 2** requests.

-   Composable Functions are **not** supported.

-   ***$expand*** with operations is ***not*** supported.

-   ***$select*** is ***not*** supported for actions.

-   ***Return-Prefer*** header is ***not*** supported for actions.

-   System query options are **not** supported for Version 4 functions.

-   If the return type of a Version 2 function is an entity type and this entity type is used by more than one entity set, the Version 2 request context only contains the \(EDM\) name of the first entity set with the underlying entity type. A precise mapping is currently not possible. For remote consumption, this can be handled in the proxy model by setting the correct entity set via method .`/iwbep/if_v4_med_func_imp->set_entity_set_name`


**Related Information**  


[Actions and Functions](actions-and-functions-cea94cf.md "Create an OData request to run an operation (an action or function) in the Client Proxy instance.")

[Import Operation](import-operation-8fce3ce.md "")

