<!-- loio079517fdf9f74e5b8bbd42377991c8e6 -->

# Client Proxy Instance

Find information on how to create and use a Client Proxy instance of type `/iwbep/if_cp_client_proxy`.



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_pwm_ytm_rsb"/>

## Overview

The Client Proxy instance is the starting point for consuming any OData service within ABAP. Its main functionality is to create a corresponding resource. For more information, see [Resource Instance](resource-instance-25e2e3d.md).

Furthermore, it can be used to create a batch or changeset as well as a delta link requests.



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_zz1_q5m_rsb"/>

## Creating an Instance

*Comparison between V2 and V4 Client Proxy*

If a V2 or V4 Client Proxy instance should be created depends on whether the OData service you want to consume is an OData V2 service or an OData V4 service, because the underlying OData protocols differ. You cannot provide a version-agnostic Client Proxy.

*Comparison between Remote and Local Consumption*

The decision of using a local or remote Client Proxy instance depends on the current use case.

*Remote Client Proxy*

A remote Client Proxy is used to consume an OData service offered on a remote server. If you want to create a remote Client Proxy instance, the following is required:

-   A configured HTTP client instance

-   The relative service root pointing to the service document

-   A Client Proxy \(or Service Consumption\) model


If you want to create an HTTP client instance, see [Enable HTTP Communication in Your ABAP Code](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cef1ada754154d11b5701ab60e6ab412.html?q=Enable%20HTTP%20Communication%20in%20Your%20ABAP%20Code).

Relative Service Root: The relative service root – combined with the HTTP destination – should point to the service document of the OData service you want to consume. The service document is the top-level representation of an OData service. It lists the entity sets, singletons and the functions of the service. It is available at `http(s)://host/service/` base URL. The resources provided in the service document can be accessed with a URL that is the concatenation of the base URL and the resource URL.

> ### Example:  
> You try to consume the OData V4 service TEA\_BUSI \(in version 2\), which is part of the `/IWBEP/TEA` OData service group and belongs to the service repository.
> 
> DEFAULT. If the absolute URL to fetch the corresponding service document is `http://xyzia1b.rot.sap.corp:1234/sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0002/`, the relative service URL is`/sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0002/`

Similar to an OData service, the remote Client Proxy needs a model object, which is the runtime representation of a model \(compare to the model defined by a model provider class \(MPC\) for an OData service\). The Service Consumption Model is needed as we do not have for example statically generated OData service specific proxies. Instead we have one generic Client Proxy; in order to handle everything that is needed to process a client request, the framework needs the following information:

-   Name and definition of the EDM artifacts

-   The mapping from EDM to ABAP names – most importantly for properties

-   ABAP data types

-   ABAP conversion exits


This means that a Service Consumption Model defines the characteristics, properties, or parameters - such as the number or the age of employees.

For detailed examples on how to create a Service Consumption Model, see [Service Consumption Model](service-consumption-model-ed5d88e.md).

*Local Client Proxy*

The local Client Proxy is used in case a locally deployed OData service is consumed. The local Client Proxy delegates a request to the backend component of the corresponding V2 or V4 runtime without an HTTP overhead. The use case for this scenario is the creation of Unit Tests, for example, when you try to build an integration test for your service data provider.

> ### Note:  
> Since it is designed for writing tests of your data provider, the local Client Proxy skips several layers inside the *SAP Gateway Framework* and directly calls the data provider class. This has following effects:
> 
> -   Particular tests, usually executed during OData request processing, are skipped.
> 
> -   For both, V2 and V4, the business data received from the \(local consumption\) response will also not be re-converted for outbound processing.
> 
> -   When using the V4 local client proxy, the business data you enter will not be converted for inbound processing; the data provider receives exactly the data you entered in the request.

For creating a local Client Proxy instance, you the service key is required, which consists of the service repository id \(e.g. DEFAULT\), the service id \(i.e. the internal name of the OData service\) and the service idversion \(for example, 0003\). You neither need a HTTP client instance nor a Proxy model.



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_tnp_nnm_ysb"/>

## Asynchronous Client Proxy

A special case is the asynchronous Client Proxy. It can be used if you want to consume an OData V4 service on a remote server using asynchronous processing of HTTP calls, for example, if you want to add a queue between the client application and the current HTTP outbound call.

> ### Note:  
> In this case, *asynchronous* means asynchronous for the Client only. The actual HTTP outbound call is executed synchronously.
> 
> Furthermore, there are currently some limitations for this approach:
> 
> -   The server response can not be fetched
> 
> -   If the HTTP return code is 300 or higher, the queue between client application and HTTP outbound call is blocked

For more information on the asynchronous technology used, see [bgRFC \(Background Remote Function Call\)](https://help.sap.com/viewer/753088fc00704d0a80e7fbd6803c8adb/202110.000/en-US/48927c2caa6b17cee10000000a421937.html).

> ### Note:  
> Asynchronous processing is only supported for remote consumption of OData V4 services and only available on On-Premise systems.

For creating an asynchronous Client Proxy, the following is required:

-   A "Callback" factory for http clients

-   A Client Proxy model \(see chapter *Remote Client Proxy*\)

-   The name of your bgRFC destination

-   The name of your bgRFC queue

-   The relative service path \(see chapter *Remote Client Proxy*\)


Similar to the remote Client Proxy, the asynchronous Client Proxy requires a configured HTTP client instance. However, due to technical reasons, this instance cannot be injected into the Client Proxy directly. Instead, you need a factory class that provides a configured HTTP instance on demand.

For detailed information on how to provide such a class and how to create a bgRFC destination/queue, see [OData Asynchronous Request](odata-asynchronous-request-139f06b.md).



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_bkn_3dn_rsb"/>

## Creating an Instance

An instance of the Client Proxy can be created via class `/iwbep/cl_cp_client_proxy_fact`, which provides the following static methods:

-   create\_v2\_local\_proxy

-   create\_v2\_remote\_proxy

-   create\_v4\_asynchronous\_proxy

-   create\_v4\_local\_proxy

-   create\_v4\_remote\_proxy


For examples on the creation of instances, see [Client Proxy Instance](client-proxy-instance-7984f71.md).

> ### Note:  
> All instances returned are of type `/iwbep/if_cp_client_proxy` and therefore offer the same methods. However, certain methods can only be used by a specific Client Proxy \(for eaxample, a remote OData V4 proxy\) and will therefore raise an exception if called with the wrong Client Proxy instance.



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_j3x_fjn_rsb"/>

## Functionality

The Client Proxy instance is the starting point for the OData service consumption within ABAP. Its main functionality is to provide a corresponding resource instance \(see [Resource Instance](resource-instance-25e2e3d.md)\), such as an action import or an entity\(set\).

Furthermore, it provides methods for creating $batch \(see [OData Request as Batch Including Changesets](odata-request-as-batch-including-changesets-fc10253.md)\) and delta link requests \(together with certain delta link centered utility methods, see [OData Request: Delta Link Query Option](odata-request-delta-link-query-option-9dff06d.md) \).



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_fvc_g3n_rsb"/>

## Examples

For examples on how to create and use Client Proxy instances, see [Client Proxy Instance](client-proxy-instance-7984f71.md).

