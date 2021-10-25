<!-- loio287674d4684c4a6780799dcd7a5fbd22 -->

# Local Client Proxy

A local proxy is used when a locally deployed OData service is consumed. It delegates a request to the backend component of the corresponding V2 runtime.

> ### Note:  
> The same applies for V4 runtime. Open class `/IWBEP/CL_CP_SRV_PROXY_LOC_V4` in the ABAP Development Tool \(ADT\) and click on *Test Classes*. Test class `ltc_srv_proxy_local_v4` contains examples for V4 runtime.

> ### Note:  
> *Unit Test*: You can use the local proxy to set up a unit test for your data provider class. For more information, see examples below.

> ### Note:  
> Due to performance reasons, not all tests that are usually set up during OData requests, are executed.

**V2 Runtime**

The local proxy for V2 delegates a request to the V2 runtime. As a prerequisite, you must have built a V2 request context from the request object.

In some use cases, a V2 OData service is consumed locally without an additional proxy model being provided. This is especially the case for the unit test scenario. If you want to unit test your V2 DPC, you can use the V2 *Model Provider Class* \(MPC\). In case of local consumption, a client cannot provide a proxy model.

> ### Example:  
> ```
> 
> DATA:	lt_employee      TYPE STANDARD TABLE OF /iwbep/s_tea_employee,
>           lt_employee_a    TYPE STANDARD TABLE OF /iwbep/s_tea_employee_a (abstract entity from the service consumption model). If etag is used in the consumption model,
>           the response has an `etag__etag` field.
>           lo_client_proxy  TYPE REF TO /iwbep/if_cp_client_proxy,
>           lo_read_request  TYPE REF TO /iwbep/if_cp_request_read_list,
>           lo_read_response TYPE REF TO /iwbep/if_cp_response_read_lst.
> TRY.
> 		" Create Proxy
>          lo_client_proxy = CL_WEB_ODATA_CLIENT_FACTORY=>create_v2_local_proxy( VALUE #( service_id      = '/IWBEP/TEA_TEST_APPLICATION'
>                                                                                           service_version = '0001' ) ).
> 
>         " Create read request on entity set 'Employees'
>         lo_read_request = lo_client_proxy->create_resource_for_entity_set( 'Employees' )->create_request_for_read( ).
>         lo_read_response = lo_read_request->execute( ).
> 
>         " Retrieve the business data
>         lo_read_response->get_business_data( IMPORTING et_business_data = lt_employee ).
> 
>       CATCH /iwbep/cx_gateway INTO DATA(lx_gateway).
>         " Error Handling
> ENDTRY.
> 
> ```

**Execution of Operations**

The following actions and functions for the execution of operations are available in the *Client Proxy* framework:

-   The interface `/IWBEP/IF_CP_CLIENT_PROXY` contains method `CREATE_RESOURCE_FOR_FUNCTION`. This method returns an object of type `/IWBEP/IF_CP_RESOURCE_FUNCTION`. The interface is implemented in class`/IWBEP/CL_CP_CLIENT_PROXY`.

-   An instance of interface `/IWBEP/IF_CP_RESOURCE_FUNCTION` is returned by method `CREATE_RESOURCE_FOR_FUNCTION` of interface `/IWBEP/IF_CP_CLIENT_PROXY`.

    The interface offers the following methods:

    -   `CREATE_REQUEST`

        Returns an instance of `/IWBEP/IF_CP_REQUEST_FUNCTION`.

    -   `SET_PARAMETER`

        Used to set the values of the non-binding parameters for the function call.


    The interface is implemented in class `/IWBEP/CL_CP_RESOURCE`. Setting the non-binding parameter data for functions at the resource object enables an easy handling of composable functions once implemented. Furthermore, when invoking an OData V4 function, the non-binding parameters are part of the URI in contrast to actions where the non-binding parameters are part of the request body. This is reflected by the different handling in the client proxy.

-   An instance of interface `/IWBEP/IF_CP_REQUEST_FUNCTION` is returned by method `CREATE_REQUEST` of interface `/IWBEP/IF_CP_RESOURCE_FUNCTION`.

    The interface offers the following methods:

    -   `CHECK_EXECUTION`. This method checks the successful execution of the operation request.

    -   `EXECUTE`. This method executes operation requests and returns an instance of interface `/IWBEP/IF_CP_RESPONSE_FUNCTION`

    -   `GET_RESPONSE`. This method returns an instance of interface `/IWBEP/IF_CP_RESPONSE_FUNCTION`.


    The interface is implemented in class `/IWBEP/CL_CP_REQUEST`.

-   An instance of interface `/IWBEP/IF_CP_RESPONSE_FUNCTION` is returned by the methods `GET_RESPONSE` and `EXECUTE` of interface `/IWBEP/IF_CP_REQUEST_OPERATION`. It offers the following methods:

    -   `GET_BUSINESS_DATA`. This method returns the business data of the successful executed function request.


    The interface is implemented in class `/IWBEP/CL_CP_RESPONSE`.

-   The interface /IWBEP/IF\_CP\_RESOURCE\_FW contains the following methods:

    -   `GET_FUNCTION`. This method returns the V4 function read-only object.

    -   `TO_V2_FUNCTION_INFO`. This method returns required information \(e.g. the function name or non-binding parameter values\) for the V2 request context in order to be able to invoke the function.


    These methods are implemented in class `/IWBEP/CL_CP_RESOURCE`.

-   `/IWBEP/CL_CP_REQUEST`:

    -   Method `/IWBEP/IF_CP_REQUEST_FW~TO_V2_REQUEST_CONTEXT` sets the required information for invoking a function into the V2 request context.

    -   Method `/IWBEP/IF_CP_REQUEST_FW~TO_URI_REPRESENTATION` calculates the URI representation of functions.


-   `/IWBEP/CL_CP_RESOURCE`

    Method `TO_URI_REPRESENT_INTERNAL` calculates the URI representation of functions.

-   Interface `/IWBEP/IF_CP_ODATA_FACADE` contains method `SERIALIZE_URI_FUNCTION_SEGMENT`. This method calculates the URI segment for functions that contain the non-binding parameters and their values. It is implemented in class`/IWBEP/CL_CP_ODATA_FACADE_V2`.

-   Interface `/IWBEP/IF_CP_SERVICE_PROXY` contains method `EXECUTE_FUNCTION`. It is implemented in class `/IWBEP/CL_CP_SRV_PROXY_LOC_V2`.


> ### Sample Code:  
> ```
> "Execute Function Import "GetEdmDefault" in TEA_TEST V1
> "GET /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/GetEdmDefault?Id='0001'
> TYPES:
>   BEGIN OF ty_s_id,
>     id TYPE /iwbep/tea_employee_id,
>   END OF ty_s_id.
> 
> DATA: ls_parameter     TYPE ty_s_id,
>       ls_busi_data_act TYPE /iwbep/cl_tea_model_provider=>ty_s_edm_default,
>       lo_request       TYPE REF TO /iwbep/if_cp_request_function,
>       lo_client_proxy  TYPE REF TO /iwbep/if_cp_client_proxy.
> 
> TRY.
>     lo_client_proxy = /iwbep/CL_WEB_ODATA_CLIENT_FACTORY=>create_v2_local_proxy( VALUE #( service_id      = '/IWBEP/TEA_TEST_APPLICATION'
>                                                                                       service_version = 0001 ) ).
> 
>     ls_parameter = VALUE #( id = '0001' ).
> 
>     lo_request = lo_client_proxy->create_resource_for_function( 'GetEdmDefault'
>                                )->set_parameter( ls_parameter
>                                )->create_request( ).
> 
>     lo_request->execute( )->get_business_data( IMPORTING ea_response_data = ls_busi_data_act ).
> 
>   CATCH /iwbep/cx_gateway.
>     "Exception handling
> ENDTRY.
> 
> ```

**Constraints**

-   Only V2 function imports via local consumptions are supported

-   V2 remote consumption for functions is not supported

-   V4 functions and actions \(both bound or as imports\) are not supported

-   IF\_MATCH headers for V2 functions is not supported

-   Invoking operations as part of a $batch request is not supported

-   $expand in combination with operations is not supported


For more information, see [Preparing Access to the Remote OData Service](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/59a91c95137e4c42946d50b25dba3fd7.html?q=Preparing%20Access%20to%20the%20Remote%20OData%20Service).

