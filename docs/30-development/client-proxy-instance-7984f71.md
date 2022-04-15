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
>       lo_client_proxy = /iwbep/cl_cp_client_proxy_fact=>create_v2_local_proxy( VALUE #( service_id =                                                
> 
> ‘ODATA_V2_TEST_SERVICE' 
> service_version =  ‘0001’ ) ). 
> ```



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_rd3_tgx_5sb"/>

## OData V2 – Remote Client Proxy

**Overview**

A Client Proxy instance can be created using class `IWBEP/CL_CP_CLIENT_PROXY_FACT`. It offers the static method `CREATE_V2_REMOTE_PROXY` to create an instance of the remote V2 Client Proxy. As importing parameters, the relative service root, the Proxy Model key, and a configured HTTP client instance are required.

For more information on how to create a configured HTTP client instance, see [Enable HTTP Communication in Your ABAP Code](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/cef1ada754154d11b5701ab60e6ab412.html?locale=en-US&version=Cloud&q=if_web_http_client%3Fq%3Dif_web_http_client).

The proxy model key consists of the proxy model id, the proxy model version and the proxy model repository id. Use the values defined in `IWBEP/CP_ADMIN` for model id and model version and use `DEFAULT` for the repository id.

For more information on how to create a Proxy Model, see

The concatenated HTTP destination and the relative service root must point to the service document of the underlying OData service. This means that it depends on the configuration of the HTTP client instance how the relative service root must appear. In the following example it is assumed, that the HTTP destination does not contain a path prefix \(meaning it does not point to a specific OData service\). In this case, the relative service root follows the general pattern /sap/opu/odata/<service\_id\>.

**Example**

You want to create a Client Proxy instance to consume the OData V2 service with the Proxy Model Id `ODATA_V2_PROXY_MODEL` and the service id `ODATA_V2_SERVICE_ID`:

> ### Sample Code:  
> ```
> 
> DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy, 
>       lo_http_client TYPE REF TO if_http_client.                                               
> 
> lo_client_proxy = /iwbep/cl_cp_client_proxy_fact=>create_v2_remote_proxy( 
> 	is_proxy_model_key = VALUE #( repository_id = ‘DEFAULT’ 
>  				proxy_model_id = ‘ODATA_V2_PROXY_MODEL' 
>  				proxy_model_version = ‘0001’ 
> io_http_client = lo_http_client 
> iv_relative_service_root = '/sap/opu/odata/ODATA_V2_SERVICE_ID' ).
> 
> ```



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_v44_tgx_5sb"/>

## OData V4 – Local Client Proxy

**Overview**

A Client Proxy instance can be created using class `IWBEP/CL_CP_CLIENT_PROXY_FACT`. It offers the static method `CREATE_V4_LOCAL_PROXY` to create an instance of the local V4 Client Proxy. As importing parameter, the service key \(i.e. the service id, the service repository and the service version\) of the V4 OData service you want to consume is required. Furthermore, you have the option to specify whether a workload trace shall be written, which can later be checked in transaction `STAD`.

> ### Note:  
> A workload trace will not be written by default.

**Example**

You want to create a Client Proxy instance to consume the OData V4 service `ODATA_V4_TEST_SERVICE` in version number 1:

> ### Sample Code:  
> ```
> 
> DATA: lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy. 
> 
> lo_client_proxy = /iwbep/cl_cp_client_proxy_fact=>create_v4_local_proxy( VALUE #( service_id = 
> 
> ‘ODATA_V4_TEST_SERVICE' 
> 														service_version = ‘0001’ 
> 														repository_id = ‘DEFAULT’ ) ).
> 
> ```

> ### Note:  
> For RAP created OData services, the repository id is `SRVD`. For manually created services, the repository is `DEFAULT`.



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_wh1_xgx_5sb"/>

## OData V4 – Remote Client Proxy

Overview

A Client Proxy instance can be created using class `IWBEP/CL_CP_CLIENT_PROXY_FACT`. It offers the static method `CREATE_V4_REMOTE_PROXY` to create an instance of the remote V4 Client Proxy. As importing parameters, the relative service root, the Proxy Model key, and a configured HTTP client instance are required.

For more information on how to create a configured HTTP client instance, see [Enable HTTP Communication in Your ABAP Code](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/cef1ada754154d11b5701ab60e6ab412.html?locale=en-US&version=Cloud&q=if_web_http_client%3Fq%3Dif_web_http_client).

The proxy model key consists of the proxy model id, the proxy model version and the proxy model repository id.

Use the values defined in `IWBEP/CP_ADMIN` for model id and model version and use `DEFAULT` for the repository id.

For more information on how to create a Proxy Model, see

The concatenated HTTP destination and the relative service root must point to the service document of the underlying OData service. This means that it depends on the configuration of your HTTP client instance how the relative service root must appear. In the following example it is assumed, that the HTTP destination does not contain a path prefix \(i.e. does not point to a specific OData service\); the relative service root follows the general pattern /sap/opu/odata4/<service group id\>/<repository id\>/<service id\>/<service version\>

> ### Note:  
> For RAP created OData services, the repository id is `SRVD`. For manually created services, the repository is `DEFAULT`.

**Example**

You want to create a Client Proxy instance to consume the OData V4 service with the Proxy Model Id `ODATA_V4_PROXY_MODEL` and the service id “ODATA\_V4\_SERVICE” \(version 1\), stored in service group `ODATA_GROUP` and repository `DEFAULT`:

> ### Sample Code:  
> ```
> 
> DATA:	lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy, 
> 		lo_http_client TYPE REF TO if_http_client. 
> 
> lo_client_proxy = /iwbep/cl_cp_client_proxy_fact=>create_v4_remote_proxy( 
> 		is_proxy_model_key = VALUE #( repository_id = ‘DEFAULT’ 
> 								proxy_model_id = ‘ODATA_V4_PROXY_MODEL' 
> 								proxy_model_version = ‘0001’ 
> 		io_http_client = lo_http_client 
> 		iv_relative_service_root =
> '/sap/opu/odata4/ODATA_GROUP/DEFAULT/ODATA_V4_SERVICE/0001').
> ```



<a name="loio7984f7104ab74f35a1a8da57e7421022__section_hxh_ygx_5sb"/>

## OData V4 –Asynchronous Client Proxy

**Overview**

The asynchronous Client Proxy uses background remote function calls \(bgRFC\). For an overview about this technology, see [bgRFC \(Background Remote Function Call\)](https://help.sap.com/viewer/753088fc00704d0a80e7fbd6803c8adb/1709%20002/en-US/48927c2caa6b17cee10000000a421937.html).

A Client Proxy instance can be created using class `IWBEP/CL_CP_CLIENT_PROXY_FACT`. It offers the static method `CREATE_V4_ASYNCHRONOUS_PROXY` to create an instance of the asynchronous \(remote\) V4 Client Proxy. As importing parameters, the relative service root, the Proxy Model key, a "Callback" factory for http clients, the name of the underlying bgRFC destination, and the name of the underlying bgRFC queue are required.

Similar to other remote Client Proxy instances, the asynchronous Client Proxy requires a configured HTTP client. Due to technical reasons, it is not sufficient to hand over the configured HTTP client instance for asynchronous processing. Instead, you must provide a “Callback”, i.e. a factory method of type`ref to /IWBEP/IF_CP_HTTP_CLIENT_FACT`, which can return the configured HTTP client via method `GET_HTTP_CLIENT`.

For more information on how to create a configured HTTP client instance, see [Enable HTTP Communication in Your ABAP Code](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/cef1ada754154d11b5701ab60e6ab412.html?locale=en-US&version=Cloud&q=if_web_http_client%3Fq%3Dif_web_http_client).

A bgRFC destination can be created using transaction SM59 or in the *SAP Implementation Guide* \(page Configuration of RFC destination\) under *ABAP Platform* \> *SAP Gateway* \> *OData Channel* \> *Configuration* \> *Connection Settings* \> *SAP Gateway to Consumer* \> *Create RFC Destination for Outbound Queues*.

A bgRFC queue can be monitored on the bgRFC Monitor page in the *SAP Implementation Guide* under *ABAP Platform* \> *SAP Gateway* \> *OData Channel* \> *Configuration* \> *Connection Settings* \> *SAP Gateway to Consumer* \> *Monitor bgRFC Queues*.

-   Find more details on the bgRFC queue and destination and the callback factory in the corresponding example under

-   Also refer to:
    -   [bgRFC \(Background Remote Function Call\)](https://help.sap.com/viewer/753088fc00704d0a80e7fbd6803c8adb/1709%20002/en-US/48927c2caa6b17cee10000000a421937.html).

    -   [Creating a Supervisor Destination](https://help.sap.com/doc/saphelp_nw73/7.3.16/en-US/48/9bfc541786062de10000000a42189d/frameset.htm).


-   Transaction `SBGRFCCONF`

-   Transaction `SBGRFCMON`


The proxy model key consists of the proxy model id, the proxy model version and the proxy model repository id. If you have created the proxy model manually using transaction `IWBEP/CP_ADMIN`, use the values defined there for model id and model version and use `DEFAULT` for the repository id.

If you have created a *Service Consumption Model* in the ADT, use ‘0001’ as model version, `SRVD` as repository id and the name of the generated service definition for the model id.

For more information on how to create a Proxy Model, see

For more information on the Service Consumption Model, see [Creating Service Consumption Model](https://help.sap.com/viewer/25cf71e63940453397a32dc2b7676947/2111.500/en-US/96132822b3554016b653d3601bb9ff1a.html).

The concatenated HTTP destination and the relative service root must point to the service document of the underlying OData service. Therefore, it depends on the configuration of your HTTP client instance how the relative service root must appear. The following example assumes that the HTTP destination does not contain a path prefix \(i.e. does not point to a specific OData service\). The relative service root follows the general pattern /sap/opu/odata4/<service group id\>/<repository id\>/<service id\>/<service version\>

> ### Note:  
> For RAP created OData services, the repository id is `SRVD`. For manually created services, the repository is `DEFAULT`.

**Example**

You want to create a Client Proxy instance to consume the OData V4 service with the Proxy Model Id `ODATA_V4_PROXY_MODEL` and the service id `ODATA_V4_SERVICE_BINDING` \(stored in the `ODATA_GROUP` service group and repository `DEFAULT`\) asynchronously. The bgRFC destination and queue have the name `ASYNC_DEST` and `ASYNC_QUEUE`.

> ### Sample Code:  
> ```
> 
> DATA:	lo_client_proxy TYPE REF TO /iwbep/if_cp_client_proxy, 
> 		lo_http_client_factory TYPE REF TO /IWBEP/IF_CP_HTTP_CLIENT_FACT. 
> 
> lo_client_proxy = /iwbep/cl_cp_client_proxy_fact=>create_v4_asynchronous_proxy( 
> 		is_proxy_model_key = VALUE #( repository_id = ‘DEFAULT’
> 								proxy_model_id = ‘ODATA_V4_PROXY_MODEL’ 
> 								proxy_model_version = ‘0001’ 
> 		iv_bgrfc_destination = 'ASYNC_DEST' 
> 		iv_bgrfc_queue = 'ASYNC_QUEUE' 
> 		io_http_client_factory = lo_http_client_factory 
> 		iv_relative_service_root =
> ‘/sap/opu/odata4/ODATA_GROUP/DEFAULT/ODATA_V4_SERVICE/0001' ). 
> ```

