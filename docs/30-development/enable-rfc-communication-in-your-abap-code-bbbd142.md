<!-- loiobbbd14283e984d6aa7b05062f197ef5b -->

# Enable RFC Communication in Your ABAP Code

Use the *CALL FUNCTION ... DESTINATION* statement with a destination of proxy type `Internet` or `OnPremise` that is defined in the Destination service to call other systems from the ABAP environment.



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_x2n_dvw_qmb"/>

## Context

Using outbound calls via RFC from the ABAP environment, you can reach remote-enabled function modules in SAP cloud products and on-premise systems.



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_kch_jvw_qmb"/>

## Prerequisites

The respective destination exists in the relevant instance of the Destination service. The destination must be of type `RFC` and can use the proxy types `Internet` or `OnPremise`.

> ### Note:  
> Since there are no SM59-managed destinations \(destinations created via SAP transaction SM59\) available in the ABAP environment, the decoupling of design time and runtime is done through the Destination service.



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_mks_gvw_qmb"/>

## Example

The sample code below shows how to get a reference to a destination and how to use it when calling a remote-enabled function module.

> ### Sample Code:  
> ```lang-abap
> "Getting the reference to the relevant destination
> DATA(lr_dest) = cl_rfc_destination_provider=>create_by_cloud_destination(
>     EXPORTING
> 		i_name       = 'name_of_destination'
> ).
> DATA(lv_dest) = lr_dest->get_destination_name( ).
> "Using the destination in a Remote Function Call
> 
> CALL FUNCTION 'RFCPING' DESTINATION lv_dest.
> ```

Typically, you wil be using the destinations of the subaccount in which the ABAP instance resides. However, you can add more destinations using your own Destination service instance and communication scenario SAP\_COM\_0276, for example, to achieve separation of concerns.

> ### Note:  
> The use of authentication type `PrincipalPropagation` for a destination is not supported in the ADT class runner.



<a name="loiobbbd14283e984d6aa7b05062f197ef5b__section_kxv_zqm_drb"/>

## Extended Connection Control

The interface `IF_RFC_DEST` provides two methods allowing extended control of RFC connections. Using the methods `close_connection` and `reset_connection`, you can close or reset a connection respectively.

-   `close_connection`: Closes the connection. Use this method as soon as the connection is not needed any more.
-   `reset_connection`: Resets the server session. Using this method, you can re-use an existing connection.

```
lo_rfc_dest->reset_connection( ).
lo_rfc_dest->close_connection( ).

```

**Related Information**  


[Generate a Proxy to Consume Remote-Enabled Function Modules](generate-a-proxy-to-consume-remote-enabled-function-modules-0c9b60f.md "Generate an RFC proxy via the service consumption model.")

