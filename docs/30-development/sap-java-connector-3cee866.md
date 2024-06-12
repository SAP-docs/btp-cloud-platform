<!-- loio3cee866c27ec4492b789b10c5d52d94b -->

# SAP Java Connector

You can use the SAP Java Connector through the SAP Java buildpacks.



<a name="loio3cee866c27ec4492b789b10c5d52d94b__section_if3_xck_kgb"/>

## Activation

SAP Java Buildpack \(1 and 2\) provide an option to use [SAP Java Connector \(SAP JCo\)](https://support.sap.com/en/product/connectors/jco.html).

To activate SAP JCo in the buildpack, set the environment variable `USE_JCO` to *true*.

> ### Sample Code:  
> manifest.yml
> 
> ```
> ---
> applications:
> - name: <app_name>
>   ...
>   env:
>     USE_JCO: true
> ```

The previous method of activating the SAP JCo feature, by defining a service instance for both the connectivity and destination services in the `manifest.yml` file, has been deprecated and stops working at the end of a transition phase.

The activation of SAP JCo provides all relevant libraries in the application container, so that [SAP JCo API](https://support.sap.com/en/product/connectors/jco.html?anchorId=section_1355144687) can be used. To use SAP JCo during runtime, a destination and an SAP Authorization and Trust Management \(XSUAA\) service instance are mandatory. Additionally, if you want to set up on-premise connectivity, a connectivity service instance is required.



<a name="loio3cee866c27ec4492b789b10c5d52d94b__section_xf4_xnd_fhb"/>

## Limitations

SAP JCo is only available for the Tomcat-based application containers that are included in the SAP Java buildpacks. Spring Boot applications only work with SAP JCo if you're using WAR deployment.

**Related Information**  


[Invoking ABAP Function Modules via RFC](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/fa4adc9bd40e45dbac573fd616695446.html "Call a remote-enabled function module in an on-premise or cloud ABAP server from your application, using the RFC protocol.") :arrow_upper_right:

[Invoke ABAP Function Modules in On-Premise ABAP Systems](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/bfcb54ca058f4b1dafd26e438ff1e2f4.html "Call a function module in an on-premise ABAP system via RFC, using a sample Web application.") :arrow_upper_right:

