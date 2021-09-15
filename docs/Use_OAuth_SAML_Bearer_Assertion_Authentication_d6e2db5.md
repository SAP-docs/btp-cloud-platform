<!-- loiod6e2db57cde344faa7f0a496c2d2257c -->

# Use OAuth SAML Bearer Assertion Authentication



<a name="loiod6e2db57cde344faa7f0a496c2d2257c__prereq_hkg_zlt_n2b"/>

## Prerequisites

-   You have set up the communication arrangement for scenario `SAP_COM_0276`. See [Create a Destination](Create_a_Destination_3fa7934.md).

-   You have an existing destination in your destination service instance.
-   You have created an HTTP service or OData service. See [Tutorial: Create an HTTP Service](https://developers.sap.com/tutorials/abap-environment-create-http-service.html), [Creating an OData Service](https://help.sap.com/viewer/c0d02c4330c34b3abca88bdd57eaccfc/Cloud/en-US/2b08207efb954644b20f3587f39a77a6.html) and [Video Tutorial: Create OData Service](https://www.youtube.com/watch?v=7rJxhjy2LKg&index=5&list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr&t=0s).



<a name="loiod6e2db57cde344faa7f0a496c2d2257c__steps_dsc_hmt_n2b"/>

## Procedure

1.  In Eclipse, navigate either to your HTTP service or your OData service implementation.

2.  Create a destination object using class `cl_http_destination_provider` and method `create_by_cloud_destination` with the following parameters:

    -   **i\_service\_instance\_name**: the value of the service instance name property of the communication arrangement

    -   **i\_name**: the name of the destination
    -   \[Optional\] **i\_authn\_mode**: `if_a4c_cp_service=>user_propagation`

        > ### Note:  
        > This parameter is used to call the destination service with `OAuth 2.0 SAML Bearer Assertion Flow`. By default, it is set to `user_propagation`.

3.  Create an HTTP client object with class `cl_web_http_client_manager` and method `create_by_http_destination` providing the destination object you have created as a parameter.

4.  Execute the request using method `execute` on the HTTP client object.


