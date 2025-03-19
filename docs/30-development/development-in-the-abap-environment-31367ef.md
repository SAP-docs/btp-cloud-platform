<!-- loio31367ef6c3e947059e0d7c1cbfcaae93 -->

# Development in the ABAP Environment

Learn more about developing applications in the ABAP environment.



## Overview

The ABAP environment is a platform as a service that allows you to extend existing ABAP-based applications and develop ABAP cloud apps decoupled from the digital core. You can leverage your ABAP know-how in the cloud and reuse existing ABAP assets by writing your source code with ABAP Development Tools for Eclipse.

The ABAP environment enables you to **expose**:

-   OData services. See [ABAP RESTful Application Programming Model](https://help.sap.com/docs/abap-cloud/abap-rap/abap-restful-application-programming-model?version=sap_btp).

-   HTTP services. See [Working with the HTTP Service Editor](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/494a02697388437aa71067dd95b2c561.html).
-   SQL services. See [Data Federation Using the SQL Service](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/data-federation).
-   RFC function modules. See [Providing an RFC Service](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/provide-rfc-service).
-   SOAP provider model. See [Providing a SOAP Service](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/provide-soap-service).


With your ABAP applications, you can **consume**:

-   HTTP services \(HTTP client\). See [Outbound HTTP Administration Tasks](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/outbound-http-administration-tasks).

-   OData services \(service consumption model\). See [Developing a UI Service with Access to a Remote Service](https://help.sap.com/docs/abap-cloud/abap-rap/developing-ui-service-with-access-to-remote-service?version=sap_btp).
-   Remote Function Calls \(RFC\). See [Outbound RFC Administration Tasks](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/outbound-rfc-administration-tasks).
-   On-premise systems via Cloud Connector. See [Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md).
-   SOAP-based Web services. See [Outbound SOAP Administration Tasks](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/outbound-soap-administration-tasks).



<a name="loio31367ef6c3e947059e0d7c1cbfcaae93__section_qml_szm_j1c"/>

## Technical Limits and Boundary Conditions for ABAP Applications

For elasticity, operability and protection reasons, the runtime of API or UI requests to ABAP applications is limited. After 10 minutes, running requests are automatically canceled. Tasks requiring longer runtimes have to be executed in [Application Jobs](https://help.sap.com/docs/btp/sap-business-technology-platform/application-jobs-2), as background processes via the background processing framework \(bgPF\), or need to be split into smaller work packages. For an optimal user experience, all ABAP applications, including application jobs, have to be prepared to be interrupted and restarted even earlier than the maximum runtime. This allows to provide a continuous application service, unimpacted from scaling operations, maintenance activities or even infrastructure failures.



<a name="loio31367ef6c3e947059e0d7c1cbfcaae93__section_qlm_pls_n2b"/>

## Development Resources

[ABAP RESTful Application Programming Model](https://help.sap.com/docs/abap-cloud/abap-rap/abap-restful-application-programming-model?version=sap_btp)

[ABAP Development Tools for Eclipse: User Guide](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/about-abap-development-tools-user-guide?version=sap_btp)

[ABAP CDS Development User Guide](https://help.sap.com/docs/abap-cloud/abap-cds-tools-user-guide/about-abap-cds-development-tools-user-guide?version=sap_btp)

[Generative AI in ABAP Cloud](https://help.sap.com/docs/abap-ai/generative-ai-in-abap-cloud/generative-ai-in-abap-cloud?locale=en-US)

[ABAP Keyword Documentation](abap-keyword-documentation-1632c79.md)

[ABAP Lifecycle Management](abap-lifecycle-management-5c7b17d.md)

[Connect to the ABAP System](connect-to-the-abap-system-7379dbd.md)

[Providing an HTTP Service](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/provide-http-service)

[Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md)

[Supported Protocols and Authentication Methods](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/supported-protocols-and-authentication-methods)

[Inbound Communication](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/inbound-communication-4a091c967fd44ab7ba7d9c4429979b1e)

[Working with abapGit](working-with-abapgit-d62ed9d.md)

**Related Information**  


[Eclipse Tool for the ABAP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/54dd7126d5b74efeb7a21f6b0bfe5f1a.html)

[Learning Journey](https://help.sap.com/doc/221f8f84afef43d29ad37ef2af0c4adf/HP_2.0/en-US/49047e7668844d419ccee567923a475e.html)

[Manage Software Components](../50-administration-and-ops/manage-software-components-3dcf76a.md "You can use this app to create, display, clone, delete and configurate software components in your ABAP environment landscape. Moreover, you can pull (import) changes from the central software component into other instances.")

[Video Tutorials](https://www.youtube.com/playlist?list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr)

