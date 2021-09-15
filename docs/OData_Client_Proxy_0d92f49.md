<!-- loio0d92f493624f47fba997d3a5e0dd2a0d -->

# OData Client Proxy

An OData Client Proxy is the public Application Programming Interface \(API\) for client applications. It is used to call an OData Client Proxy service with the specific OData Client Proxy version \(V2 and V4\), to consume its business data. The OData Client Proxy provides:

-   request details \(such as the entity set to be read with which filter\) using the client request object

-   response data using the client response object


> ### Note:  
> In the *ABAP RESTful Application Programming Model* \(RAP\), you can generate a *Service Consumption Model* \(SCM\) for the remote proxy based on the EDMX file of an OData service \(for example ZSC\_EDMX\_IMPORT\). In this case, a different repository id \(SRVD\) is used in the proxy model key \(import parameter `is_proxy_model_key`\).
> 
> > ### Note:  
> > For information on how to enable HTTP communication, see [Enable HTTP Communication in Your ABAP Code](Enable_HTTP_Communication_in_Your_ABAP_Code_cef1ada.md).
> 
> For local proxy, you only need the service id and the service version \(import parameter `create_v2_local_proxy ( VALUE #( service_id = '/IWBEP/TEA_TEST_APPLICATION' service_version = '0001' ) )`\).

> ### Example:  
> SAP BTP, ABAP environment
> 
> ```
> 
> TRY.
> 	lo_client_proxy = CL_WEB_ODATA_CLIENT_FACTORY=>create_v2_remote_proxy(
> 	io_http_client = lo_http_client
> 	is_proxy_model_key = VALUE #( repository_id = /iwbep/if_cp_registry_types=>gcs_repository_id-srvd "SRVD
> 	proxy_model_id = 'ZSC_EDMX_IMPORT'
> 	proxy_model_version = 0001 )
> 	iv_relative_service_root = '/sap/opu/odata/IWBEP/TEA_TEST_APPLICATION' ).
> 
> ENDTRY.
> 
> 
> ```

**Tracing Tools**

You can trace the payload and display error logs. To do so, check*Payload Trace* on the *Configuration* tab under *Available Log and Traces*. You can display tracing results on the *Payload Trace* tab.

**Constraints**

[2428114](https://launchpad.support.sap.com/#/notes/2428114): This SAP Note outlines the constraints applicable to the OData Client Proxy support in SAP Gateway Foundation \(SAP\_GWFND\) for OData version 2 \(V2\) and OData version 4 \(V4\).

-   **[Local Client Proxy](Local_Client_Proxy_287674d.md "")**  

-   **[Remote Client Proxy](Remote_Client_Proxy_7c69fb6.md "")**  

-   **[Client Proxy Administration](Client_Proxy_Administration_f256afd.md "")**  

-   **[Additional Features for OData Client Proxy](Additional_Features_for_OData_Client_Proxy_8d1423c.md "")**  


