<!-- loio50ec2f8eae16460dbf5bef769b00a9d8 -->

# Service Consumption Model as OData Consumer

A Service Consumption Model is the main requirement for consuming an OData service in the ABAP environment. To learn how to create a Service Consumption Model with ABAP development tools for Eclipse \(ADT\), see [Creating Service Consumption Model](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/creating-service-consumption-model?version=sap_btp).

> ### Note:  
> We recommend to create a new package for the Service Consumption Model. Generated objects are then created within this package. This allows better organization and clarity.

A Service Consumption Model generates ABAP code from the service metadata file \(EDMX file\) of the OData service you want to consume. For every operation \(***Create***, ***Read***, ***Read List***, ***Update***, and ***Delete***\), a code snippet is generated that indicates how to perform the corresponding operation.

For more information on creating a Service Consumption Model, see [Generating Proxies for Remote OData Service](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/generating-proxies-for-remote-odata-service?version=sap_btp).

