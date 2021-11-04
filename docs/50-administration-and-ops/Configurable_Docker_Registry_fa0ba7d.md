<!-- loiofa0ba7d0ae084a13ba3dcc89927bb148 -->

# Configurable Docker Registry

Change the default Docker registry. Store all Function images from a given Namespace in an external registry of your choice.



In its default configuration, the Kyma environment uses persistent volumes as the internal registry to store Docker images for Functions. The default storage size of a single volume is 20 GB. This internal registry is suitable for local development. For production purposes, we recommend you use an external registry, such as [Docker Hub](https://hub.docker.com/), [Google Container Registry \(GCR\)](https://cloud.google.com/container-registry), or [Azure Container Registry \(ACR\)](https://azure.microsoft.com/en-us/services/container-registry/).



The Kyma environment gives you an option to switch at runtime to a chosen external registry in a given Namespace. To do that, create a Secret custom resource \(CR\) that meets these requirements:

-   Is named `serverless-registry-config`.

-   Is of type `kubernetes.io/dockerconfigjson`.

-   Has the `serverless.kyma-project.io/remote-registry: config` label.

-   Contains these keys with valid values pointing to the external registry:

    -   `username`

    -   `password`

    -   `serverAddress`

    -   `registryAddress`





See this example:

> ### Sample Code:  
> ```
>   apiVersion: v1
>   kind: Secret
>   type: kubernetes.io/dockerconfigjson
>   metadata:
>    name: serverless-registry-config
>    namespace: {VALUE}
>    labels:
>      serverless.kyma-project.io/remote-registry: config
>   data:
>    username: {VALUE}
>    password: {VALUE}
>    serverAddress: {VALUE}
>    registryAddress: {VALUE}
> ```



You can also add the `serverless.kyma-project.io/managed-by: user` label to the Secret CR. This way you make sure that your Namespace configuration will not be overridden by any cluster-wide configuration.



For detailed steps, see the [tutorial on switching between registries at runtime](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-serverless/svls-08-switch-to-external-registry/).



Learn more about:

-   [Registries in the Kyma environment](https://kyma-project.io/docs/kyma/latest/01-overview/main-areas/serverless/svls-03-container-registries/)


-   [Admission webhook and its role in the registry change process](https://kyma-project.io/docs/kyma/latest/05-technical-reference/svls-07-supported-webhooks/#admission-webhook)


