<!-- loio8fce3cebf2394b94b6b75176e0a9ab6a -->

# Import Operation





### Overview

The starting point for an operation import is the corresponding operation resource that is created directly on the Client Proxy instance. You can use the resource instance to create a request instance. You can use the response instance to retrieve the response business data of the successfully executed request. This is fetched from the request instance.

> ### Note:  
> In OData Version 2, all Operation requests must be created as Function Import requests.



### Example

To invoke the Version 2 function ‘***PromoteEmployee***’ with the non-binding \(for example, input\) parameters “***Id***=***’0001’***” and “***Level=2***’:

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



### Steps

**Step 1:** Create the function resource “***PROMOTE\_EMPLOYEE***” with the **internal** name of function “***PromoteEmployee***”:

```

  DATA: lo_client_proxy      TYPE REF TO /iwbep/if_cp_client_proxy,

        lo_function_resource TYPE REF TO /iwbep/if_cp_resource_function.

  lo_function_resource = lo_client_proxy->create_resource_for_function( 'PROMOTE_EMPLOYEE').
```

**Step 2:** Set the non-binding \(for example. input\) parameters on the function resource instance. You can do this on the function resource, using method “***SET\_PARAMETER***”:

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

**Step 3:** Create a function request in the function resource instance:

```
DATA: lo_function_request TYPE REF TO /iwbep/if_cp_request_function.

lo_function_request = lo_function_resource->create_request( ).
```

**Step 4:** Select the corresponding HTTP method to invoke the function on the request object. In this example, it is ***POST***. You must do this in method ***SET\_HTTP\_METHOD*** or directly in the ***EXECUTE*** method. You can use the given constants in ***GCS\_HTTP\_METHOD*** of interface ***/IWBEP/IF\_CP\_REQUEST\_FUNCTION***:

```

  DATA: lo_function_response TYPE REF TO /iwbep/if_cp_response_function.

  “Option one: Set http method on the request
  lo_function_request->set_http_method( /iwbep/if_cp_request_function=>gcs_http_method-post ).

  “Option two: Directly set the http method when executing the function
  lo_function_response = lo_function_request->execute( /iwbep/if_cp_request_function=>gcs_http_method-post ).
```

> ### Note:  
> Setting the HTTP method is only allowed for OData Version 2 requests. In OData Version 4, functions must always be called with ***GET*** and actions with ***POST***. You don't need to set the HTTP method if the function is called with ***GET***.

**Step 5:** Set the ***If-Match*** header to provide an ETag \(if needed for this request\). For example, if the corresponding request header is ***if-match:*** W/"***2407***", the required input for ***SET\_IF\_MATCH*** is ‘***2407***':

```
lo_function_request->set_if_match( ‘2407’ ).
```

> ### Note:  
> Only Version 2 remote consumption supports the ***If-Match*** header.

**Step 6:** Create the Function request:

```

  DATA: lo_function_response TYPE REF TO /iwbep/if_cp_response_function.

  lo_function_response = lo_function_request->execute( /iwbep/if_cp_request_function=>gcs_http_method-post ).
```

**Step 7:** Check if the response object contains business data. This is especially useful for nullable operations, where the operation might not return data \(compare to HTTP return code 204 – No Content\):

```
CHECK lo_function_response->has_business_data( ) = abap_true.
```

**Step 8:** Fetch the business data from the response object \(if the corresponding function does return business data\):

```

  DATA: ls_busi_data TYPE /iwbep/tea_employee.

  lo_function_response->get_business_data( IMPORTING ea_response_data = ls_busi_data ).
```

> ### Note:  
> -   When using the Version 4 local client proxy, the business data you enter is not converted for inbound processing. The data provider receives the data exactly how you entered it in the request. For both Version 2 and Version 4, the business data received from the \(local consumption\) response is also not re-converted for outbound processing.
> 
> -   Using an OData Version 4 action import works the same way. Use method ***CREATE\_RESOURCE\_FOR\_ACTION*** instead of ***CREATE\_RESOURCE\_FOR\_FUNCTION***.



<a name="loio8fce3cebf2394b94b6b75176e0a9ab6a__section_on1_jfz_4tb"/>

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

[Bound Operation](bound-operation-6c29b98.md "")

