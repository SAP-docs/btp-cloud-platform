<!-- loioeba113235f52423b8bc0a571842fb5e6 -->

# Configuring Registry Cache

Create a `RegistryCacheConfig` custom resource \(CR\) to enable caching for an upstream container image registry in your SAP BTP, Kyma runtime instance.



<a name="loioeba113235f52423b8bc0a571842fb5e6__prereq_configure_rcc"/>

## Prerequisites

-   You have a Kyma instance created.
-   You have administrative access to the Kyma runtime with kubeconfig and kubectl. See [Access a Kyma Instance Using kubectl](https://help.sap.com/docs/btp/sap-business-technology-platform/access-kyma-instance-using-kubectl?locale=en-US&version=Cloud).
-   You have the Registry Cache module added. See [Adding and Deleting a Kyma Module](https://help.sap.com/docs/btp/sap-business-technology-platform-internal/enable-and-disable-kyma-module?locale=en-US&state=DRAFT&version=Internal#loio1b548e9ad4744b978b8b595288b0cb5c).



<a name="loioeba113235f52423b8bc0a571842fb5e6__context_configure_rcc"/>

## Context

`RegistryCacheConfig` is a namespace-scoped resource and can be created in any namespace.



## Procedure

1.  Create the `test` namespace if it doesn't exist.

    ```
    kubectl create namespace test
    ```

2.  Create a `RegistryCacheConfig` CR.

    ```
    kubectl create -f - <<EOF
    apiVersion: core.kyma-project.io/v1beta1
    kind: RegistryCacheConfig
    metadata:
      name: config1
      namespace: test
    spec:
      upstream: docker.io
      volume:
        size: 100Gi
    EOF
    ```

    When applied, Kyma Control Plane \(KCP\) processes the resource and configures a caching layer for the specified upstream registry \(in this case, `docker.io`\). The `volume.size` field specifies the size of the persistent volume used to store cached images.

    You can create multiple `RegistryCacheConfig` resources to cache different upstream registries. Each resource must have a unique name, and each upstream registry must be unique across all resources in the cluster.

3.  Verify that KCP processed the resource successfully by checking its status:

    ```
    kubectl get registrycacheconfig <name> -n <namespace> -o jsonpath='{.status.state}'
    ```

    The expected output values are the following:

    -   *Pending* — KCP is processing the configuration.
    -   *Ready* — the caching layer has been configured successfully.
    -   *Error* — KCP encountered an issue and is retrying. The state transitions to `Ready` automatically when processing succeeds.


