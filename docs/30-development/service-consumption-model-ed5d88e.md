<!-- loioed5d88ea66ce439398c37fe3dfc2cfd5 -->

# Service Consumption Model

Consume a remote OData request in the Client Proxy instance.



<a name="loioed5d88ea66ce439398c37fe3dfc2cfd5__section_yxd_y1d_vtb"/>

## Overview

Before consuming remote ODATA request request, you must first create a Service Consumption Model for the OData Service you want to consume. See [Creating Service Consumption Model](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/96132822b3554016b653d3601bb9ff1a.html) for more information.



<a name="loioed5d88ea66ce439398c37fe3dfc2cfd5__section_e4n_1bd_vtb"/>

## Creating a Service Consumption Model



### Overview

A remote Client Proxy request needs a corresponding Service Consumption Model.

The benefits of using a Service Consumption Model \(instead of manually creating a corresponding model\) are:

-   Simple creation using XML or EDMX file uploading. You don't need to manually define the model.

-   The code generator creates code snippets to use as blueprint on how to write Client Proxy-related coding.


![](images/Service_Consumption_1cdb46d.png)



### Example

Create a Service Consumption Model for remote consumption of your OData service. You have the metadata of the corresponding OData service that you want to consume in an XML or EDMX file.



### Step-by-step

See [Generating Proxies for Remote OData Service](https://help.sap.com/viewer/25cf71e63940453397a32dc2b7676947/2111.500/en-US/aa3a88a28694471d8c90623dc32ceabe.html) for how to create your Service Consumption Model.



<a name="loioed5d88ea66ce439398c37fe3dfc2cfd5__section_jkb_wkd_vtb"/>

## Constraints

-   Not all OData service model features are supported for Service Consumption Models. For example, you might not be able to create a Service Consumption Model for your underlying OData service. This is the case if your Service Model contains Complex Collections, Actions, or Functions.


