<!-- loio079517fdf9f74e5b8bbd42377991c8e6 -->

# Client Proxy Instance Types

Create remote and local Client Proxy instances in OData Version 2 or Version 4.



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_pwm_ytm_rsb"/>

## Client Proxy Versions



### Client Proxy Version 2 and Version 4

Depending on if the OData service you want to consume \(Version 2 or Version 4 service\), you'll create a Version 2 or Version 4 Client Proxy instance, The underlying OData protocols differ between Version 2 and Version 4. You can't provide a version-agnostic Client Proxy.



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_zhb_bjv_j5b"/>

## Consumption Types

The decision of using a local or remote Client Proxy instance depends on the current use case.



### Remote Client Proxy

A remote Client Proxy is used to consume an OData service offered on a remote server. If you want to create a remote Client Proxy instance, the following is required:

-   A configured HTTP client instance

-   The relative service root pointing to the service document

-   Service Consumption model


If you want to create an HTTP client instance, see [Enable HTTP Communication in Your ABAP Code](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cef1ada754154d11b5701ab60e6ab412.html?q=Enable%20HTTP%20Communication%20in%20Your%20ABAP%20Code).

**Relative Service Root:** The relative service root \(combined with the HTTP destination\) should point to the service document for the OData service you want to consume. The service document is the top-level representation of an OData service. It lists the entity sets, singletons, and service functions. It is available at `http(s)://host/service/` base URL. You can access the resources in the service document using a URL that is the concatenation of the base URL and the resource URL.

> ### Example:  
> You want to consume the OData Version 4 service ***TEA\_BUSI*** in version 2, which is part of the `/IWBEP/TEA` OData service group and belongs to the service repository ***DEFAULT***.
> 
> If the absolute URL to fetch the corresponding service document is `http://xyzia1b.rot.sap.corp:1234/sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0002/`, the relative service URL is `/sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0002/`.

The remote Client Proxy needs a model object, which is the runtime representation of a model \(compared to the model defined by a model provider class \(MPC\) for an OData service\). The Service Consumption Model is needed since we don't have \(for example\) statically generated OData service specific proxies. Instead, we have one generic Client Proxy. To handle everything needed to process a client request, the framework needs this information:

-   Name and definition of the EDM artifacts

-   The mapping from EDM to ABAP names \(most importantly for properties\)

-   ABAP data types

-   ABAP conversion exits


A Service Consumption Model defines the characteristics, properties, or parameters \(such as, the number or the age of employees\).

For detailed examples on how to create a Service Consumption Model, see [Service Consumption Model](service-consumption-model-ed5d88e.md).



### Local Client Proxy

Use the local Client Proxy when a locally-deployed OData service is consumed. The local Client Proxy delegates a request to the backend component of the corresponding Version 2 or Version 4 runtime without an HTTP overhead. The use case for this scenario is to creation Unit Tests, for example, when you want to build an integration test for your service data provider.

> ### Note:  
> Since the local Client proxy is designed for writing tests of your data provider, it skips several layers inside the *SAP Gateway Framework* and directly calls the data provider class. This has following effects:
> 
> -   Certain tests that are usually executed during OData request processing are skipped.
> 
> -   For both Version 2 and Version 4, the business data received from the \(local consumption\) response is not re-converted for outbound processing.
> 
> -   When using the Version 4 local client proxy, the business data you enter is not converted for inbound processing. The data provider receives the data exactly how you entered in the request.

For creating a local Client Proxy instance, the service key is required. The service key includes the service repository id \(for example, ***DEFAULT***\), the service id \(the ODATA service internal name\), and the service id version \(for example, ***0003***\). You don't need an HTTP client instance or a Service Consumption model.



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_bkn_3dn_rsb"/>

## Creating an Instance

You can create an instance of the Client Proxy using class `cl_web_odata_client_factory`, which provides these static methods:

-   ***create\_v2\_local\_proxy***

-   ***create\_v2\_remote\_proxy***

-   ***create\_v4\_local\_proxy***

-   ***create\_v4\_remote\_proxy***


> ### Note:  
> All returned instances are from type `/iwbep/if_cp_client_proxy` and offer the same methods. Certain methods are only used by a specific Client Proxy \(for example, a remote OData Version 4 proxy\) and can raise an exception if the wrong Client Proxy instance is called.



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_j3x_fjn_rsb"/>

## Functionality

-   The Client Proxy instance is the starting point for the OData service consumption with ABAP.
-   The Client Proxy instance provides a corresponding [Resource Instance](resource-instance-25e2e3d.md) \(for example, an action import or an entity set\).
-   The Client Proxy instance provides methods for creating ***$batch*** and delta link requests \(with certain delta link-centered utility methods\).



<a name="loio079517fdf9f74e5b8bbd42377991c8e6__section_fvc_g3n_rsb"/>

## Examples

For examples on how to create and use Client Proxy instances, see [Client Proxy Examples](client-proxy-examples-7984f71.md).

**Related Information**  


[Resource Instance](resource-instance-25e2e3d.md "A resource instance represents a resource that is shared between applications and identified using URLs and defined in the data model.")

[OData Request as Batch Including Changesets](odata-request-as-batch-including-changesets-fc10253.md "Create an $batch request, including changesets in the Client Proxy instance.")

[OData Request: Delta Link Query Option](odata-request-delta-link-query-option-9dff06d.md "Create an OData request with $delta token query option in the Client Proxy instance.")

