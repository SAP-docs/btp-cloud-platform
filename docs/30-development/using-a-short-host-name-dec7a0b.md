<!-- loiodec7a0b1573c474293d7e36412a4b9a8 -->

# Using a Short Host Name

Learn how to expose a Service instance using a short host name instead of the full domain name.



<a name="loiodec7a0b1573c474293d7e36412a4b9a8__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have installed [curl](https://curl.se/) and [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl). You have configured kubectl to communicate with your Kyma runtime instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).
-   You have a deployed workload.

    > ### Note:  
    > To expose a workload using APIRule in version `v2`, the workload must be a part of the Istio service mesh. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

-   You have [set up your custom domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload). Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`.

    > ### Note:  
    > Because the default Kyma domain is a wildcard domain, which uses a simple TLS Gateway, it is recommended that you set up your custom domain for use in a production environment.

    > ### Tip:  
    > To learn what the default domain of your Kyma cluster is, run the following command:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}
    > ```




<a name="loiodec7a0b1573c474293d7e36412a4b9a8__context_rbx_bxg_y2c"/>

## Context

Using a short host makes it simpler to apply an APIRule custom resource \(CR\) because the domain name is automatically retrieved from the referenced Gateway, and you don’t have to manually set it in each APIRule. This might be particularly useful when reconfiguring resources in a new cluster, as it reduces the risk of errors and streamlines the process.



## Procedure

1.  To expose your workload using a short host, create an APIRule CR and define only a subdomain in the `hosts` field. See the following example:

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: gateway.kyma-project.io/v2alpha1
    kind: APIRule
    metadata:
      name: {APIRULE_NAME}
      namespace: {APIRULE_NAMESPACE}
    spec:
      hosts:
        - {SUBDOMAIN}
      service:
        name: {SERVICE_NAME}
        namespace: {SERVICE_NAMESPACE}
        port: {SERVICE_PORT}
      gateway: {NAMESPACE/GATEWAY}
      rules:
        - path: /*
          methods: ["GET"]
          noAuth: true
        - path: /post
          methods: ["POST"]
          noAuth: true
    EOF
    ```

2.  Send a `GET` request to the exposed workload:

    ```
    curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/ip
    ```

    If successful, the call returns the `200 OK` response code.

3.  Send a `POST` request to the exposed workload:

    ```
    curl -ik -X POST https://{SUBDOMAIN}.{DOMAIN_NAME}/post -d "test data"
    ```

    If successful, the call returns the `200 OK` response code.


