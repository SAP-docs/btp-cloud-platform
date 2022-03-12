<!-- loio4e3cc67a25064958a8661f1cd614d329 -->

# Example: HTTP Multipart Request

Using multipart requests for HTTP communication from the ABAP environment.

The code examples below show an **HTTP multipart request**:



<a name="loio4e3cc67a25064958a8661f1cd614d329__section_afy_k5l_mnb"/>

## Client Side

> ### Sample Code:  
> ```abap
> DATA: http_client TYPE REF TO if_web_http_client,
>       lo_response TYPE REF TO if_web_http_response,
>       iv_url TYPE string.
>  
> iv_url = 'https://...'. "Enter a correct url
>  
>  
> TRY.
>   http_client = cl_web_http_client_manager=>create_by_http_destination( i_destination = cl_http_destination_provider=>create_by_url( i_url = iv_url ) ).
>  
>   DATA(lo_request) = http_client->get_http_request(   ).
>   lo_request->set_header_field( i_name =  'Content-type'
>                                 i_value = 'multipart/mixed' ).
>  
>   DATA(part_1) = lo_request->add_multipart(  ).
>   part_1->set_header_field( i_name =  'Content-type'
>                             i_value = 'text/html; charset=UTF-8' ).
>  
>   part_1->set_text( 'This is part one.' ).
>  
>   DATA(part_2) = lo_request->add_multipart(  ).
>   part_2->set_header_field( i_name =  'Content-type'
>                             i_value = 'text/html; charset=UTF-8' ).
>   part_2->set_text( 'This is part two.' ).
>  
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



<a name="loio4e3cc67a25064958a8661f1cd614d329__section_fwk_45l_mnb"/>

## Server Side

> ### Sample Code:  
> ```abap
> CLASS ZCL_TEST_MULTIPART IMPLEMENTATION.
>   method IF_HTTP_SERVICE_EXTENSION~HANDLE_REQUEST.
>     DATA: answer TYPE string,
>           num_part TYPE i.
>  
>     num_part = request->num_multiparts(   ).
>     IF num_part = 0.
>       answer = '<html><body>No multipart found in request!!</body></html>'.
>       response->set_text(  answer ).
>     ELSE.
>       DO num_part TIMES.
>         DATA(lo_part_request) = request->get_multipart( index = sy-index ).
>         IF lo_part_request IS BOUND.
>           "Do something here with this part.
>         ENDIF.
>       ENDDO.
>     ENDIF.
>   endmethod.
> ENDCLASS.
> 
> ```

