<!-- loio3cee866c27ec4492b789b10c5d52d94b -->

# SAP Java Connector

The SAP Java buildpack provides an option to use the SAP Java Connector.



<a name="loio3cee866c27ec4492b789b10c5d52d94b__section_if3_xck_kgb"/>

## Activation

The SAP Java buildpack provides an option to use the [SAP Java Connector \(SAP JCo\)](https://support.sap.com/en/product/connectors/jco.html).

To activate SAP JCo in the SAP Java buildpack, set the environment variable *<USE\_JCO\>* to `true`:

> ### Sample Code:  
> manifest.yml
> 
> ```
> ---
> applications:
> - name: <APP_NAME>
>   ...
>   env:
>     USE_JCO: true
> ```

The previous method of activating the SAP JCo feature by defining a service instance for both the connectivity and destination services in the `manifest.yml` has been deprecated and stops working at the end of a transition phase.

The activation of SAP JCo will provide all relevant libraries in the application container, so the [Java Connector API](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d917276b236f45f9960442bebf262dab.html "The Java Connector (JCo) is a middleware component that enables you to develop ABAP-compliant components and applications in Java.") :arrow_upper_right: can be used. To use SAP JCo during runtime, a destination and XSUAA service instance are mandatory. Additionally, if you want to set up on-premise connectivity, a connectivity service instance is required.



<a name="loio3cee866c27ec4492b789b10c5d52d94b__section_xf4_xnd_fhb"/>

## Limitations

SAP JCo is only available for the Tomcat-based application containers that are included in the SAP Java Buildpack. Spring Boot applications only work with SAP JCo if you're using WAR deployment.

**Related Information**  


[Invoking ABAP Function Modules via RFC (Neo)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/628bae0298e6451b998127830975a7f3.html "Call a remote-enabled function module in an on-premise ABAP server from your Neo application, using the RFC protocol.") :arrow_upper_right:

[Invoking ABAP Function Modules via RFC](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/fa4adc9bd40e45dbac573fd616695446.html "Call a remote-enabled function module in an on-premise or cloud ABAP server from your Cloud Foundry application, using the RFC protocol.") :arrow_upper_right:

[Invoke ABAP Function Modules in On-Premise ABAP Systems](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/0a238b915b3a48adb950e5807654226c.html "") :arrow_upper_right:

[About JCo](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/fa4adc9bd40e45dbac573fd616695446.html "Call a remote-enabled function module in an on-premise or cloud ABAP server from your Cloud Foundry application, using the RFC protocol.") :arrow_upper_right:

