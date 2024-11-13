<!-- loio50347eaa4f174ba782f89a00b1f2eac0 -->

# SAP BTP Operator Module

Use the SAP BTP Operator module to enable service management and consume SAP BTP services from your Kyma cluster.



<a name="loio50347eaa4f174ba782f89a00b1f2eac0__section_h2t_yq2_qbc"/>

## What Is SAP BTP Operator?

The SAP BTP Operator module provides service management, which allows you to consume [SAP BTP services](https://discovery-center.cloud.sap/protected/index.html#/viewServices) from your Kyma cluster using Kubernetes-native tools. Within the SAP BTP Operator module, [BTP Manager](https://github.com/kyma-project/btp-manager) installs the [SAP BTP service operator.](https://github.com/SAP/sap-btp-service-operator/blob/main/README.md) The SAP BTP service operator enables provisioning and managing service instances and service bindings of SAP BTP services. Consequently, your Kubernetes-native applications can access and use the services from your cluster.



<a name="loio50347eaa4f174ba782f89a00b1f2eac0__section_prg_1r2_qbc"/>

## Features

The SAP BTP Operator module provides the following features:

-   Credentials and access preconfiguration: Your Secret is readily available on Kyma runtime creation. See [Preconfigured Credentials and Access](preconfigured-credentials-and-access-ab106d7.md).

-   Multitenancy: You can configure multiple subaccounts in a single cluster. See [Working with Multiple Subaccounts](working-with-multiple-subaccounts-862dd6a.md).

-   Lifecycle management of service instances and service bindings: You can create and delete service instances and service bindings. See [Creating Service Instances and Service Bindings](creating-service-instances-and-service-bindings-17bd304.md) and [Deleting Service Bindings and Service Instances](deleting-service-bindings-and-service-instances-5deca69.md).

-   Service binding rotation: You can enhance security by automatically rotating the credentials associated with your service bindings. See [Rotating Service Bindings](rotating-service-bindings-37ac30a.md).

-   Service binding Secret formatting: You can use different attributes in your `ServiceBinding` resource to generate different formats of your Secret resources. See [Formatting Service Binding Secrets](formatting-service-binding-secrets-4733eb5.md).




<a name="loio50347eaa4f174ba782f89a00b1f2eac0__section_pvw_gr2_qbc"/>

## Scope

By default, the SAP BTP Operator module consumes SAP BTP services from the subaccount in which you created it. To consume the services from multiple subaccounts in a single Kyma cluster, configure a dedicated Secret for each additional subaccount.



<a name="loio50347eaa4f174ba782f89a00b1f2eac0__section_ixg_1r2_qbc"/>

## Architecture

The SAP BTP Operator module provides and retrieves the initial credentials that your application needs to use an SAP BTP service.

![](images/SAP_BTP_Operator_Architecture_315a173.svg)

Depending on the number of configured Secrets, SAP BTP Operator can have access to multiple subaccounts within your cluster.

![](images/Access_Configuration_1254684.svg)

For more information on multitenancy, see [Working with Multiple Subaccounts](working-with-multiple-subaccounts-862dd6a.md).



### SAP BTP, Kyma Runtime

SAP BTP, Kyma runtime runs on a Kubernetes cluster and wraps the SAP BTP Operator module, API server, and one or more applications. The application or multiple applications are the actual consumers of SAP BTP services.



### BTP Manager

BTP Manager is an operator based on the [Kubebuilder](https://github.com/kubernetes-sigs/kubebuilder) framework. It extends Kubernetes API by providing [BtpOperator Custom Resource Definition \(CRD\)](https://github.com/kyma-project/btp-manager/blob/main/config/crd/bases/operator.kyma-project.io_btpoperators.yaml).

BTP Manager performs the following operations:

-   Manages the lifecycle of the SAP BTP service operator, including provisioning of the latest version, updating, and deprovisioning.

-   Configures the SAP BTP service operator.




### SAP BTP Service Operator

The SAP BTP service operator is an open-source component that allows you to connect SAP BTP services to your cluster and manage them using Kubernetes-native tools. It is responsible for communicating with SAP Service Manager. The operator's resources, service instances and service bindings, come from the `services.cloud.sap.com` API group.



### SAP Service Manager

[SAP Service Manager](https://help.sap.com/docs/service-manager/sap-service-manager/sap-service-manager?locale=en-US&version=Cloud) is the central registry for service brokers and platforms in SAP BTP, which enables you to:

-   Consume platform services in any connected runtime environment.

-   Track the creation and management of service instances.

-   Share services and service instances between different runtimes.


SAP Service Manager uses [Open Service Broker API](https://www.openservicebrokerapi.org/) \(OSB API\) to communicate with service brokers.



### Service Brokers

Service brokers manage the lifecycle of services. SAP Service Manager interacts with service brokers using OSB API to provision and manage service instances and service bindings.



<a name="loio50347eaa4f174ba782f89a00b1f2eac0__section_j3q_qr2_qbc"/>

## API/Custom Resource Definitions

The `btpoperators.operator.kyma-project.io` Custom Resource Definition \(CRD\) describes the kind and the format of data that SAP BTP Operator uses to configure resources.

See the documentation related to the BtpOperator custom resource \(CR\):

-   [SAP BTP Operator Custom Resource](https://kyma-project.io/#/btp-manager/user/resources/02-10-sap-btp-operator-cr)

-   [Service Instance Custom Resource](https://kyma-project.io/#/btp-manager/user/resources/02-20-service-instance-cr)

-   [Service Binding Custom Resource](https://kyma-project.io/#/btp-manager/user/resources/02-30-service-binding-cr)




<a name="loio50347eaa4f174ba782f89a00b1f2eac0__section_u2c_qr2_qbc"/>

## Resource Consumption

To learn more about the resources used by the SAP BTP Operator module, see [SAP BTP Operator](../50-administration-and-ops/kyma-modules-sizing-3a92490.md#loio3a924906857b4f01969cb684ccd25309__section_sap_btp_operator).

