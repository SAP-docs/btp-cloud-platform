<!-- loio28de1b09aec84041a53e50c0af105dec -->

# Action and Functions

You want to execute an OData request to invoke an operation \(for example, an action or a function\) using the OData Client Proxy.



<a name="loio28de1b09aec84041a53e50c0af105dec__section_fh2_by1_5qb"/>

## OData Specification

**OData V2**

A service operation is represented by a function import and returns one of the following:

-   *Primitive* type

-   Collection of *Primitive* types

-   A single *ComplexType* instance

-   Collection of *ComplexType* instances

-   A single *EntityType* instance


> ### Note:  
> The corresponding function import may have side effects and can be invoked by any pre-defined HTTP method.

For more information, see the [Open Data Protocol](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata/2b686a1a-9e1f-456f-80ff-072a010fc278).

**OData V4**

Function

A function is an operation exposed by an OData Client Proxy service that does not have side effects. Functions must return data and can be further composed with additional path segments. Functions are invoked using HTTP method `GET`.

Action

An action is an operation exposed by an OData Client Proxy service that may have side effects. Actions may return data but must not be further composed with additional path segments. Actions are invoked using HTTP method `POST`.

Operation

Functions and actions are considered operations. Operations are either bound to a resource \(for example, an entity type\), enabling them to be called as members of an instance of that type, or unbound, in which case they are called as static operations \(using *action imports* or *function imports*, since a static – for example, unbound – operation cannot be called directly\).

For more information, see [OData Version 4.01. Part1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).



<a name="loio28de1b09aec84041a53e50c0af105dec__section_lnv_mz1_5qb"/>

## Example Requests

**V4 Function Import**

*GetEmployeeByManagerId* including non-binding parameter *ManagerId*

> ### Sample Code:  
> ```
> 
> GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/GetEmployeeByManagerID(ManagerID='0001')
> ```

**V4 Bound Action**

*AcChangeTeamOfEmployee* including non-binding parameter *TeamId*.

```

POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES('2')/SAP__self.AcChangeTeamOfEmployee
```

Request Body.

> ### Sample Code:  
> ```
> 
> {
>   "TeamID" : "TEAM_02"
> }
> 
> ```

**V2 Function**

*SetEmployeeSalary* including non-binding parameter *Id* and *Amount*.

> ### Sample Code:  
> ```
> 
> PUT /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/SetEmployeeSalary?Id='0001'&Amount=200
> ```



<a name="loio28de1b09aec84041a53e50c0af105dec__section_vvk_d1b_5qb"/>

## How-To

**Overview**

Starting point for invoking an operation import is the corresponding operation resource, which is directly created on the OData Client Proxy instance.

The resource instance can be used to create a request instance; the latter can directly execute the request.

Finally, the response instance – which can be used to retrieve the response business data of the successfully executed request – can be fetched from the request instance.

**Example**

You want to invoke the *PromoteEmployee* V2 function with the non-binding \(that means input\) parameter `"Id=’0001'"` and `"Level=2’"`:

POST /sap/opu/odata/IWBEP/TEA\_TEST\_APPLICATION/PromoteEmployee?Id='0001'&Level=2

> ### Sample Code:  
> ```
> 
> 	TYPES: 
> 		BEGIN OF tys_parameter, 
> 		id TYPE /iwbep/tea_employee_id, 
> 		level TYPE i,  
> 		END OF tys_parameter. 
> 
> 	DATA:
> 		lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy, 
> 		lo_function_resource TYPE REF TO /iwbep/if_cp_resource_function, 
> 		lo_function_request TYPE REF TO /iwbep/if_cp_request_function, 
> 		lo_function_response TYPE REF TO /iwbep/if_cp_response_function, 
> 		ls_parameter TYPE tys_parameter, 
> 		ls_busi_data TYPE /iwbep/tea_employee. 
> 
> 	lo_function_resource = lo_client_proxy->create_resource_for_function( 'PROMOTE_EMPLOYEE'). 
> 
> ls_parameter = VALUE #( id = '0001'   level = 2 ). 
> lo_function_resource->set_parameter( ls_parameter ). 
> 
> lo_function_request = lo_function_resource->create_request( ). 
> 
> lo_function_request->set_if_match( ‘2407’ ).  
> 
> lo_function_response = lo_function_request->execute(   
> /iwbep/if_cp_request_function=>gcs_http_method-post ). 
> 
> CHECK lo_function_response->has_business_data( ) = abap_true. 
> 
> lo_function_response->get_business_data( IMPORTING ea_response_data = ls_busi_data ). 
> ```

**Procedure**

1.  Creation of the function resource. `PROMOTE_EMPLOYEE` is the internal name of function *PromoteEmployee*:

    > ### Sample Code:  
    > ```
    > 
    > DATA:
    > lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy,
    > lo_function_resource type ref to /iwbep/if_cp_resource_function.
    > 
    > lo_function_resource = lo_client_proxy->create_resource_for_function( 'PROMOTE_EMPLOYEE')
    > ```

2.  Set the non-binding \(that means input\) parameter. This can be done on the function resource using method `SET_PARAMETER`:

    > ### Sample Code:  
    > ```
    > 
    > TYPES:
    >   BEGIN OF tys_parameter, 
    >    id TYPE /iwbep/tea_employee_id, 
    >   level TYPE i, 
    >   END OF tys_parameter.
    > 
    > DATA: ls_parameter TYPE tys_parameter. 
    > 
    > ls_parameter = VALUE #(id = '0001'   level = 2 ). 
    > lo_function_resource->set_parameter( ls_parameter ). 
    > 
    > 
    > ```

3.  Create a function request using the function resource instance:

    > ### Sample Code:  
    > ```
    > 
    > DATA:
    > lo_function_request TYPE REF TO /iwbep/if_cp_request_function.
    > 
    > lo_function_request = lo_function_resource->create_request( ).
    > 
    > ```

4.  Set the corresponding HTTP method to invoke the function \(in this example `POST`\). This can be done using method `SET_HTTP_METHOD` or directly in the `EXECUTE` method. You can use the given constants in `GCS_HTTP_METHOD` of interface `/IWBEP/IF_CP_REQUEST_FUNCTION`:

    > ### Sample Code:  
    > ```
    > 
    > DATA:
    > lo_function_response TYPE REF TO /iwbep/if_cp_response_function.
    > 
    > “Option one: Set HTTP method on the request
    > lo_function_request->set_http_method( /iwbep/if_cp_request_function=>gcs_http_method-post ).
    > 
    > “Option two: Directly set the HTTP method when executing the function
    > lo_function_response = lo_function_request->execute(/iwbep/if_cp_request_function=>gcs_http_method-post ).
    > 
    > ```

    > ### Note:  
    > Setting the HTTP method is only allowed for OData V2 requests. For OData V4, functions must always be called using `GET`.
    > 
    > You do not need to set the HTTP method if the function is called via`GET` and actions via `POST`.

5.  Set the *if-match* header to provide an \(weak\) ETag \(if needed for this request\).

    If the corresponding request header was, for example, *if-match: W/"2407"*, the required input for `SET_IF_MATCH` was *‘2407’*:

    > ### Sample Code:  
    > ```
    > 
    > lo_function_request->set_if_match( ‘2407’ ).
    > ```

    > ### Note:  
    > Only V2 remote consumption supports the *if-match* header.

6.  Execute the Function request:

    > ### Sample Code:  
    > ```
    > 
    > DATA: lo_function_response TYPE REF TO /iwbep/if_cp_response_function.
    > 
    > lo_function_response = lo_function_request->execute(
    > /iwbep/if_cp_request_function=>gcs_http_method-post ). 
    > ```

7.  Check whether the response object does contain business data. This is especially useful for nullable operations where the operation might not return data \(compare to HTTP return code `204 – No Content)`:

    > ### Sample Code:  
    > ```
    > CHECK lo_function_response->has_business_data( ) = abap_true. 
    > ```

8.  Fetch the business data from the response object \(if the corresponding function does return business data\):

    > ### Sample Code:  
    > ```
    > 
    > DATA:
    > ls_busi_data TYPE /iwbep/tea_employee.
    > 
    > lo_function_response->get_business_data( IMPORTING ea_response_data = ls_busi_data ).
    > 
    > ```

    > ### Note:  
    > When using the V4 local OData Client Proxy, the business data you enter will not be converted for inbound processing; the data provider receives exactly the data you entered in the request. Furthermore, for both V2 and V4, the business data received from the \(local consumption\) response will also not be re-converted for outbound processing.
    > 
    > Involving an OData V4 action import works in the same way: use method `CREATE_RESOURCE_FOR_ACTION` instead of `CREATE_RESOURCE_FOR_FUNCTION`.




<a name="loio28de1b09aec84041a53e50c0af105dec__section_ard_djl_hsb"/>

## Bound Operations

**Overview**

The starting point for invoking a bound operation is the corresponding operation resource. In contrast to the operation import, however, this resource is not directly created at the client proxy instance; it is created at the resource object the operation is bound to \(that means either an entity resource or an entity list resource\).

The resource instance can be used to create a request instance; the latter can directly execute the request.

Last, the response instance – which can be used to retrieve the response business data of the successfully executed request – can be fetched from the request instance.

> ### Note:  
> Bound Operations are only available for OData V4 requests. All operation-related OData V2 requests must be created as function import requests.

**Example**

You want to invoke the V4 bound action "IncreaseSalary" with the non-binding \(that means input\) parameters "NewSalary=5000" and "Currency='EUR'". The action is bound to one entity of the entity set "Employees":

POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea\_busi/0003/Employees\('0006'\) /com.sap.gateway.default.iwbep.tea\_busi.v0003.IncreaseSalary

Request body:

> ### Sample Code:  
> ```
> 
> {
>  "NewSalary" : 5000
>  "Currency" : "EUR"
> }
> 
> TYPES: 
>  BEGIN OF tys_parameter, 
>   new_salary TYPE i, 
>   currency     TYPE c length 3,  
>  END OF tys_parameter, 
> 
> BEGIN OF tys_key, 
>  id TYPE /iwbep/v4_tea_employee_id, 
> END OF tys_key.  
> 
> 	DATA:	lo_client_proxy	   TYPE REF TO /iwbep/if_cp_client_proxy,
> 			lo_action_request	 TYPE REF TO /iwbep/if_cp_request_action, 
> 			lo_action_resource	TYPE REF TO /iwbep/if_cp_resource_action, 
> 			lo_action_response	TYPE REF TO /iwbep/if_cp_response_action, 
> 			lo_entity_resource     TYPE REF TO /iwbep/if_cp_resource_entity, 
> 			ls_parameter		 TYPE tys_parameter, 
> 			ls_employee            TYPE /iwbep/s_v4_tea_employee, 
> 			ls_key                 TYPE tys_key.
> 
> ls_key = value #( id = ‘0006’ ).
>  lo_entity_resource = lo_client_proxy->create_resource_for_entity_set( 'EMPLOYEES' 
> 								)->navigate_with_key( ls_key ). 
>  lo_action_resource = lo_entity_resource->bind_action( 'INCREASE_SALARY' ). 
> 
>  lo_action_request = lo_action_resource->create_request( ). 
> 
>  ls_parameter = value #( new_salary = 5000  currency = ‘EUR’ ).  
> 
>  lo_action_request->set_parameter( ls_parameter ). 
> 
>  lo_action_request->set_if_match( '1234' ).  
> 
>  lo_action_response = lo_action_request->execute( ). 
> 
> CHECK lo_action_response->has_business_data( ) = abap_true.  
> 
> lo_action_response->get_business_data( IMPORTING ea_business_data = ls_employee ). 
> ```

**Procedure**

1.  Creation of the entity resource. Required is the employee with Id '0006' of the entity set 'Employees' \(with internal name 'EMPLOYEES'\):

    > ### Sample Code:  
    > ```
    > TYPES:
    > BEGIN OF tys_key, 
    >  id TYPE /iwbep/v4_tea_employee_id, 
    > END OF tys_key. 
    >  
    >  DATA:  lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy, 
    > 	   lo_entity_resource TYPE REF TO /iwbep/if_cp_resource_entity, 
    > 	   ls_key TYPE tys_key. 
    > 
    > ls_key = value #( id = ‘0006’ ). 
    > 
    > lo_entity_resource = lo_client_proxy->create_resource_for_entity_set ('EMPLOYEES')->navigate_with_key( ls_key ).
    > ```

2.  Create the action resource instance. This is done on the instance the action is bound to \(in this case an entity of entity set 'Employees'\). 'INCREASE\_SALARY' is the internal name of action 'IncreaseSalary':

    > ### Sample Code:  
    > ```
    >  
    > DATA: lo_action_resource TYPE REF TO /iwbep/if_cp_resource_action. 
    > 
    > lo_action_resource = lo_entity_resource->bind_action( 'INCREASE_SALARY' ).
    > ```

3.  Create an action request instance using the action resource:

    > ### Sample Code:  
    > ```
    > 
    > DATA: lo_action_request TYPE REF TO /iwbep/if_cp_request_action. 
    > 
    > lo_action_request = lo_action_resource->create_request( ).
    > ```

4.  Set the non-binding \(that means, input\) parameters of the bound action on the action request:

    > ### Sample Code:  
    > ```
    > 
    > TYPES: 
    >  BEGIN OF tys_parameter, 
    >   new_salary TYPE i, 
    >   currency TYPE c length 3, 
    >  END OF tys_parameter, 
    >  
    >   DATA: ls_parameter TYPE tys_parameter. 
    >  
    >  ls_parameter = value #( new_salary = 5000 currency = ‘EUR’ ). 
    > 
    >  lo_action_request->set_parameter( ls_parameter ). 
    > ```

5.  Set the if-match header to provide an \(weak\) ETag \(if required for this request\) on the action request.

    If the corresponding request header would e.g. be if-match: W/"2407", the needed input for SET\_IF\_MATCH would be '2407':

    > ### Sample Code:  
    > ```
    > Lo_action_request->set_if_match( ‘2407’ ).
    > ```

    > ### Note:  
    > Only remote consumption supports the if-match header.

6.  Execute the action request and gain the action response instance:

    > ### Sample Code:  
    > ```
    > 
    > DATA: lo_action_response TYPE REF TO /iwbep/if_cp_response_action.
    > lo_action_response = lo_action_request->execute( ).
    > ```

7.  Check whether the response object does contain business data. This is useful for nullable operations, where the operation might not return data \(compare to HTTP return code `204 – No Content)`:

    > ### Sample Code:  
    > ```
    > CHECK lo_action_response->has_business_data( ) = abap_true.
    > ```

8.  Fetch the business data from the response object \(if the corresponding action does return business data\):

    > ### Sample Code:  
    > ```
    > 
    > DATA: ls_employee TYPE /iwbep/s_v4_tea_employee. 
    > lo_action_response->get_business_data( IMPORTING ea_business_data = ls_employee ) 
    > ```


> ### Note:  
> When using the V4 local client proxy, the business data entered will not be converted for inbound processing; the data provider receives exactly the data you entered in the request. Furthermore, the business data received from the \(local consumption\) response will also not be re-converted for outbound processing.
> 
> Invoking an OData V4 bound function works in the same way: use method `BIND_FUNCTION` instead of `BIND_ACTION`.



<a name="loio28de1b09aec84041a53e50c0af105dec__section_ytg_1db_5qb"/>

## Constraints

-   The *if-match* header is only supported for remote consumption.

-   In case of function imports, the *if-match* header is only supported for OData V2 requests.

-   Composable functions are not supported.

-   $expand in combination with operations is not supported.

-   $select is not supported for actions.

-   The `Return-Prefer` header is not supported for actions.

-   System query options are not supported for V4 functions.

-   If the return type of a V2 function is an entity type and this entity type is used by more than one entity set, the V2 request context will only contain the \(edm\) name of the first entity set with the underlying entity type. A precise mapping is currently not possible.

    For remote consumption, this can be handled in the proxy model by setting the correct entity set using method `/IWBEP/IF_V4_MED_FUNC_IMP → SET_ENTITY_SET_NAME`.


