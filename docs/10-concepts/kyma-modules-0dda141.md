<!-- loio0dda141a58d54f29a860a4b3164bf4a9 -->

# Kyma Modules

With Kyma's modular approach, you can install just the modules you need, instead of a predefined set of components.



You can choose to enable any modules as required. To learn how, see [Enable and Disable a Kyma Module](../50-administration-and-ops/enable-and-disable-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c). To find out which module version is running on your cluster, go to Kyma Dashboard.

> ### Remember:  
> One by one, all Kyma components are converted to modules that work independently from each other.
> 
> Table entries marked with “\*” are still components and will be modularized soon.



<a name="loio0dda141a58d54f29a860a4b3164bf4a9__section_rpm_hyz_jxb"/>

## Kyma Modules

**Kyma Modules**


<table>
<tr>
<th valign="top">

Module



</th>
<th valign="top">

Purpose



</th>
<th valign="top">

Documentation



</th>
</tr>
<tr>
<td valign="top">

*SAP BTP Operator* 



</td>
<td valign="top">

Within the SAP BTP Operator module, BTP Manager installs SAP BTP Service Operator that allows you to consume SAP BTP services from your Kubernetes cluster using Kubernetes-native tools.



</td>
<td valign="top">

-   [Using SAP BTP Services in the Kyma Environment](../30-development/using-sap-btp-services-in-the-kyma-environment-ea4dd81.md#loioea4dd81e49254dd482d32e3c20f4477a)
-   [kyma-project.io: SAP BTP Operator module](https://kyma-project.io/#/btp-manager/user/README)
-   [GitHub: BTP Manger releases](https://github.com/kyma-project/btp-manager/releases)
-   [GitHub: SAP BTP Service Operator releases](https://github.com/SAP/sap-btp-service-operator/releases)



</td>
</tr>
<tr>
<td valign="top">

*Keda* 



</td>
<td valign="top">

The Keda module comes with Keda Manager, an extension to Kyma that allows you to install [KEDA](https://keda.sh) \(Kubernetes Event Driven Autoscaler\).



</td>
<td valign="top">

-   [kyma-project.io: Keda module](https://kyma-project.io/#/keda-manager/user/README)



</td>
</tr>
<tr>
<td valign="top">

*Serverless* 



</td>
<td valign="top">

With the Serverless module, you can define simple code snippets \(Functions\) with minimal implementation effort.



</td>
<td valign="top">

-   [Deploy Workloads in the Kyma Environment to Extend SAP Systems](../30-development/deploy-workloads-in-the-kyma-environment-to-extend-sap-systems-fe4ba5b.md)
-   [kyma-project.io: What is Serverless in Kyma?](https://kyma-project.io/#/serverless-manager/user/README)
-   [GitHub repository: Serverless](https://github.com/kyma-project/serverless-manager)



</td>
</tr>
<tr>
<td valign="top">

*Telemetry* 



</td>
<td valign="top">

The Telemetry module collects application logs and distributed traces for your application, and dispatches them to your preferred backends.



</td>
<td valign="top">

-   [kyma-project.io: Telemetry module](https://kyma-project.io/#/telemetry-manager/user/README)
-   [GitHub: Telemetry manager releases](https://github.com/kyma-project/telemetry-manager/releases)
-   [GitHub repository: Telemetry](https://github.com/kyma-project/telemetry-manager)



</td>
</tr>
<tr>
<td valign="top">

*NATS* 



</td>
<td valign="top">

NATS deploys a NATS cluster within the Kyma cluster. You can use it as a backend for Kyma Eventing.



</td>
<td valign="top">

-   [kyma-project.io: NATS module](https://kyma-project.io/#/nats-manager/user/README)
-   [GitHub repository: NATS](https://github.com/kyma-project/nats-manager)



</td>
</tr>
<tr>
<td valign="top">

Eventing\*



</td>
<td valign="top">

Eventing provides functionality to publish and subscribe to CloudEvents.

At the moment, the SAP Event Mesh default plan and NATS \(provided by the NATS module\) are supported.



</td>
<td valign="top">

-   [Using Kyma Eventing with SAP Event Mesh](../30-development/using-kyma-eventing-with-sap-event-mesh-407d126.md)
-   [GitHub repository: Eventing](https://github.com/kyma-project/eventing-manager) 



</td>
</tr>
<tr>
<td valign="top">

Application Connector\*



</td>
<td valign="top">

Application Connector allows you to connect with external solutions. No matter if you want to integrate an on-premise or a cloud system, the integration process doesn't change, which allows you to avoid any configuration or network-related problems.



</td>
<td valign="top">

-   [GitHub repository: Application Connector default plan and NATS \(provided by the NATS module\) are supported.](https://github.com/kyma-project/application-connector-manager)



</td>
</tr>
<tr>
<td valign="top">

API Gateway\*



</td>
<td valign="top">

API Gateway provides functionalities that allow you to expose and secure APIs.



</td>
<td valign="top">

-   [default plan and NATS \(provided by the NATS module\) arekyma-project.io: API Gateway in Kyma](https://kyma-project.io/#/01-overview/api-exposure/apix-01-api-gateway)



</td>
</tr>
<tr>
<td valign="top">

Istio\*



</td>
<td valign="top">

Istio is a service mesh with Kyma-specific configuration.



</td>
<td valign="top">

-   [kyma-project.io: Istio Service Mesh](http://kyma-project.io/#/istio/user/00-overview/00-20-overview-service-mesh)



</td>
</tr>
</table>



<a name="loio0dda141a58d54f29a860a4b3164bf4a9__section_jcm_gyz_jxb"/>

## Third-Party Modules

**Third-Party Modules**


<table>
<tr>
<th valign="top">

Module



</th>
<th valign="top">

Purpose



</th>
<th valign="top">

Documentation



</th>
</tr>
<tr>
<td valign="top">

*Transparent Proxy* 



</td>
<td valign="top">

Use the transparent proxy for Kubernetes to connect workloads on a Kubernetes cluster to Internet and on-premise applications.



</td>
<td valign="top">

-   [Transparent Proxy in the Kyma Environment](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-in-kyma-environment?version=Cloud)



</td>
</tr>
</table>



