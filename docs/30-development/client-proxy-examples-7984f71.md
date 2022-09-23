<!-- loio7984f7104ab74f35a1a8da57e7421022 -->

# Client Proxy Examples

OData Proxy examples for OData Version 2 and Version 4 for local and remote client proxies.

*Overview*

For information about the Client Proxy Instance, see [Client Proxy Instance Types](client-proxy-instance-types-079517f.md).



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_gwk_52x_5sb"/>

## OData Version 2: Local Client Proxy

**Overview**

You can create a Client Proxy instance with class `IWBEP/CL_CP_CLIENT_PROXY_FACTORY`. It offers the static method `CREATE_V2_LOCAL_PROXY` to create a local V2 Client Proxy instance. The service key parameters \(***service\_id*** and ***service\_version***\) are required for the V2 OData service you want to consume. You can also specify if you want to write a workload trace \(you can later check in transaction `STAD`.

> ### Note:  
> A workload trace is not written by default.

**Example**

Create a Client Proxy instance to consume the OData V2 service “***ODATA\_V2\_TEST\_SERVICE***” in version number 1:

> ### Sample Code:  
> ```
> 
> DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy.
> 	 lo_client_proxy = cl_web_odata_client_factory=>create_v2_local_proxy( VALUE #( service_id = ‘ODATA_V2_TEST_SERVICE' service_version = ‘0001’ ) ). 
> ```



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_rd3_tgx_5sb"/>

## OData Version 2: Remote Client Proxy



### Overview

You can create a Client Proxy instance using class `CL_WEB_ODATA_CLIENT_FACTORYT`. It offers the static method `CREATE_V2_REMOTE_PROXY` to create a remote V2 Client Proxy instance. The relative service root parameter \(***service\_definition\_name***\) and a configured HTTP web client instance are required.

For more information about how to create a configured HTTP web client instance, see:

-   [Enable HTTP Communication in your ABAP Code](enable-http-communication-in-your-abap-code-cef1ada.md).
-   [HTTP Communication via Communication Arrangements](http-communication-via-communication-arrangements-3047582.md).

The service definition is automatically generated when you create a `Service Consumption Model`.

The concatenated HTTP destination and the relative service root must point to the service document of the OData service. Depending on your HTTP web client instance configuration, the way your relative service root looks can vary. In our example, we assume that your HTTP destination doesn't have a path prefix \(for example, doesn't point to a specific OData service\). The relative service root follows the general pattern `/sap/opu/odata/<service_id>`.



### Example

Create a Client Proxy instance to consume the OData Version 2 service with the service definition `ODATA_V2_SERVICE_DEFINITION` and the service id `ODATA_V2_SERVICE`.

> ### Sample Code:  
> ```
> 
> DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy,
>       lo_web_http_client TYPE REF TO if_web_http_client.
> 
> lo_client_proxy = cl_web_odata_client_factory=>create_v2_remote_proxy(
> 		  iv_service_definition_name = 'ODATA_V2_SERVICE_DEFINITION'
> 		  io_http_client = lo_web_http_client
> 		  iv_do_fetch_csrf_token = abap_true
> 			
> 		  iv_relative_service_root = '/sap/opu/odata/ODATA_V2_SERVICE' ).
> ```

> ### Note:  
> In this example, the Client Proxy automatically fetches a cross-site request forgery \(CSRF\) token. It does a `HEAD` request to fetch a CSRF token. This token is automatically reused for all requests executed with this Client Proxy instance. If you want to change this behavior, set `iv_do_fetch_csrf_token` to `abap_false`.



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_v44_tgx_5sb"/>

## OData Version 4: Local Client Proxy



### Overview

Create a Client Proxy instance using class `CL_WEB_ODATA_CLIENT_FACTORY`. It offers the static method `CREATE_V4_LOCAL_PROXY` to create a local Version 4 Client Proxy instance. The service key parameters \(***service\_id***, ***relative\_service\_root***, which is “***SRVD***, and the ***service\_version***\) are required for the Version 4 OData service you want to consume.

> ### Note:  
> The local Version 4 Client Proxy can't be used to consume SAP OData services. You can only use it to consume your own services.



### Example

Create a Client Proxy instance to consume the OData Version 4 service `ODATA_V4_TEST_SERVICE` in version number 1:

> ### Sample Code:  
> ```
> 
> DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy. 
> 	  lo_client_proxy = /cl_web_odata_client_factory=>create_v4_local_proxy( VALUE #( service_id =‘ODATA_V4_TEST_SERVICE'	
> 																						service_version = ‘0001’ 
> 																						repository_id = ‘DEFAULT’ ) ).
> 
> ```



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_wh1_xgx_5sb"/>

## OData Version 4: Remote Client Proxy



### Overview

You can create a Client Proxy instance using class `CL_WEB_ODATA_CLIENT_FACTORY`. It offers the static method `CREATE_V4_REMOTE_PROXY` to create a remote Version 4 Client Proxy instance. The relative service root parameters \(***relative\_service\_root***\) definition and a configured HTTP web client instance are required.

The concatenated HTTP destination and the relative service root must point to the OData service document. Depending on your HTTP web client instance configuration, the way your the relative service root looks can vary. In our example, we assume that your HTTP destination does not contain a path prefix \(i.e. does not point to a specific OData service\); then, the relative service root follows the general pattern `/sap/opu/odata4/<service group id>/<repository id>/<service id>/<service version>`



### Example

You want to create a Client Proxy instance to consume the OData Version 4 service with the service definition named `ODATA_V4_SERVICE_DEFINITION` and the service id `ODATA_V4_SERVICE` \(version 1\), stored in service group `ODATA_GROUP` and repository `SRVD`.

> ### Sample Code:  
> ```
> 
> DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy,	
> 	 lo_web_http_client TYPE REF TO if_web_http_client.
> 
> 	 lo_client_proxy = cl_web_odata_client_factory=>create_v4_remote_proxy(iv_service_definition_name = 'ODATA_V4_SERVICE_DEFINITION'
> 															   io_http_client = lo_web_http_client
> 															   iv_do_fetch_csrf_token = abap_true
> 															   iv_relative_service_root = '/sap/opu/odata4/ODATA_GROUP/SRVD/ODATA_V4_SERVICE/0001' ).
> ```

> ### Note:  
> In this example, the Client Proxy automatically fetches a cross-site request forgery \(CSRF\) token. It does a `HEAD` request to fetch a CSRF token. This token is automatically reused for all requests executed with this Client Proxy instance. If you want to change this behavior, set `iv_do_fetch_csrf_token` to `abap_false`.



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_r3y_xl3_ytb"/>

## Constraints

The local Client Proxy \(both Version 2 and Version 4\) can't be used to consume SAP OData services.

**Related Information**  


[Service Consumption Model](service-consumption-model-ed5d88e.md "Consume a remote OData request in the Client Proxy instance.")

