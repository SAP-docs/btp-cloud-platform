<!-- loiocef1ada754154d11b5701ab60e6ab412 -->

# Enable HTTP Communication in Your ABAP Code

Use the HTTP client to enable HTTP communication from SAP BTP, ABAP environment.



<a name="loiocef1ada754154d11b5701ab60e6ab412__section_p55_pmc_1hb"/>

## Context

The HTTP client is a wrapper of the ABAP HTTP client \(which is not supported by SAP BTP, ABAP environment\).

It is used for communication with S/4HANA Cloud, on-premise systems, or any other HTTP service exposed to the Internet.

The HTTP client provides integration with, for example, the Destination service residing on SAP BTP, Cloud Foundry environment.

See also [Consuming the Destination Service](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html).

As there are no SM59-managed destinations \(destinations created via SAP transaction SM59\) available in the ABAP environment, the decoupling of designtime and runtime is done via generic HTTP destinations that you can create using a plain URL or a Cloud Foundry destination:

> ### Sample Code:  
> ```lang-abap
> DATA(lo_url_destination) = cl_http_destination_provider=>create_by_url( 'https://foo.bar' ).
>  
> DATA(lo_cloud_destination) = cl_http_destination_provider=>create_by_cloud_destination(
>                                i_name                  = 'DestinationName'
>                                i_authn_mode = if_a4c_cp_service=>service_specific
>                              ).
> 
> ```

> ### Note:  
> Using `create_by_url` is only suitable for public services, because credentials should be stored in the Destination service \(`create_by_cloud_destination`\).



Alternatively, you can use the method `create_by_comm_arrangement`.

Using `create_by_comm_arrangement`, the information is passed via 3 parameters:

-   `comm_scenario` \(mandatory\): ID of the developed communication scenario.
-   `comm_system_id` \(optional\): ID of the configured communication system.
-   `service_id` \(optional\): ID of the developed outbound service.

As a prerequisite, you must have installed the respective communication scenario.

The method `create_by_comm_arrangement` is only supported for customer-developed scenarios. The supported authentication methods depend on whether you are using the destination service or the communication system to store the target information.

> ### Sample Code:  
> ```lang-abap
> DATA(lo_destination) = cl_http_destination_provider=>create_by_comm_arrangement( 
> comm_scenario  =  'Z_MY_SCENARIO_ID' 
> comm_system_id = 'Z_MY_SYSTEM_ID' 
> service_id = 'Z_MY_SERVICE_ID'
> ).
> DATA(lo_http_client) = cl_web_http_client_manager=>create_by_http_destination( lo_destination ).
> DATA(lo_response) = lo_http_client->execute( if_web_http_client=>get ).
> 
> ```



<a name="loiocef1ada754154d11b5701ab60e6ab412__section_b2w_pmc_1hb"/>

## Use

When using `create_by_cloud_destination`, proceed as follows:

Create a destination object using class `cl_http_destination_provider` and method `create_by_cloud_destination` with the following parameters:

-   `i_name`: the name of the destination.
-   `i_authn_mode`: Set the value of this parameter according to the authentication method configured in your destination. If the authentication method uses user propagation, the value is `if_a4c_cp_service=>user_propagation`, if it doesn't, set `if_a4c_cp_service=>service_specific`:


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

    -   [OAuth User Token Exchange Authentication](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e3c333f9de6245fca326993f2397c13a.html)

    -   [Oauth SAML Bearer Assertion Authentication](https://help.sap.com/viewer/DRAFT/cca91383641e40ffbe03bdc78f00f681/Validation/en-US/c69ea6aacd714ad2ae8ceb5fc3ceea56.html)



    
    </td>
    <td valign="top">

     [Principal Propagation Authentication](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/73194cc419894433994c5f0444b4c6a1.html) 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `if_a4c_cp_service=>service_specific`


    
    </td>
    <td valign="top">

    -   No Authentication

    -   Basic Authentication

    -   [OAuth Client Credentials Authentication](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/4e1d742a3d45472d83b411e141729795.html)



    
    </td>
    <td valign="top">

    -   No Authentication
    -   Basic Authentication


    
    </td>
    </tr>
    </table>
    
    Other Logon-Methods are currently not supported by the ABAP environment.

    Find more information on using this parameter for different authentication types in section *Related Information* below.

    > ### Note:  
    > The use of `if_a4c_cp_service=>user_propagation` is not supported in the ADT class runner. In can only be tested when a business user context is available, for example, during processing of OData services or HTTP services.


 

-   \(Optional\) `i_service_instance_name`: Typically, you will be using the destinations of the subaccount in which the ABAP instance resides. However, you can add more destinations using your own Destination service instance and communication scenario SAP\_COM\_0276, for example, to achieve separation of concerns \(see also [Create a Destination](create-a-destination-3fa7934.md)\). In that case, specify the value of the service instance name property of the communication arrangement for SAP\_COM\_0276.

The actual **processing of an HTTP request** and its response is shown in the following code example:

> ### Sample Code:  
> ```lang-abap
> DATA lo_http_destination TYPE REF TO if_http_destination.
>     DATA lo_http_client      TYPE REF TO if_web_http_client.
>     DATA lo_http_response    TYPE REF TO if_web_http_response.
> 
>     TRY.
>         " Create HTTP Destination by URL
>         lo_http_destination = cl_http_destination_provider=>create_by_cloud_destination( i_name = 'DestinationName' i_authn_mode = if_a4c_cp_service=>service_specific).
> 
>         " Create HTTP Client by HTTP Destination
>         lo_http_client = cl_web_http_client_manager=>create_by_http_destination( lo_http_destination ).
> 
>         " Adding Header Fields
>         lo_http_client->get_http_request( )->set_header_fields( VALUE #( ( name = if_web_http_header=>content_type value = if_web_http_header=>accept_application_json )
>                                                                          ( name = if_web_http_header=>accept       value = if_web_http_header=>accept_application_json )
>                                                                          ( name = 'APIKey'                         value = '<API_KEY>' ) ) ).
> 
>         " Execute HTTP GET-Request and store Response
>         lo_http_response = lo_http_client->execute( if_web_http_client=>get ).
> 
>         " Print Response Text to Console
>         DATA(ls_status) = lo_http_response->get_status( ).
>         out->write( |Response is: { ls_status-code } { ls_status-reason }.| ).
>         out->write( lo_http_response->get_text( ) ).
> 
>       CATCH cx_http_dest_provider_error cx_web_http_client_error INTO DATA(lx_error).
>         " Display Error Details
>         out->write( lx_error->get_text( ) ).
>     ENDTRY.
> 
> ```



<a name="loiocef1ada754154d11b5701ab60e6ab412__section_vb2_2nn_5mb"/>

## Related Information

[Use OAuth Client Credentials Authentication](use-oauth-client-credentials-authentication-60bfb24.md)

[Use OAuth SAML Bearer Assertion Authentication](use-oauth-saml-bearer-assertion-authentication-d6e2db5.md)

[Example: HTTP Multipart Request](example-http-multipart-request-4e3cc67.md)

[Connectivity in the Cloud Foundry Environment](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/34010ace6ac84574a4ad02f5055d3597.html)

