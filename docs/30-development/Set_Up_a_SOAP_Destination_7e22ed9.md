<!-- loio7e22ed9979a34a61afdeaee7c49e3711 -->

# Set Up a SOAP Destination

Set up SOAP connectivity for the ABAP environment by configuring an HTTP destination and additional, SOAP-specific parameters.

To configure a SOAP-specific destination, create an HTTP destination as described in [Set Up an HTTP Destination](Set_Up_an_HTTP_Destination_3884bc3.md).

You can set more web service properties under *Additional Properties*:

-   `ws.soapVersion`: SOAP version
-   `ws.maxWaitTime`: Maximum wait time for the consumer \(in seconds\)
-   `ws.compressMessage`: Enables compression of the message.
-   `ws.soapAction.<operationName>`: Sets the SOAP action for a given operation with name <operationName\>.

Instead of settings these properties in the service destination, you can set them programmatically:

-   `set_soap_version( )`: Sets the SOAP version. Valid values for the SOAP version are provided by the constants `if_soap_destination=>soap_version_11` and `if_soap_destination=>soap_version_12`
-   `set_max_wait_time( )`: Sets the maximum wait time for the consumer \(in seconds\).
-   `set_compress_message( )`: Enables compression of messages if parameter `i_compress_message` is set to true. Disables compression if the parameter is set to false.
-   `set_soap_action( )`: Sets the SOAP action for a given operation. Parameters are the name of the operation and the value of the SOAP action.
-   `set_url( )`: Sets the URL of the endpoint
-   set\_basic\_authentication\( \): Sets the authentication method to basic authentication, and sets user and password.
-   `use_client_certificate( )`: Sets the authentication method to client certificate authentication. The default client certificate is used.

> ### Note:  
> For the approach via communication arrangement, you can't set the properties programmatically by using the setter methods.
> 
> The properties such as URL and the authentication method are defined in the communication arrangement.

