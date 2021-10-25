<!-- loio7c69fb67a82949c39ba7882cf7b0b851 -->

# Remote Client Proxy

The remote proxy is used when an OData service is consumed remotely using a HTTP request. The remote proxy does the following:

-   It serializes the request to

    -   URL

    -   Payload

    -   HTTP-header \(such as eTag\)


-   It serializes the response to

    -   Business data \(such as an ABAP data container\)

    -   Status information


    *Header*

    You can set a header to the http\_client object using parameter `io_http_client` in class `/IWBEP/CL_CP_CLIENT_PROXY_FACT~CREATE_V2_REMOTE_PROXY()` or class `/IWBEP/CL_CP_CLIENT_PROXY_FACT~CREATE_V4_REMOTE_PROXY()` with `if_http_client-> request-> set_header_field()`:

    > ### Sample Code:  
    > ```
    > CLASS-METHODS create_v2_remote_proxy
    >       IMPORTING
    >         !is_proxy_model_key       TYPE /iwbep/if_cp_runtime_types=>ty_s_proxy_model_key
    >         !io_http_client           TYPE REF TO if_http_client
    >         !iv_relative_service_root TYPE string
    >       RETURNING
    >         VALUE(ro_client_proxy)    TYPE REF TO /iwbep/if_cp_client_proxy
    >       RAISING
    >         /iwbep/cx_gateway .
    >     "! <p class="shorttext synchronized" lang="en">Create client proxy for remote OData V4 service consumption</p>
    >     "!
    >     "! <h1>Description</h1>
    >     "! <p>Create client proxy for remote OData V4 service consumption</p>
    >     "!
    >     "! <p>Concatenated HTTP destination and <em>iv_relative_service_root</em> must point to the service document.
    >     "! Example for <em>iv_relative_service_root: /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/</em></p>
    >     "!
    >     "! @parameter is_proxy_model_key       | <p class="shorttext synchronized" lang="en">Proxy model key</p>
    >     "! @parameter iv_relative_service_root | <p class="shorttext synchronized" lang="en">Relative service path</p>
    >     "! @parameter io_http_client           | <p class="shorttext synchronized" lang="en">Configured IF_HTTP_CLIENT object</p>
    >     "! @parameter ro_client_proxy          | <p class="shorttext synchronized" lang="en">Client Proxy</p>
    >     "! @raising   /iwbep/cx_gateway        | <p class="shorttext synchronized" lang="en">SAP Gateway Exception</p>
    > ```

    *Exceptions*

    The following errors can be part of the request:

    -   You entered an invalid value to the request.

    -   Your request has a wrong navigation, e.g. you ask for the name of all employees beginning with a "B" and navigate to the department and not to the list of employees.


    If this is the case, the error handling executes the following exception:

    > ### Sample Code:  
    > ```
    > CATCH /iwbep/cx_gateway INTO DATA(lx_gateway).
    >         " Error Handling
    > ```

    If you enter an invalid value and the client proxy reports an error, the following exception is executed:

    > ### Sample Code:  
    > ```
    > CATCH /iwbep/cx_cp_remote into data(lx_remote)
    >       " Handle remote Exception
    >       " It contains details about the problems of your http(s) connection)
    > ```

    The error response contains the following information:

    -   HTTP Status Code

    -   HTTP Status Reason Message

    -   OData Error Details

    -   HTTP Client Error Details


    > ### Note:  
    > The exception is also executed, wenn the HTTP Status Code is 4xx or 5xx.

    > ### Example:  
    > SAP BTP, ABAP environment
    > 
    > ```
    > 
    > DATA:	lt_employee      TYPE STANDARD TABLE OF /iwbep/s_tea_employee,
    >           lt_employee_a    TYPE STANDARD TABLE OF /iwbep/s_tea_employee_a (abstract entity from the service consumption model). If etag is used in the consumption model,
    >           the response has an `etag__etag` field.
    >           lo_client_proxy  TYPE REF TO /iwbep/if_cp_client_proxy,
    >           lo_read_request  TYPE REF TO /iwbep/if_cp_request_read_list,
    >           lo_read_response TYPE REF TO /iwbep/if_cp_response_read_lst,
    >           lo_http_client   TYPE REF TO if_http_client. 
    > 
    > 	TRY.
    >         " Using SM59 destination for HTTP client object
    >         cl_web_http_client_manager=>create_by_http_destination (
    >           EXPORTING
    >             destination              = '<DESTINATION>'
    >           IMPORTING
    >             client                   = lo_http_client
    >           EXCEPTIONS
    > *            argument_not_found       = 1
    > *            destination_not_found    = 2
    > *            destination_no_authority = 3
    > *            plugin_not_active        = 4
    > *            internal_error           = 5
    >             OTHERS                   = 6 ).
    > 
    >         CHECK sy-subrc = 0.
    > 
    >         " Create Proxy
    >          lo_client_proxy = CL_WEB_ODATA_CLIENT_FACTORY=>create_v2_remote_proxy( VALUE #(lv_service_definition_name
    >                                                                                         io_http_client
    >                                                                                         iv_relative_service_root) ).
    >         " Create read request on entity set 'Employees'
    >         lo_read_request = lo_client_proxy->create_resource_for_entity_set( 'Employees' )->create_request_for_read( ).
    >         lo_read_response = lo_read_request->execute( ).
    > 
    >         " Retrieve the business data
    >         lo_read_response->get_business_data( IMPORTING et_business_data = lt_employee ). employee_a is an abstract entity of the abstract entity of /iwbep/s_tea_employee from service consumption model
    > 
    >         CATCH /iwbep/cx_cp_remote into data(lx_remote)
    >         " Handle remote Exception
    >         " It contains details about the problems of your http(s) connection)
    > 
    >         CATCH /iwbep/cx_gateway INTO DATA(lx_gateway).
    >         " Error Handling
    >     ENDTRY.
    > 
    > ```


> ### Note:  
> You can perfom a virus scan for remote client proxy V2/V4 using class /IWBEP/CL\_V4\_VIRUS\_SCANNER and method if\_vscan\_instance.

