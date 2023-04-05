<!-- loio5a00c94884404dc8a6f530cab4e7b136 -->

# Example: Enable Path Prefix

Enable a path prefix for HTTP calls in ABAP.

Interface `IF_WEB_HTTP_CLIENT` provides a method `enable_path_prefix` to extend a URL set by the method `set_uri_path`.

Calling only `set_uri_path` overwrites the URL used to instanciate the client:

> ### Sample Code:  
> ```abap
> DATA: http_client TYPE REF TO if_web_http_client,
>       lo_response TYPE REF TO if_web_http_response,
>       iv_url TYPE string.
>  
> iv_url = 'https://hostfoobar:port/foo1/bar1'. "Enter a correct url
>  
> TRY.
>   http_client = cl_web_http_client_manager=>create_by_http_destination( i_destination = cl_http_destination_provider=>create_by_url( i_url = iv_url ) ).
>  
>   DATA(lo_request) = http_client->get_http_request(   ).
>   
>   lo_request->set_uri_path( EXPORTING i_uri_path = '/foo2/bar2' ).
> 
>   "the request will be send to /foo2/bar2
>   lo_response = http_client->execute( if_web_http_client=>post ).
>  
>   DATA(status) = lo_response->get_status( ).
>   IF status-code NE 200.
>     "Error handling here
>   ENDIF.
>  
> CATCH cx_web_http_client_error cx_http_dest_provider_error.
>   WRITE 'An exception has occurrred!'.
> ENDTRY.
> 
> ```

If you call the method `enable_path_prefix` before calling `set_uri_path`, the path passed by `set_uri_path` is appended to the initial path:

> ### Sample Code:  
> ```abap
> DATA: http_client TYPE REF TO if_web_http_client,
>       lo_response TYPE REF TO if_web_http_response,
>       iv_url TYPE string.
>  
> iv_url = 'https://hostfoobar:port/foo1/bar1'. "Enter a correct url
>  
> TRY.
>   http_client = cl_web_http_client_manager=>create_by_http_destination( i_destination = cl_http_destination_provider=>create_by_url( i_url = iv_url ) ).
>  
>   DATA(lo_request) = http_client->get_http_request(   ).
>   
>   http_client->enable_path_prefix( ).
>   lo_request->set_uri_path( EXPORTING i_uri_path = '/foo2/bar2' ).
> 
>   "the request will be send to /foo1/bar1/foo2/bar2
>   lo_response = http_client->execute( if_web_http_client=>post ).
>  
>   DATA(status) = lo_response->get_status( ).
>   IF status-code NE 200.
>     "Error handling here
>   ENDIF.
>  
> CATCH cx_web_http_client_error cx_http_dest_provider_error.
>   WRITE 'An exception has occurrred!'.
> ENDTRY.
> 
> ```

