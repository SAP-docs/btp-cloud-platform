<!-- loiofa0ba7d0ae084a13ba3dcc89927bb148 -->

# Configure the Docker Registry

In its default configuration, Kyma environment uses persistent volumes as the internal registry to store Docker images for Functions. You can change the default Docker registry and store all Function images from a given Namespace in an external registry of your choice.



<a name="loiofa0ba7d0ae084a13ba3dcc89927bb148__context_xxy_grr_c5b"/>

## Context

This internal registry is suitable for local development. The default storage size of a single volume is 20 GB. You can check your current consumption with the Grafana Dashboard *Kubernetes / Persistent Volumes* \> *kyma-system* \> *serverless-docker-registry*.

For production purposes, we recommend you use an external registry, such as [Docker Hub](https://hub.docker.com/), [Google Container Registry \(GCR\)](https://cloud.google.com/container-registry), or [Azure Container Registry \(ACR\)](https://azure.microsoft.com/en-us/services/container-registry/).

In the Kyma environment, you can switch at runtime to a chosen external registry in a given Namespace. For detailed steps, see [Kyma: Switch to an external Docker registry at runtime](https://kyma-project.io/docs/kyma/latest/03-tutorials/00-serverless/svls-08-switch-to-external-registry/).



<a name="loiofa0ba7d0ae084a13ba3dcc89927bb148__steps_rhx_jrr_c5b"/>

## Procedure

1.  Create a Secret custom resource \(CR\) that meets the following requirements:

    -   Name: `serverless-registry-config`

    -   Type: `kubernetes.io/dockerconfigjson`

    -   Label: `serverless.kyma-project.io/remote-registry: config`

    -   Contains the following keys with valid values pointing to the external registry:

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
    >    registryAddress: {VALUE
    > ```

2.  To make sure that your Namespace configuration is not overridden by any cluster-wide configuration, add the label `serverless.kyma-project.io/managed-by: user` to the Secret CR.


**Related Information**  


[Kyma: Container registries](https://kyma-project.io/docs/kyma/latest/01-overview/main-areas/serverless/svls-03-container-registries)

[Kyma: Admission webhook and its role in the registry change process](https://kyma-project.io/docs/kyma/latest/05-technical-reference/svls-07-supported-webhooks#admission-webhook)

