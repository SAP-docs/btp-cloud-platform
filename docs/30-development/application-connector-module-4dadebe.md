<!-- loio4dadebea59a74c20a5b22447cf68c7e3 -->

# Application Connector Module

With the Application Connector module, you can connect your workflows deployed on Kyma with external solutions. No matter if you want to integrate an on-premise or a cloud system, the integration process does not change, which prevents any configuration or network-related problems.



<a name="loio4dadebea59a74c20a5b22447cf68c7e3__section_h2t_yq2_qbc"/>

## What is Application Connectivity in Kyma?

Application Connectivity in Kyma simplifies the interaction between external systems and your Kyma workloads. The main benefits are:

-   Smooth and loosely coupled integration of external systems with Kyma workloads using [Kyma Eventing](https://kyma-project.io/#/eventing-manager/user/README)

-   Easy consumption of SAP BTP services by supporting the SAP BTP Extensibility approach

-   Establishing high-security standards for any interaction between systems by using trusted communication channels and authentication methods

-   Reducing configuration changes for Kyma workloads through encapsulating configuration details of external API endpoints

-   Monitoring and tracing capabilities to facilitate operational aspects


The Application Connector module bundles all features of Application Connectivity in Kyma. You can [install and manage the module using Kyma dashboard](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

The module includes Kubernetes operators and is fully configurable over its own Kubernetes custom resources \(CRs\). For each external system, a dedicated configuration is used. This allows for individual configuration of security and aspects \(like encryption and authentication\) per system.

Besides proxying any ingress and egress requests to external systems and dealing with security concerns, it also includes full integration with SAP BTP Unified Customer Landscape \(UCL\) to simplify the consumption of SAP BTP services.



<a name="loio4dadebea59a74c20a5b22447cf68c7e3__section_prg_1r2_qbc"/>

## Features

The Application Connector module provides the following features:

-   Easy installation of Kyma's Application Connectivity capabilities by enabling the Application Connector module in your SAP BTP, Kyma runtime.

-   Simple configuration using Kubernetes CRs and easy management with Kyma dashboard.

-   Full integration of BTP's UCL service, which implements the SAP BTP Extensibility concept. This allows for the automated integration of external systems registered in the UCL service.

-   Dispatching of incoming requests from external systems to Kyma workloads \(for example, a [Kyma Serverless Function](https://kyma-project.io/external-content/serverless/docs/user/README.html)\) by using an Istio Gateway with mTLS and the [Kyma Eventing module](https://kyma-project.io/#/eventing-manager/user/README).

-   Proxying outgoing requests to external APIs and transparently covering security requirements like encryption and authentication \(like OAuth 2.0 + mTLS, Basic Auth, and Client Certificates\).

-   Metering of throughput and exposing monitoring metrics.




<a name="loio4dadebea59a74c20a5b22447cf68c7e3__section_ixg_1r2_qbc"/>

## Architecture

![](images/ACM_Architecture_1292486.svg)





### Application Connector Manager

When you add the Application Connector module, Application Connector Manager takes care of installation and configuration of all the Application Connector module components in your cluster. It manages the lifecycle of the Application Connector module based on the dedicated `ApplicationConnector` custom resource \(CR\).



<a name="loio4dadebea59a74c20a5b22447cf68c7e3__section_j3q_qr2_qbc"/>

## API/Custom Resource Definitions

The API of the Applicaton Connector module is based on Kubernetes Custom Resource Definitions \(CRD\), which extend the Kubernetes API with custom additions. To inspect the specification of the Application Connector module API, see:

-   [Application CRD](https://kyma-project.io/#/application-connector-manager/user/resources/04-10-application)

-   [CompassConnection CRD](https://kyma-project.io/#/application-connector-manager/user/resources/04-20-compassconnection)

-   [ApplicationConnector CRD](https://kyma-project.io/#/application-connector-manager/user/resources/04-30-application-connector)




<a name="loio4dadebea59a74c20a5b22447cf68c7e3__section_u2c_qr2_qbc"/>

## Resource Consumption

To learn more about the resources used by the Application Connector module, see [Application Connector](../50-administration-and-ops/kyma-modules-sizing-3a92490.md#loio3a924906857b4f01969cb684ccd25309__section_application_connector).





<a name="loio4dadebea59a74c20a5b22447cf68c7e3__section_hlf_132_xcc"/>

## Useful Links

To learn more how to work with the Application Connector module, see the [Application Connectivity tutorials](https://kyma-project.io/#/application-connector-manager/user/tutorials/README).

To learn more about the architecture, the configuration parameters, and any other references, see [Technical Reference](https://kyma-project.io/#/application-connector-manager/user/technical-reference/README).

