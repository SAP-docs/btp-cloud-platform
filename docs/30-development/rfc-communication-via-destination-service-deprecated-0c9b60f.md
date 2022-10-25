<!-- loio0c9b60f19d1644dabd4e89ebff79328d -->

# RFC Communication via Destination Service \(Deprecated\)



<a name="loio0c9b60f19d1644dabd4e89ebff79328d__section_ewg_mpz_qsb"/>

## Context

Use the destination service in SAP BTP to store destination information that can be reused by SAP BTP app services.

> ### Note:  
> You can use the destination service. However, this approach is deprecated. We recommend using the communication arrangement approach instead. See [RFC Communication via Communication Arrangements](rfc-communication-via-communication-arrangements-fadc4a2.md) for more information.

You've the following options to consume a destination service:

-   Dynamic by using a communication arrangement and a communication system
-   Static by using the method `create_by_cloud_destination` in the code



<a name="loio0c9b60f19d1644dabd4e89ebff79328d__section_nsw_yqz_qsb"/>

## Prerequisites

If you want to call other systems via SRVC, you must have created an SRVC of type RFC as described in [Generating Proxies for Remote Function Call \(RFC\)](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/32812d950d3848359ce391dae477f201.html).



<a name="loio0c9b60f19d1644dabd4e89ebff79328d__section_esz_brz_qsb"/>

## Procedure

When using `create_by_cloud_destination`, proceed as follows:

Create a destination object using class `cl_http_destination_provider` and method `create_by_cloud_destination` with the following parameters:

-   `i_name`: the name of the destination.
-   Optional: `i_service_instance_name`: Typically, you use the destinations of the subaccount in which the ABAP instance resides or, in case of a SaaS solution based on the ABAP environment, the destinations of the consumer subaccount. However, you can add more destinations using your own destination service instance and communication scenario `SAP_COM_0276`, for example, to achieve separation of concerns \(see also [Create a Destination](create-a-destination-3fa7934.md)\). In this case, specify the value of the service instance name property of the communication arrangement for `SAP_COM_0276`.



**Using a Service Consumption Model**

You can consume your service using a Service Consumption Model \(SRVC\). Create an SRVC and replace the call of the method`cl_rfc_destination_provider=>create_by_comm_arrangement( )` that is proposed in the SRVC with`cl_rfc_destination_provider=>create_by_cloud_destination( )`:

> ### Sample Code:  
> ```abap
> TRY.
>       
>      " replace Method create_by_comm_arrangement( ).
>      " dest = cl_rfc_destination_provider=>create_by_comm_arrangement(
>      " comm_scenario = 'MY_COMM_SCENARIO'
>      " ).
>  
>     " replacement
>     DATA(dest) = cl_rfc_destination_provider=>create_by_cloud_destination(
>     EXPORTING
>     i_name       = 'name of destination'
>     ).
>  
>         CREATE OBJECT myobj
>           EXPORTING
>             destination = dest.
>  
>       myobj->bapi_activitytype_getlist(
>     IMPORTING
>        return            = lt_return
>     CHANGING
>        activitytype_list = lt_acttype_list.
>   ).
>     CATCH cx_aco_communication_failure INTO DATA(lcx_comm).
>     " handle CX_ACO_COMMUNICATION_FAILURE (sy-msg* in lcx_comm->IF_T100_MESSAGE~T100KEY)
>     CATCH cx_aco_system_failure INTO DATA(lcx_sys).
>      " handle CX_ACO_SYSTEM_FAILURE (sy-msg* in lcx_sys->IF_T100_MESSAGE~T100KEY)
>     CATCH cx_aco_application_exception INTO DATA(lcx_appl).
>     " handle APPLICATION_EXCEPTIONS (sy-msg* in lcx_appl->IF_T100_MESSAGE~T100KEY)
>     CATCH cx_rfc_dest_provider_error.
>     " handle CX_RFC_DEST_PROVIDER_ERROR
>  
> ENDTRY.
> ```

**Using `CALL FUNCTION ... DESTINATION`**

The sample code below shows how to get a reference to a destination and how to use it when calling a remote-enabled function module.

> ### Sample Code:  
> ```abap
> " getting the reference to the relevant destination
> TRY.
> DATA(lr_dest) = cl_rfc_destination_provider=>create_by_cloud_destination(
>     EXPORTING
>         i_name       = 'name_of_destination'
> ).
> CATCH cx_rfc_dest_provider_error.
>     " handle CX_RFC_DEST_PROVIDER_ERROR
> ENDTRY.
>  
>     DATA(lo_dest) = lr_dest->get_destination_name( ).
>     " using the destination in RFC
>  
>  
>    DATA msg TYPE c LENGTH 255.
>       CALL FUNCTION 'BAPI_ACTIVITYTYPE_GETLIST' DESTINATION lo_dest->get_destination_name( )
>           IMPORTING
>             return            = lt_return
>           TABLES
>             activitytype_list = lt_acttype_list.
>       EXCEPTIONS
>         system_failure        = 1 MESSAGE msg
>         communication_failure = 2 MESSAGE msg
>         OTHERS                = 3.
>     CASE sy-subrc.
>       WHEN 1.
>       " handle system failure    
>       WHEN 2.
>       " handle communication failure
>       WHEN 3.
>       " handle application failure
>     ENDCASE.
> ```

> ### Note:  
> When using on-premise connectivity, make sure the called RFC function module is exposed in Cloud Connector. See [Configure Access Control (RFC)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/ca5868997e48468395cf0ca4882f5783.html "Specify the backend systems that can be accessed by your cloud applications using RFC.") :arrow_upper_right:.



<a name="loio0c9b60f19d1644dabd4e89ebff79328d__section_an3_1sz_qsb"/>

## Test Your Outbound Call

To test your outbound call, configure an RFC destination as described in [Create RFC Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/9b3cc683cca944bd98346bef3181630e.html "How to create RFC destinations in the Destinations editor (SAP BTP cockpit).") :arrow_upper_right:. The following authentication methods are supported in the SAP BTP, ABAP environment:

**Internet**:

-   Basic Authentication: Fill the *User* and *Password* fields. If an alias logon is required, use the field *Alias User*.
-   Client Certificate Authentication: Use the additional property `jco.client.tls_client_certificate_logon` with value ***1*** to enable Client Certificate Authentication.

**OnPremise**:

-   Basic Authentication: Fill the *User* and *Password* fields.
-   Principal Propagation: Use the additional property `jco.destination.auth_type` with value ***PrincipalPropagation*** to enable Principal Propagation.

> ### Note:  
> -   For proxy type *Internet* and the use of authentication type client certificate, you must upload the X.509 client certificate in P12 format on the client side in the SAP BTP, ABAP environment, using the Maintain Client Certificates application. For more information, see [Maintain Client Certificates](../50-administration-and-ops/maintain-client-certificates-7f6a8fb.md). Uploading the client certificate via destination service isn't supported.
> -   For proxy type *OnPremise*, the use of authentication type ***PrincipalPropagation*** for a destination isn't supported in the ADT class runner.

**Related Information**  


[Destination Service](communication-management-5b8ff39.md#loioeeb0ec2318fb4dda87830a09ac7a02fa "Using the SAP destination service, you can retrieve and store technical information about the target resource (destination) that you want to connect with your application to a remote service or a system.")

