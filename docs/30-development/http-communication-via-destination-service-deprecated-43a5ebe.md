<!-- loio43a5ebed034547ad8aa85250f85098a2 -->

# HTTP Communication via Destination Service \(Deprecated\)



<a name="loio43a5ebed034547ad8aa85250f85098a2__section_nl2_2zx_qsb"/>

## Context

Use the destination service in SAP BTP to store destination information that can be reused by applications deployed in one of the BTP environments.

> ### Note:  
> You can use the destination service. However, this approach is deprecated. We recommend using the communication arrangement approach instead. See [HTTP Communication via Communication Arrangements](http-communication-via-communication-arrangements-3047582.md) for more information.

You've the following options to consume a destination service:

-   Dynamic by using a communication arrangement and a communication system

-   Static by using the method `create_by_cloud_destination` in the code



<a name="loio43a5ebed034547ad8aa85250f85098a2__section_uy2_nzx_qsb"/>

## Procedure

When using `create_by_cloud_destination`, proceed as follows:

Create a destination object using class `cl_http_destination_provider` and method `create_by_cloud_destination` with the following parameters:

-   `i_name`: the name of the destination

-   Optional: `i_service_instance_name`: Typically, you use the destinations of the subaccount in which the ABAP instance resides or, in case of a SaaS solution based on the ABAP environment, the destinations of the consumer subaccount. However, you can add more destinations using your own destination service instance and communication scenario`SAP_COM_0276`, for example, to achieve separation of concerns \(see also [Create a Destination](create-a-destination-3fa7934.md)\). In this case, specify the value of the service instance name property of the communication arrangement for `SAP_COM_0276`.
-   `i_authn_mode`: Set the value of this parameter according to the authentication method configured in your destination. If the authentication method uses user propagation, the value is `if_a4c_cp_service=>user_propagation`, if it doesn't, set `if_a4c_cp_service=>service_specific`:

    **Authentication Methods**


    <table>
    <tr>
    <th valign="top">

    Value
    
    </th>
    <th valign="top">

    Proxy Type *Internet*
    
    </th>
    <th valign="top">

    Proxy Type *OnPremise*
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `if_a4c_cp_service=>user_propagation`
    
    </td>
    <td valign="top">
    
    -   [OAuth User Token Exchange Authentication](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/oauth-user-token-exchange-authentication?version=Cloud)

    -   [OAuth SAML Bearer Assertion Authentication](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/oauth-saml-bearer-assertion-authentication?version=Cloud)

    -   [OAuth JWT Bearer Authentication](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/oauth-jwt-bearer-authentication?version=Cloud)



    
    </td>
    <td valign="top">
    
    [Principal Propagation SSO Authentication for HTTP](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/principal-propagation-sso-authentication-for-http?version=Cloud)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `if_a4c_cp_service=>service_specific`
    
    </td>
    <td valign="top">
    
    -   No Authentication

    -   Basic Authentication

    -   [Client Authentication Types for HTTP Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/client-authentication-types-for-http-destinations?version=Cloud)

    -   [OAuth Client Credentials Authentication](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/oauth-client-credentials-authentication?version=Cloud)

    -   [OAuth Password Authentication](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/oauth-password-authentication?version=Cloud)



    
    </td>
    <td valign="top">
    
    -   No Authentication

    -   Basic Authentication



    
    </td>
    </tr>
    </table>
    

Other authentication methods are currently not supported by the SAP BTP ABAP environment.



## Example

The actual processing of an HTTP request and its response is shown in the following code example:

> ### Sample Code:  
> ```abap
> DATA lo_http_destination TYPE REF TO if_http_destination.
> DATA lo_http_client     TYPE REF TO if_web_http_client.
> DATA lo_http_response   TYPE REF TO if_web_http_response.
>  
>     TRY.
>         " create HTTP destination by cloud destination
>         lo_http_destination = cl_http_destination_provider=>create_by_cloud_destination( i_name = 'DestinationName' i_authn_mode = if_a4c_cp_service=>service_specific ).
>  
>         " create HTTP client by HTTP destination
>         lo_http_client = cl_web_http_client_manager=>create_by_http_destination( lo_http_destination ).
>  
>         " adding header fields
>         lo_http_client->get_http_request( )->set_header_fields( VALUE #( ( name = if_web_http_header=>content_type value = if_web_http_header=>accept_application_json )
>                                                                          ( name = if_web_http_header=>accept       value = if_web_http_header=>accept_application_json ) ) ).
>                                                                           
>  
>         " execute HTTP GET-request and store response
>         lo_http_response = lo_http_client->execute( if_web_http_client=>get ).
>  
>         " print response text to console
>         DATA(ls_status) = lo_http_response->get_status( ).
>         out->write( |Response is: { ls_status-code } { ls_status-reason }.| ).
>         out->write( lo_http_response->get_text( ) ).
>  
>       CATCH cx_http_dest_provider_error cx_web_http_client_error INTO DATA(lx_error).
>         " display error details
>         out->write( lx_error->get_text( ) ).
>     ENDTRY.
> ```



<a name="loio43a5ebed034547ad8aa85250f85098a2__section_lwx_ycy_qsb"/>

## Test Your Outbound Call

To test your outbound call, configure an HTTP destination as described in [Create HTTP Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/create-http-destinations?version=Cloud).

**Authentication Methods**

-   Only the authentication methods listed in table *Authentication Methods* are available.
-   If you're using Client Certificate Authentication as authentication method, activate *Use client provided certificate*. This flag is only visible if the URL field contains a URL string starting with *https://...* .
-   For proxy type `Internet` and the use of authentication type `client certificate`, you must upload the X.509 client certificate in P12 format on the client side in the SAP BTP ABAP environment using the Maintain Client Certificates application. For more information, see [Maintain Client Certificates](../50-administration-and-ops/maintain-client-certificates-7f6a8fb.md). Uploading the client certificate via destination service isn't supported.
-   The use of `if_a4c_cp_service=>user_propagation` isn't supported in the ADT class runner. It can only be tested when a business user context is available, for example, during processing of OData services or HTTP services.

**Related Information**  


[Destination Service](communication-management-5b8ff39.md#loioeeb0ec2318fb4dda87830a09ac7a02fa "Using the SAP destination service, you can retrieve and store technical information about the target resource (destination) that you want to connect with your application to a remote service or a system.")

