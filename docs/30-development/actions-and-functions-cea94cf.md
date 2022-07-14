<!-- loiocea94cf65bed42b6b5796fbe7d980b51 -->

# Actions and Functions

You want to execute an OData request to invoke an operation \(i.e. an action or function\) using the Client Proxy.



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_d15_dtn_4tb"/>

## OData V2

See also: [MS OData](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

A Service Operation is represented by a Function Import and returns any of the following:

-   Primitive type

-   A single Entity-Type instance

-   A single Complex-Type instance

-   Collection of Complex-Type instances

-   Collection of Primitive types


The corresponding Function Import may have side effects and can be invoked by any pre-defined HTTP method.



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_okj_ltn_4tb"/>

## OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)



### Function

A function is an operation exposed by an OData service that does **not** have side effects.

Functions **must** return data and **can** be further composed with additional path segments. Functions are invoked using HTTP method `GET`.



### Action

An action is an operation exposed by an OData service that **may** have side effects.

Actions **may** return data but **must not** be further composed with additional path segments. Actions are invoked using HTTP method `POST`.



### Operation

Functions and Actions are considered Operations. Operations are either bound to a resource \(e.g. an entity type\), enabling them to be called as members of an instance of that type, or unbound, in which case they are called as static operations \(using so called “action imports” or “function imports”, since a static – i.e. unbound – operation cannot be called directly\).



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_p53_r5n_4tb"/>

## Example Requests



### V4 Function Import

“GetEmployeeByManagerId” including non-binding parameter “ManagerId”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/GetEmployeeByManagerID(ManagerID='0001')
```



### V4 Bound Action

“AcChangeTeamOfEmployee” including non-binding parameter “TeamId”

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES('2')/SAP__self.AcChangeTeamOfEmployee
```

Request body:

```

{ 
"TeamID" : "TEAM_02" 
}
```



### V2 Function

“SetEmployeeSalary” including non-binding parameter “Id” and “Amount”

```
PUT /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/SetEmployeeSalary?Id='0001'&Amount=200
```



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_m32_qvn_4tb"/>

## How-To



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_yc4_15y_4tb"/>

## Operation Import



### Overview

Starting point for invoking an operation import is the corresponding operation resource, which is directly created on the Client Proxy instance.

The resource instance can be used to create a request instance; the latter can directly execute the request.

Last, the response instance – which can be used to retrieve the response business data of the successfully executed request – can be fetched from the request instance.

> ### Note:  
> In OData V2, all Operation requests have to be created as Function Import requests.



### Example

You want to invoke the V2 function ‘PromoteEmployee’ with the non-binding \(i.e. input\) parameters “Id=’0001’” and “Level=2’:

```
POST /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/PromoteEmployee?Id='0001'&Level=2
```

```


TYPES:
BEGIN OF tys_parameter,
id TYPE /iwbep/tea_employee_id,
level TYPE i,
END OF tys_parameter.

DATA: lo_client_proxy      TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_function_resource TYPE REF TO /iwbep/if_cp_resource_function,
        lo_function_request  TYPE REF TO /iwbep/if_cp_request_function,
        lo_function_response TYPE REF TO /iwbep/if_cp_response_function,
        ls_parameter         TYPE tys_parameter,
        ls_busi_data         TYPE /iwbep/tea_employee.

  lo_function_resource = lo_client_proxy->create_resource_for_function( 'PROMOTE_EMPLOYEE').
  ls_parameter = VALUE #( id = '0001' level = 2 ).

  lo_function_resource->set_parameter( ls_parameter ).
  lo_function_request = lo_function_resource->create_request( ).
  lo_function_request->set_if_match( ‘2407’ ).

  lo_function_response = lo_function_request->execute(/iwbep/if_cp_request_function=>gcs_http_method-post ).
  CHECK lo_function_response->has_business_data( ) = abap_true.

  lo_function_response->get_business_data( IMPORTING ea_response_data = ls_busi_data ).
```



### Step by step

**Step 1:** Creation of the function resource. “PROMOTE\_EMPLOYEE” is the **internal** name of function “PromoteEmployee”:

```

  DATA: lo_client_proxy      TYPE REF TO /iwbep/if_cp_client_proxy,

        lo_function_resource TYPE REF TO /iwbep/if_cp_resource_function.

  lo_function_resource = lo_client_proxy->create_resource_for_function( 'PROMOTE_EMPLOYEE').
```

**Step 2:** You set the non-binding \(i.e. input\) parameters on the function resource instance. This can be done on the function resource, using method “SET\_PARAMETER”:

```
TYPES:

BEGIN OF tys_parameter,

id TYPE /iwbep/tea_employee_id,

level TYPE i,

END OF tys_parameter.

DATA: ls_parameter TYPE tys_parameter.

ls_parameter = VALUE #(id = '0001' level = 2 ).

lo_function_resource->set_parameter( ls_parameter ).
```

**Step 3:** You create a function request via the function resource instance:

```
DATA: lo_function_request TYPE REF TO /iwbep/if_cp_request_function.

lo_function_request = lo_function_resource->create_request( ).
```

**Step 4:** You set the corresponding HTTP method to invoke the function on the request object – in our example, it would be POST. This can be done by using method SET\_HTTP\_METHOD or directly in the EXECUTE method. You can use the given constants in GCS\_HTTP\_METHOD of interface /IWBEP/IF\_CP\_REQUEST\_FUNCTION:

```

  DATA: lo_function_response TYPE REF TO /iwbep/if_cp_response_function.

  “Option one: Set http method on the request
  lo_function_request->set_http_method( /iwbep/if_cp_request_function=>gcs_http_method-post ).

  “Option two: Directly set the http method when executing the function
  lo_function_response = lo_function_request->execute( /iwbep/if_cp_request_function=>gcs_http_method-post ).
```

> ### Note:  
> Setting the HTTP method is **only** allowed for OData V2 requests; in OData V4, functions must always be called via GET and actions via POST.
> 
> You do not need to set the HTTP method if the function is called via GET.

**Step 5:** You set the If-Match header to provide an \(weak\) ETag \(if needed for this request\). If the corresponding request header would e.g. be if-match: W/"2407", the needed input for SET\_IF\_MATCH would be ‘2407’:

```
lo_function_request->set_if_match( ‘2407’ ).
```

> ### Note:  
> Only V2 remote consumption supports the If-Match header!

**Step 6:** You execute the Function request:

```

  DATA: lo_function_response TYPE REF TO /iwbep/if_cp_response_function.

  lo_function_response = lo_function_request->execute( /iwbep/if_cp_request_function=>gcs_http_method-post ).
```

**Step 7:** You check whether the response object does contain business data. This is especially useful for nullable operations, where the operation might not return data \(compare to HTTP return code 204 – No Content\):

```
CHECK lo_function_response->has_business_data( ) = abap_true.
```

**Step 8:** You fetch the business data from the response object \(if the corresponding function does return business data\):

```

  DATA: ls_busi_data TYPE /iwbep/tea_employee.

  lo_function_response->get_business_data( IMPORTING ea_response_data = ls_busi_data ).
```

> ### Note:  
> -   When using the V4 local client proxy, the business data you enter will not be converted for inbound processing; the data provider receives exactly the data you entered in the request. Furthermore, for both V2 and V4, the business data received from the \(local consumption\) response will also not be re-converted for outbound processing.
> 
> -   Involving an OData V4 action import works in exactly the same manner; simply use method CREATE\_RESOURCE\_FOR\_ACTION instead of CREATE\_RESOURCE\_FOR\_FUNCTION



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_ekq_r1z_4tb"/>

## Bound Operation



### Overview

Starting point for invoking a bound operation is the corresponding operation resource. In contrast to the operation import, however, this resource is not directly created at the client proxy instance; it is created at the resource object the operation is bound to \(i.e. either an entity resource or an entity list resource\).

The resource instance can be used to create a request instance; the latter can directly execute the request.

Last, the response instance – which can be used to retrieve the response business data of the successfully executed request – can be fetched from the request instance.

> ### Note:  
> Bound Operations are only available for OData V4 requests. All Operation related OData V2 requests have to be created as Function Import requests.



### Example

You want to invoke the V4 bound action ‘IncreaseSalary’ with the non-binding \(i.e. input\) parameters “NewSalary=5000” and “Currency=’EUR’”. The action is bound to one entity of the entity set “Employees”:

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



### Step by step

**Step 1:** Creation of the entity resource. Needed is the employee with Id ‘0006’ of the entity set ‘Employees’ \(with **internal** name ‘EMPLOYEES’\):

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

**Step 2:** Now you create the action resource instance. This is done on the instance the action is bound to \(an entity of entity set ‘Employees’ in this case\). ‘INCREASE\_SALARY’ is the **internal** name of action ‘IncreaseSalary’:

```

  DATA: lo_action_resource TYPE REF TO /iwbep/if_cp_resource_action.

  lo_action_resource = lo_entity_resource->bind_action( 'INCREASE_SALARY' ).
```

**Step 3:** You create an action request instance via the action resource:

```

  DATA: lo_action_request TYPE REF TO /iwbep/if_cp_request_action.

  lo_action_request = lo_action_resource->create_request( ).
```

**Step 4:** You set the non-binding \(i.e. input\) parameters of the bound action on the action request

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

**Step 5:** You set the If-Match header to provide an \(weak\) ETag \(if needed for this request\) on the action request. If the corresponding request header would e.g. be if-match: W/"2407", the needed input for SET\_IF\_MATCH would be ‘2407’:

```
Lo_action_request->set_if_match( ‘2407’ )
```

> ### Note:  
> Only remote consumption supports the If-Match header!

**Step 6:** You execute the action request and gain the action response instance:

```

  DATA: lo_action_response TYPE REF TO /iwbep/if_cp_response_action.

  lo_action_response = lo_action_request->execute( ).
```

**Step 7:** You check whether the response object does contain business data. This is especially useful for nullable operations, where the operation might not return data \(compare to HTTP return code 204 – No Content\):

```
CHECK lo_action_response->has_business_data( ) = abap_true.
```

**Step 8:** You fetch the business data from the response object \(if the corresponding action does return business data\):

```

  DATA: ls_employee TYPE /iwbep/s_v4_tea_employee.

  lo_action_response->get_business_data( IMPORTING ea_business_data = ls_employee
```

> ### Note:  
> -   When using the V4 local client proxy, the business data you enter will not be converted for inbound processing; the data provider receives exactly the data you entered in the request. Furthermore, the business data received from the \(local consumption\) response will also not be re-converted for outbound processing.
> 
> -   Invoking an OData V4 bound function works in exactly the same manner; simply use method BIND\_FUNCTION instead of BIND\_ACTION



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_on1_jfz_4tb"/>

## Constraints

-   If-Match header is only supported for remote consumption

-   In case of function imports, the If-Match header is only supported for OData V2 requests

-   Composable Functions are not supported

-   $expand in combination with operations is not supported

-   $select is not supported for actions

-   Return-Prefer header is not supported for actions

-   System query options are not supported for V4 functions

-   If the return type of a V2 function is an entity type, and this entity type is used by more than one entity sets, the V2 request context will only contain the \(edm\) name of the first entity set with the underlying entity type; a precise mapping is currently not possible. For remote consumption, this can be handled in the proxy model by setting the correct entity set via method `/iwbep/if_v4_med_func_imp->set_entity_set_name`


