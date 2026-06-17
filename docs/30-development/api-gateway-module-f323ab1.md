<!-- loiof323ab16595a47779bc74344969c0133 -->

# API Gateway Module

API Gateway is a Kyma module with which you can expose and secure APIs.



<a name="loiof323ab16595a47779bc74344969c0133__section_what_is_api_gateway"/>

## What Is API Gateway?

To use the API Gateway module, you must also add the Istio module. Moreover, to expose a workload using the `APIRule` custom resource \(CR\), the workload must be part of the Istio service mesh.

By default, both the API Gateway and Istio modules are automatically added when you create a SAP BTP, Kyma runtime instance.



<a name="loiof323ab16595a47779bc74344969c0133__section_features"/>

## Features

The API Gateway module offers the following features:

-   API exposure: The module uses Istio features to help you easily and securely expose your workloads by creating `APIRule` CRs. With an `APIRule`, you can perform the following actions:

    -   Group multiple workloads and expose them under a single host.
    -   Use a short host name to simplify the migration of resources to a new cluster.
    -   Configure the *noAuth* access strategy, which offers a simple configuration to allow access to specific HTTP methods.
    -   Secure your workloads by configuring *jwt* or *extAuth* access strategies. The *jwt* access strategy enables you to use Istio's JWT configuration to protect your exposed services and interact with them using JSON Web Tokens. The *extAuth* access strategy allows you to implement custom authentication and authorization logic.

-   Default Kyma gateway configuration: The module creates and manages the default Istio TLS Gateway that receives incoming traffic in your Kyma cluster. The gateway uses the cluster's default domain and a self-signed certificate.
-   Rate limiting: The module simplifies local rate limiting on the Istio service mesh layer. By configuring a `RateLimit` CR, you can limit the number of requests targeting an exposed application in a unit of time, based on specific paths and headers.
-   External gateway integration: Configure Istio mTLS Gateway and integrate it with an external gateway deployed outside of the Kyma cluster.



<a name="loiof323ab16595a47779bc74344969c0133__section_architecture"/>

## Architecture

Within the API Gateway module, API Gateway Operator manages the application of API Gateway's configuration and handles resource reconciliation. It contains the following controllers: APIGateway Controller, APIRule Controller, RateLimit Controller, and ExternalGateway Controller.

![Architecture diagram showing the Kyma API Gateway Operator overview. The operator manages API Gateway configuration and resource reconciliation, containing four controllers: APIGateway Controller, APIRule Controller, RateLimit Controller, and ExternalGateway Controller.](images/API_Gateway_Module_s_Architecture_f88a5ae.png)



<a name="loiof323ab16595a47779bc74344969c0133__section_api_crd"/>

## API/Custom Resource Definitions

The `apigateways.operator.kyma-project.io` CustomResourceDefinition \(CRD\) describes the `APIGateway` CR that APIGateway Controller uses to manage the module and its resources. See [APIGateway Custom Resource](https://kyma-project.io/external-content/api-gateway/docs/user/custom-resources/apigateway/04-00-apigateway-custom-resource.html).

The `apirules.operator.kyma-project.io` CRD describes the `APIRule` CR that APIRule Controller uses to expose and secure APIs. See [APIRule Custom Resource](https://kyma-project.io/external-content/api-gateway/docs/user/custom-resources/apirule/04-10-apirule-custom-resource.html).

The `externalgateways.gateway.kyma-project.io` CRD describes the kind and the format of data that ExternalGateway Controller uses to configure external gateway integration. See [ExternalGateway Custom Resource](https://kyma-project.io/external-content/api-gateway/docs/user/custom-resources/externalgateway/externalgateway-custom-resource.html).

The `ratelimits.gateway.kyma-project.io` CRD describes the kind and the format of data that RateLimit Controller uses to configure request rate limits for applications. See [RateLimit Custom Resource](https://kyma-project.io/external-content/api-gateway/docs/user/custom-resources/ratelimit/04-10-ratelimit-custom-resource.html).



<a name="loiof323ab16595a47779bc74344969c0133__section_authorization"/>

## Authorization

To assign access permissions to the API Gateway module resources, use the following [aggregated ClusterRoles](https://kubernetes.io/docs/reference/access-authn-authz/rbac/#aggregated-clusterroles):

-   `kyma-api-gateway-view` - Grants read-only access to all API Gateway resources.
-   `kyma-api-gateway-edit` - Grants full access to `gateway.kyma-project.io` resources and read-only access to `operator.kyma-project.io` resources.
-   `kyma-api-gateway-admin` - Grants full access to all API Gateway resources.



<a name="loiof323ab16595a47779bc74344969c0133__section_resource_consumption"/>

## Resource Consumption

To learn more about the resources used by the Istio module, see [Kyma Modules' Sizing](https://help.sap.com/docs/btp/sap-business-technology-platform-internal/kyma-modules-sizing?locale=en-US&state=DRAFT&version=Internal&comment_id=22217515&show_comments=true#api-gateway).

