<!-- loio28de1b09aec84041a53e50c0af105dec -->

# Action and Functions

Execute an OData request to invoke an operation \(i.e. an action or function\) via the OData Client Proxy.



<a name="loio28de1b09aec84041a53e50c0af105dec__section_fh2_by1_5qb"/>

## OData Specification

**OData V2**

A service operation is represented by a function import and returns one of the following:

-   Primitive type

-   Collection of primitive types

-   A single ComplexType instance

-   Collection of ComplexType instances

-   A single EntityType instance


> ### Note:  
> The corresponding function import may have side effects and can be invoked by any pre-defined HTTP method.

For more information, see the [Open Data Protocol](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata/2b686a1a-9e1f-456f-80ff-072a010fc278).

**OData V4**

Function

A function is an operation exposed by an OData service that does not have side effects. Functions must return data and can be further composed with additional path segments. Functions are invoked using HTTP method `GET`.

Action

An action is an operation exposed by an OData service that may have side effects. Actions may return data but must not be further composed with additional path segments. Actions are invoked using HTTP method `POST`.

Operation

Functions and actions are considered operations. Operations are either bound to a resource \(e.g. an entity type\), enabling them to be called as members of an instance of that type, or unbound, in which case they are called as static operations \(using so called “action imports” or “function imports”, since a static – i.e. unbound – operation cannot be called directly\).

For more information, see [OData Version 4.01. Part1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).



<a name="loio28de1b09aec84041a53e50c0af105dec__section_lnv_mz1_5qb"/>

## Example Requests

**V4 Function Import**

**GetEmployeeByManagerId** including non-binding parameter “ManagerId”

GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea\_busi/0001/GetEmployeeByManagerID\(ManagerID='0001'\)

**V4 Bound Action**

**AcChangeTeamOfEmployee** including non-binding parameter “TeamId”

POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea\_busi/0001/EMPLOYEES\('2'\)/SAP\_\_self.AcChangeTeamOfEmployee

```

{
  "TeamID" : "TEAM_02"
}

```

**V2 Function** 

**SetEmployeeSalary** including non-binding parameter “Id” and “Amount”

PUT /sap/opu/odata/IWBEP/TEA\_TEST\_APPLICATION/SetEmployeeSalary?Id='0001'&Amount=200



<a name="loio28de1b09aec84041a53e50c0af105dec__section_vvk_d1b_5qb"/>

## Process

**Overview**

Starting point for invoking an operation is the corresponding operation resource, which is directly created on the OData Client Proxy instance.

The resource instance can be used to create a request instance; the latter can directly execute the request.

Finally, the response instance – which can be used to retrieve the response business data of the successfully executed request – can be fetched from the request instance.

**Example**

You want to invoke the *PromoteEmployee* V2 function with the non-binding \(i.e. input\) parameter “Id=’0001'”:

POST /sap/opu/odata/IWBEP/TEA\_TEST\_APPLICATION/PromoteEmployee?Id='0001'

1.  Creation of the function resource. “PROMOTE\_EMPLOYEE” is the internal name of function “PromoteEmployee”:

    > ### Sample Code:  
    > ```
    > 
    > DATA:
    > lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy,
    > lo_function_resource type ref to /iwbep/if_cp_resource_function.
    > 
    > lo_function_resource = lo_client_proxy->create_resource_for_function( 'PROMOTE_EMPLOYEE')
    > ```

2.  Set the non-binding \(i.e. input\) parameter. This can be done on the function resource, using method `SET_PARAMETER`:

    > ### Sample Code:  
    > ```
    > 
    > TYPES:
    >   BEGIN OF ty_s_id,
    >     id TYPE /iwbep/tea_employee_id,
    >   END OF ty_s_id.
    > DATA:
    > ls_parameter     TYPE ty_s_id.
    > ls_parameter = VALUE #(id = '0001' ).
    > 
    > lo_function_resource->set_parameter( ls_parameter ).
    > 
    > ```

3.  Create a function request:

    > ### Sample Code:  
    > ```
    > 
    > DATA:
    > lo_function_request TYPE REF TO /iwbep/if_cp_request_function.
    > 
    > lo_function_request = lo_function_resource->create_request( ).
    > 
    > ```

4.  Set the corresponding HTTP method to invoke the function \(in thisexample, it would be `POST`\). This can be done using method `SET_HTTP_METHOD` or directly in the `EXECUTE` method. You can use the given constants in `GCS_HTTP_METHOD` of interface `/IWBEP/IF_CP_REQUEST_FUNCTION`:

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
    > lo_function_response = lo_function_request->execute( /iwbep/if_cp_request_function=>gcs_http_method-post ).
    > 
    > ```

    > ### Note:  
    > Setting the HTTP method is only allowed for OData V2 requests. For OData V4, functions must always be called via `GET`.
    > 
    > You do not need to set the HTTP method if the function is called via`GET`.

5.  Set the if-match header to provide an \(weak\) ETag \(if needed for this request\).

    If the corresponding request header was, e.g. if-match: W/"2407", the required input for SET\_IF\_MATCH was ‘2407’:

    > ### Sample Code:  
    > ```
    > 
    > lo_function_request->set_if_match( ‘2407’ ).
    > ```

    > ### Note:  
    > Only remote consumption supports the if-match header.

6.  Fetch the business data from the response object \(if the corresponding function does return business data\):

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
    > When using the local client proxy, the business data you enter will not be converted for inbound processing; the data provider receives exactly the data you entered in the request. Furthermore, the business data received from the response will also not be re-converted for outbound processing.




<a name="loio28de1b09aec84041a53e50c0af105dec__section_ytg_1db_5qb"/>

## Constraints

-   If-match header is only supported for remote consumption

-   is not supported

-   If the return type of a V2 function is an entity type and this entity type is used by more than one entity sets, the V2 request context will only contain the \(edm\) name of the first entity set with the underlying entity type. A precise mapping is currently not possible.

-   The following is not supported:

    -   V4 Bound Functions

    -   V4 Bound Actions

    -   V4 Action Imports

-   For remote consumption, this can be handled in the proxy model by setting the correct entity set using method `/IWBEP/IF_V4_MED_FUNC_IMP → SET_ENTITY_SET_NAME`.


