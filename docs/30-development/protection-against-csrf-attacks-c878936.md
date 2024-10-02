<!-- loioc8789362de5f47fcacdbfb84dcdc54ee -->

# Protection Against CSRF Attacks

Protect against cross-side request forgery \(CSRF\) attacks by enabling CSRF token handling in the HTTP service.

To protect an HTTP service against CSRF attacks, you must implement the method `HANDLE_REQUEST` in the interface `IF_HTTP_SERVICE_EXTENSION` of the service. If this method is implemented, within a session each caller of the service must :

-   Request a CSRF token by setting the header `X-CSRF-Token` with value `fetch`.
-   Provide the specific CSRF token with each request of this session in header `X-CSRF-Token`, which is validated by the server.

The method `HANDLE_REQUEST`:

-   Provides a CSRF token and adds it to the HTTP response, if the value `fetch` is present in the corresponding header field.

-   Validates the CSRF token, if it is present in the header field of the request.

-   Returns an error with the HTTP response, if validation fails.


> ### Caution:  
> If you have implemented the method `IF_HTTP_SERVICE_EXTENSION` for an HTTP service, all calls that do not request a CSRF token and provide it in the respective session are rejected. Only clients enabled for CSRF token handling can perform successful calls to the service in this case.

**Example**

The code below shows an example for implementing the method `HANDLE_REQUEST` of the interface `IF_HTTP_SERVICE_EXTENSION` to enable correct CSRF token handling:

> ### Sample Code:  
> ```
> METHOD if_http_service_extension~handle_request.
>   DATA(lv_valid) = cl_http_service_utility=>handle_csrf(
> 	 EXPORTING
> 	   request = request
> 	   response = response
>   ).
>   CHECK lv_valid = abap_true.
>   //Start the implementation of the HTTP service 
>   //Start the application logic
> ENDMETHOD.
> 
> ```

