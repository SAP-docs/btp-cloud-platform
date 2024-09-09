<!-- loiob046aa34242e495c9e79a8818ba0be79 -->

# Example: Retry Design Pattern

Repeat an HTTP request automatically in ABAP.

Using this feature, you can repeat a request automatically up to 3 times, as long as the status code from the response has an appropriate value.

You can provide a set of response codes upon which the request is supposed to be repeated, if the corresponding response returns a status code from this set.

If you do not provide this set of codes, a default set is drawn depending on the idempotence of a request. You can control the idempotence of a request via parameter.

The default set for a non-idempotent request is 408, 429 and 503. For an idempotent request, the default set is 308, 429, 500, 502, 503, 504, 507, 509.

All other parameters correspond to the known `execute` method.

> ### Sample Code:  
> ```abap
> DATA: http_client           TYPE REF TO if_web_http_client,
>       lo_response           TYPE REF TO if_web_http_response,
>       lt_retry_status_codes  TYPE http_status_codes,
>       iv_url                TYPE string.
> 
> iv_url = 'https://hostfoobar:port/foo/bar'. "Enter a correct url
> 
> TRY.
>     http_client = cl_web_http_client_manager=>create_by_http_destination( i_destination = cl_http_destination_provider=>create_by_url( i_url = iv_url ) ).
>     
>     "select for which numbers the execution should be retried
>     lt_retry_status_codes = VALUE http_status_codes( ( '111' )
>                                                      ( '222' )
>                                                      ( '333' ) ).
> 
>     lo_response = http_client->retry_execute(
>                     i_retry_status_codes = lt_retry_status_codes      " Table for HTTP status codes for whose entries retry is done
>                     i_method             = if_web_http_client=>post " HTTP Method (GET, POST etc.)
>                     i_idempotent_method  = abap_true                  " Idempotent request method
>                   ).
> 
>     DATA(status) = lo_response->get_status( ).
>     IF status-code NE 200.
>       "Error handling here
>     ENDIF.
> 
>   CATCH cx_web_http_client_error cx_http_dest_provider_error.
>      " handle exception here
> ENDTRY. has occurred!'.
> ENDTRY.
> 
> ```

