<!-- loio0dda141a58d54f29a860a4b3164bf4a9 -->

# Kyma Modules

With Kyma's modular approach, you can install just the modules you need, instead of a predefined set of components.



You can choose to add any modules as required. To learn how, see [Add and Delete a Kyma Module](../50-administration-and-ops/add-and-delete-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c). To find out which module version is running on your cluster, go to Kyma dashboard.

> ### Tip:  
> A release of a new module’s version is announced with a release note in [What’s New for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&version=Cloud) for both, the fast and regular channels:
> 
> -   On the day of the release in the fast channel, a release note is published with the *Preview* label.
> 
> -   When the module version becomes available in the regular channel \(after approximately two weeks\), the *Preview* label is removed.



<a name="loio0dda141a58d54f29a860a4b3164bf4a9__section_y2m_kzd_nzb"/>

## Default Kyma Modules

When you create Kyma runtime in SAP BTP cockpit, it is provisioned with the default modules added. The default modules are not mandatory. If you don't need them, you can delete them in [Kyma dashboard](https://dashboard.kyma.cloud.sap/clusters).

**Default Kyma Modules**


<table>
<tr>
<th valign="top">

Module

Technical name

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

*API Gateway*

`api-gateway`

</td>
<td valign="top">

API Gateway provides functionalities that allow you to expose and secure APIs.

</td>
<td valign="top">

[kyma-project.io: API Gateway module](https://kyma-project.io/#/api-gateway/user/README)

</td>
</tr>
<tr>
<td valign="top">

*Istio*

`istio`

</td>
<td valign="top">

Istio is a service mesh with Kyma-specific configuration.

</td>
<td valign="top">

[kyma-project.io: Istio module](http://kyma-project.io/#/istio/user/README)

</td>
</tr>
<tr>
<td valign="top">

*SAP BTP Operator*

`btp-operator`

</td>
<td valign="top">

Within the SAP BTP Operator module, BTP Manager installs the SAP BTP service operator that allows you to consume SAP BTP services from your Kubernetes cluster using Kubernetes-native tools.

</td>
<td valign="top">

-   [Using SAP BTP Services in the Kyma Environment](../30-development/using-sap-btp-services-in-the-kyma-environment-ea4dd81.md#loioea4dd81e49254dd482d32e3c20f4477a)
-   [kyma-project.io: SAP BTP Operator module](https://kyma-project.io/#/btp-manager/user/README)
-   [GitHub: BTP Manager releases](https://github.com/kyma-project/btp-manager/releases)
-   [GitHub: SAP BTP service operator releases](https://github.com/SAP/sap-btp-service-operator/releases)



</td>
</tr>
</table>



<a name="loio0dda141a58d54f29a860a4b3164bf4a9__section_zty_yc2_lzb"/>

## Non-Default Kyma Modules

When you create Kyma runtime in SAP BTP cockpit, the following modules are not added by default, but you can choose to add \(and delete\) them anytime.

**Non-Default Kyma Modules**


<table>
<tr>
<th valign="top">

Module

Technical name

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

*Application Connector*

`application-connector`

</td>
<td valign="top">

Application Connector allows you to connect with external solutions. No matter if you want to integrate an on-premise or a cloud system, the integration process doesn't change, which allows you to avoid any configuration or network-related problems.

</td>
<td valign="top">

-   [kyma-project.io: What is Application Connectivity in Kyma?](https://kyma-project.io/#/application-connector-manager/user/README)
-   [GitHub repository: Application Connector Manager](https://github.com/kyma-project/application-connector-manager) 



</td>
</tr>
<tr>
<td valign="top">

*Keda*

`keda`

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

`serverless`

</td>
<td valign="top">

With the Serverless module, you can define simple code snippets \(Functions\) with minimal implementation effort.

</td>
<td valign="top">

-   [Deploy Workloads in the Kyma Environment to Extend SAP Systems](../30-development/deploy-workloads-in-the-kyma-environment-to-extend-sap-systems-fe4ba5b.md)
-   [kyma-project.io: What is Serverless in Kyma?](https://kyma-project.io/#/serverless-manager/user/README)
-   [kyma-project.io: Serverless Configuration](https://kyma-project.io/#/serverless-manager/user/00-20-configure-serverless)
-   [GitHub repository: Serverless](https://github.com/kyma-project/serverless-manager)



</td>
</tr>
<tr>
<td valign="top">

*Telemetry*

`telemetry`

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

`nats`

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

*Eventing*

`eventing`

</td>
<td valign="top">

Eventing provides functionality to publish and subscribe to CloudEvents.

At the moment, the SAP Event Mesh default plan and NATS are supported. If you choose NATS, add the NATS module.

</td>
<td valign="top">

-   [Configure SAP Event Mesh for Kyma Eventing](../30-development/configure-sap-event-mesh-for-kyma-eventing-407d126.md)
-   [kyma-project.io: Eventing module](https://kyma-project.io/#/eventing-manager/user/README)
-   [GitHub repository: Eventing](https://github.com/kyma-project/eventing-manager) 



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

Technical name

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

`transparent-proxy`

</td>
<td valign="top">

Use the transparent proxy for Kubernetes to connect workloads on a Kubernetes cluster to Internet and on-premise applications.

</td>
<td valign="top">

-   [Transparent Proxy in the Kyma Environment](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-in-kyma-environment?version=Cloud)



</td>
</tr>
<tr>
<td valign="top">

*Connectivity Proxy*

`connectivity-proxy`

</td>
<td valign="top">

Use the connectivity proxy for Kubernetes to connect workloads on a Kubernetes cluster to on-premise systems, exposed via the Cloud Connector.

</td>
<td valign="top">

[On-Premise Connectivity in the Kyma Environment](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/on-premise-connectivity-in-kyma-environment?version=Cloud)

</td>
</tr>
</table>



