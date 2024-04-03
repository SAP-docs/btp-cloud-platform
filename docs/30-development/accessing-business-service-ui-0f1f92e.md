<!-- loio0f1f92e047924fdebe63d5249f532cdd -->

# Accessing Business Service UI

This section provides information about accessing Business Services UIs that are stored in HTML5 Application Repository.

Business Service UI's must be stored in HTML5 Application Repository and defined in their `manifest.json` files as `public: true` in order to be accessible from an application router application that is typically running in a different space than the Business Service space. In addition, dataSource URIs must be relative to the base URL, which means there is no need for a slash as the first character.

The following is an example `manifest.json` file of a Business Service:

> ### Sample Code:  
> ```
> {
>   "sap.app": {
>     "id":"com.sap.appbasic.country.list",
>     "applicationVersion: {
>     "version": "1.0.0"
>   },
>   "dataSources": {
>     "mainService":{
>       "uri": "odata/v2/countryservice",
>       "type": "OData"
>     }
>   },
>   "sap.cloud": {
>     "public": true,
>     "service": "com.sap.appbasic.country"
>   }
> }
> ```

A Business Service that exposes UI, must provide one or more `app-host` GUIDs in an `html5-apps-repo` block in VCAP\_SERVICES credentials.

To access the Business Service UI, the URL request to the application router must contain a business service prefix, as in the following example of a request URL:

> ### Sample Code:  
> ```
> https://tenant1.approuter-repo-examples.cfapps.sap.hana.ondemand.com/comsapappbasiccountry.comsapappbasicscountrylist/test/flpSandbox.html
> ```

In this example, `comsapappbasiccountry` is the business service prefix which matches the `sap.cloud.service` attribute in the country service VCAP\_SERVICES credentials \(without dots\). The `comsapappbasicscountrylist` is the name of the HTML5 application as defined in the `app.id` attribute in the `manifest.json` file \(without dots\).

**Related Information**  


[Integration with Business Services](integration-with-business-services-f6337cd.md "Application router supports integration with Business Services, which are a flavor of reuse-services.")

[Accessing Business Service Data](accessing-business-service-data-783809d.md "This section describes how the application router accesses the Business Service data.")

