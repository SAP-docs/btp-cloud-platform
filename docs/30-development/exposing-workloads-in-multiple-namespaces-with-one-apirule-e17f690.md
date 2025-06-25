<!-- loioe17f6904f62c448480381ccddac46532 -->

# Exposing Workloads in Multiple Namespaces with One APIRule

Learn how to expose Service endpoints in multiple namespaces.



<a name="loioe17f6904f62c448480381ccddac46532__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and configure it to interact with your Kyma runtime instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).
-   You have installed [curl](https://curl.se/).
-   You have two deployed workloads in different namespaces.

    > ### Note:  
    > To expose a workload using APIRule in version `v2`, the workload must be a part of the Istio service mesh. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

-   You have [set up your custom domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload). Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`.

    > ### Note:  
    > Because the default Kyma domain is a wildcard domain, which uses a simple TLS Gateway, it is recommended that you set up your custom domain for use in a production environment.

    > ### Tip:  
    > To learn what the default domain of your Kyma cluster is, run the following command:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}'
    > ```




<a name="loioe17f6904f62c448480381ccddac46532__context_lsv_pjz_x2c"/>

## Context

Expose two workloads deployed in different namespaces with one APIRule definition.

> ### Caution:  
> Exposing a workload to the outside world is a potential security vulnerability, so be careful. In a production environment, always secure the workload you expose.



## Procedure

You can use either Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  Create a namespace with the Istio sidecar proxy injection enabled.

        For more information, see [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

    2.  Go to *Discovery and Network \> API Rules* and select *Create*.

    3.  Switch to the *YAML* section.

    4.  Paste the following APIRule custom resource \(CR\) and replace the placeholders:

        ```
        apiVersion: gateway.kyma-project.io/v2
        kind: APIRule
        metadata:
          name: {APIRULE_NAME}
          namespace: {APIRULE_NAMESPACE}
        spec:
          hosts:
            - {SUBDOMAIN}.{DOMAIN_NAME}
          gateway: {GATEWAY_NAMESPACE}/{GATEWAY_NAME}
          rules:
            - path: /headers
              methods: ["GET"]
              service:
                name: {FIRST_SERVICE_NAME}
                namespace: {FIRST_SERVICE_NAMESPACE}
                port: {FIRST_SERVICE_PORT}
              noAuth: true
            - path: /get
              methods: ["GET"]
              service:
                name: {SECOND_SERVICE_NAME}
                namespace: {SECOND_SERVICE_NAMESPACE}
                port: {SECOND_SERVICE_PORT}
              noAuth: true
        ```

    5.  Select *Create*.

    6.  To call the endpoints, send `GET` requests to the exposed Services:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
        
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/get
        ```

        If successful, the calls return the `200 OK` response code.


-   Use kubectl.

    1.  Create a separate namespace for the APIRule CR with enabled Istio sidecar proxy injection.

        ```
        export NAMESPACE={NAMESPACE_NAME}
        kubectl create ns $NAMESPACE
        kubectl label namespace $NAMESPACE istio-injection=enabled --overwrite
        ```

    2.  Expose the Services in their respective namespaces by creating an APIRule custom resource \(CR\) in its own namespace. Run:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: gateway.kyma-project.io/v2
        kind: APIRule
        metadata:
          name: {APIRULE_NAME}
          namespace: $NAMESPACE
        spec:
          hosts:
            - {SUBDOMAIN}.{DOMAIN_NAME}
          gateway: {GATEWAY_NAMESPACE}/{GATEWAY_NAME}
          rules:
            - path: /headers
              methods: ["GET"]
              service:
                name: {FIRST_SERVICE_NAME}
                namespace: {FIRST_SERVICE_NAMESPACE}
                port: {FIRST_SERVICE_PORT}
              noAuth: true
            - path: /get
              methods: ["GET"]
              service:
                name: {SECOND_SERVICE_NAME}
                namespace: {SECOND_SERVICE_NAMESPACE}
                port: {SECOND_SERVICE_PORT}
              noAuth: true
        EOF
        ```

    3.  To call the endpoints, send `GET` requests to the exposed Services:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
        
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/get
        ```

        If successful, the calls return the `200 OK` response code.



