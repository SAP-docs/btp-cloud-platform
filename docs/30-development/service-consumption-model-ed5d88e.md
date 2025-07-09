<!-- loioed5d88ea66ce439398c37fe3dfc2cfd5 -->

# Service Consumption Model

A Service Consumption Model \(SRVC\) generates proxy artifacts to consume OData, RFC, or SOAP services.



<a name="loioed5d88ea66ce439398c37fe3dfc2cfd5__section_yxd_y1d_vtb"/>

## Overview

To consume OData, SOAP, or RFC services, you must first create a Service Consumption Model \(SRVC\). See [Creating Service Consumption Model](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/96132822b3554016b653d3601bb9ff1a.html) for more information. An SRVC creates proxy artifacts and a code snippet that you can copy and paste to your code to perform the service call. For RFC, the SRVC is optional.



<a name="loioed5d88ea66ce439398c37fe3dfc2cfd5__section_e4n_1bd_vtb"/>

## Creating a Service Consumption Model



### Overview

A remote client proxy request needs a corresponding SRVC.

The benefits of using an SRVC \(instead of manually creating a corresponding model\) are:

-   Simple creation using XML or EDMX file uploading. You don't need to manually define the model.

-   The code generator creates code snippets to use as blueprint on how to write client proxy-related coding.


![](images/Service_Consumption_1cdb46d.png)



### Example

Create a Service Consumption Model for remote consumption of your OData service. You have the metadata of the corresponding OData service that you want to consume in an XML or EDMX file.



### Step-by-step

See the following information for how to create your SRVC:

-   [Generating Proxies for Remote OData Service](https://help.sap.com/docs/btp/sap-abap-development-user-guide/generating-proxies-for-remote-odata-service?version=Cloud)
-   [Generating Proxies for Remote Function Call \(RFC\)](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/32812d950d3848359ce391dae477f201.html?q=generating%20proxies)
-   [Generating Proxies for Remote Web Service](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/3b9c145adad147058177cec27cef1f44.html)



<a name="loioed5d88ea66ce439398c37fe3dfc2cfd5__section_jkb_wkd_vtb"/>

## Constraints

Not all OData service model features are supported for Service Consumption Models. For example, you might not be able to create a Service Consumption Model for your underlying OData service. This is the case if your Service Model contains Complex Collections, Actions, or Functions.

