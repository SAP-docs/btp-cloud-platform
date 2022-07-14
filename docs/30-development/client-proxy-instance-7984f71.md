<!-- loio7984f7104ab74f35a1a8da57e7421022 -->

# Client Proxy Instance

Find information on how to create a Client Proxy instance to formulate a Client Proxy based request.

*Overview*

For information about the Client Proxy Instance, see [Client Proxy Instance](client-proxy-instance-079517f.md).



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_gwk_52x_5sb"/>

## OData V2 – Local Client Proxy

**Overview**

A Client Proxy instance can be created using class `IWBEP/CL_CP_CLIENT_PROXY_FACTORY`. It offers the static method `CREATE_V2_LOCAL_PROXY` to create an instance of the local V2 Client Proxy. As importing parameter, the service key is required \(the service id and the service version\) of the V2 OData service you want to consume. Furthermore, you have the option to specify whether a workload trace shall be written, which can later be checked in transaction `STAD`.

> ### Note:  
> A workload trace will not be written by default.

**Example**

You want to create a Client Proxy instance to consume the OData V2 service “ODATA\_V2\_TEST\_SERVICE” in version number 1:

> ### Sample Code:  
> ```
> 
> DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy.
> 	 lo_client_proxy = cl_web_odata_client_factory=>create_v2_local_proxy( VALUE #( service_id = ‘ODATA_V2_TEST_SERVICE' service_version = ‘0001’ ) ). 
> ```



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_rd3_tgx_5sb"/>

## OData V2 – Remote Client Proxy



### Overview

A Client Proxy instance can be created using class `CL_WEB_ODATA_CLIENT_FACTORYT`. It offers the static method `CREATE_V2_REMOTE_PROXY` to create an instance of the remote V2 Client Proxy. As importing parameters, you need the relative service root, the name of the underlying service definition, and a configured HTTP web client instance.

For more information about how to create a configured HTTP web client instance, see[Enable HTTP Communication in Your ABAP Code](enable-http-communication-in-your-abap-code-cef1ada.md) . See also the chapter about[HTTP Communication via Communication Arrangements](http-communication-via-communication-arrangements-3047582.md).

The service definition should have been automatically generated when creating a `Service Consumption Model`. For details on how to create a Service Consumption Model, see [Service Consumption Model](service-consumption-model-ed5d88e.md) and [Creating a Service Consumption Model](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/96132822b3554016b653d3601bb9ff1a.html).

Concerning the relative service root: The concatenated HTTP destination and the relative service root must point to the service document of the underlying OData service. So, it depends on the configuration of your HTTP web client instance how the relative service root must look like. In our example, we assume that your HTTP destination does not contain a path prefix \(i.e. does not point to a specific OData service\); then, the relative service root follows the general pattern `/sap/opu/odata/<service_id>`.



### Example

You want to create a Client Proxy instance to consume the OData V2 service with the service definition named `ODATA_V2_SERVICE_DEFINITION` and the service id `ODATA_V2_SERVICE`.

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
> In this example, the Client Proxy fetches a CSRF token automatically, i.e. it does a `HEAD` request to fetch a CSRF token. This token is automatically reused for all requests that are executed with this Client Proxy instance. If you want to change this behavior is, you can set `iv_do_fetch_csrf_token` to `abap_false`.



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_v44_tgx_5sb"/>

## OData V4 – Local Client Proxy



### Overview

A Client Proxy instance can be created using class `CL_WEB_ODATA_CLIENT_FACTORY`. It offers the static method `CREATE_V4_LOCAL_PROXY` to create an instance of the local V4 Client Proxy. As importing parameter, you need the service key \(i.e. the service id, the service repository \[which is “SRVD”\] and the service version\) of the V4 OData service you want to consume.

> ### Note:  
> The local V4 Client Proxy cannot be used to consume SAP OData services. You can only use it to consume your own services.



### Example

You want to create a Client Proxy instance to consume the OData V4 service `ODATA_V4_TEST_SERVICE` in version number 1:

> ### Sample Code:  
> ```
> 
> DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy. 
> 	  lo_client_proxy = /iwbep/cl_cp_client_proxy_fact=>create_v4_local_proxy( VALUE #( service_id =‘ODATA_V4_TEST_SERVICE'	
> 																						service_version = ‘0001’ 
> 																						repository_id = ‘DEFAULT’ ) ).
> 
> ```



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_wh1_xgx_5sb"/>

## OData V4 – Remote Client Proxy



### Overview

A Client Proxy instance can be created using class `CL_WEB_ODATA_CLIENT_FACTORY`. It offers the static method`CREATE_V4_REMOTE_PROXY` to create an instance of the remote V4 Client Proxy. As importing parameters, you need the relative service root, the name of the underlying service definition, and a configured HTTP web client instance.

For more information about how to create a configured HTTP web client instance, see[Enable HTTP Communication in Your ABAP Code](enable-http-communication-in-your-abap-code-cef1ada.md) . See also the chapter about[HTTP Communication via Communication Arrangements](http-communication-via-communication-arrangements-3047582.md).

The service definition should have been automatically generated when creating a `Service Consumption Model`. For details on how to create a Service Consumption Model, see [Service Consumption Model](service-consumption-model-ed5d88e.md) and [Creating a Service Consumption Model](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/96132822b3554016b653d3601bb9ff1a.html).

Concerning the relative service root: The concatenated HTTP destination and the relative service root must point to the service document of the underlying OData service. So, it depends on the configuration of your HTTP web client instance how the relative service root must look like. In our example, we assume that your HTTP destination does not contain a path prefix \(i.e. does not point to a specific OData service\); then, the relative service root follows the general pattern `/sap/opu/odata4/<service group id>/<repository id>/<service id>/<service version>`



### Example

You want to create a Client Proxy instance to consume the OData V4 service with the service definition named `ODATA_V4_SERVICE_DEFINITION` and the service id `ODATA_V4_SERVICE` \(version 1\), stored in service group `ODATA_GROUP` and repository `SRVD`.

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
> In this example, the Client Proxy fetches a CSRF token automatically, i.e. it does a `HEAD` request to fetch a CSRF token. This token is automatically reused for all requests that are executed with this Client Proxy instance. If you want to change this behavior is, you can set `iv_do_fetch_csrf_token` to `abap_false`.



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_r3y_xl3_ytb"/>

## Constraints

The local Client Proxy \(both V2 and V4\) cannot be used to consume OData services created by the SAP

