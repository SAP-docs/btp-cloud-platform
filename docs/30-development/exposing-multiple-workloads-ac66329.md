<!-- loioac66329f84bd460d9e9db761983190fb -->

# Exposing Multiple Workloads

Learn how to expose multiple workloads with one APIRule definition.



<a name="loioac66329f84bd460d9e9db761983190fb__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and configure it to communicate with your Kyma runtime instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).
-   You have installed [curl](https://curl.se/).
-   You have deployed two workloads in one namespace.
-   You have [set up your custom domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload). Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`.

    > ### Note:  
    > Because the default Kyma domain is a wildcard domain, which uses a simple TLS Gateway, it is recommended that you set up your custom domain for use in a production environment.

    > ### Tip:  
    > To learn what the default domain of your Kyma cluster is, run the following command:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}'
    > ```


<a name="task_y55_k1q_x2c"/>

<!-- task\_y55\_k1q\_x2c -->

## Defining Multiple Services on Different Paths



<a name="task_y55_k1q_x2c__context_jww_m1q_x2c"/>

## Context

Learn how to expose two Services on different paths at the `spec.rules` level without a root Service defined.

> ### Caution:  
> Exposing a workload to the outside world is a potential security vulnerability, so be careful. In a production environment, always secure the workload you expose.



## Procedure

You can use either Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  Go to the namespace in which you want to create an APIRule CR.

    2.  Go to *Discovery and Network \> API Rules* and select *Create*.

    3.  Provide the name of the APIRule CR.

    4.  Add a Gateway.

    5.  Add a rule with the configuration details of one Service.

    6.  Add another rule with the configuration details of the other Service.

    7.  Choose *Create*.

    8.  To call the endpoints, send requests to the exposed Services, for example:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/get
        
        ```

        If successful, the calls return the `200 OK` response code.


-   Use kubectl.

    1.  Add two rules with configuration details of your Services. See an example:

        ```
        cat <<EOF | kubectl apply -f -
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
            noAuth: true
            service:
              name: {FIRST_SERVICE_NAME}
              port: {FIRST_SERVICE_PORT}
          - path: /get
            methods: ["GET"]
            noAuth: true
            service:
              name: {SECOND_SERVICE_NAME}
              port: {SECOND_SERVICE_PORT}
        EOF
        ```

    2.  To call the endpoints, send requests to the exposed Services, for example:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/get
        
        ```

        If successful, the calls return the `200 OK` response code.



<a name="task_os2_3bq_x2c"/>

<!-- task\_os2\_3bq\_x2c -->

## Defining a Service at the Root Level



<a name="task_os2_3bq_x2c__context_ps2_3bq_x2c"/>

## Context

You can also define a Service at the root level. Such a definition is applied to all the paths specified at **spec.rules** that do not have their own Services defined. Services defined at the **spec.rules** level have precedence over Service definition at the **spec.service** level.

> ### Caution:  
> Exposing a workload to the outside world is a potential security vulnerability, so be careful. In a production environment, always secure the workload you expose.



## Procedure

You can use either Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  Go to the namespace in which you want to create an APIRule CR.

    2.  Go to *Discovery and Network \> API Rules* and select *Create*.

    3.  Provide the name of the APIRule CR.

    4.  Add a Gateway.

    5.  Define one Service in the *Service* section.

    6.  Add one rule without a Service definition.

    7.  Add another rule with the Service definition.

    8.  Choose *Create*.

    9.  To call the endpoints, send requests to the exposed Services, for example:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/get
        
        ```

        If successful, the calls return the `200 OK` response code.


-   Use kubectl.

    1.  Replace the placeholders and run the following command:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: gateway.kyma-project.io/v2
        kind: APIRule
        metadata:
          name: {APIRULE_NAME}
          namespace: {APIRULE_NAMESPACE}
        spec:
          hosts:
            - {SUBDOMAIN}.{DOMAIN_NAME}
          gateway: {GATEWAY_NAMESPACE}/{GATEWAY_NAME}
          service:
            name: {FIRST_SERVICE_NAME}
            port: {FIRST_SERVICE_PORT}
          rules:
            - path: /headers
              methods: ["GET"]
              noAuth: true
            - path: /get
              methods: ["GET"]
              noAuth: true
              service:
                name: {SECOND_SERVICE_NAME}
                port: {SECOND_SERVICE_PORT}
        EOF
        ```

    2.  To call the endpoints, send `GET` requests to the exposed Services:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/get
        
        ```

        If successful, the calls return the `200 OK` response code.



<a name="task_ofh_np1_cfc"/>

<!-- task\_ofh\_np1\_cfc -->

## Exposing Services in Different Namespaces



<a name="task_ofh_np1_cfc__context_lsv_pjz_x2c"/>

## Context

Expose two workloads deployed in different namespaces with one APIRule definition.



## Procedure

You can use either Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  Create a namespace with the Istio sidecar proxy injection enabled.

        For more information, see [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

    2.  Go to *Discovery and Network \> API Rules* and select *Create*.

    3.  Switch to the *YAML* section.

    4.  Paste the APIRule custom resource \(CR\) configuration into the editor. You must specify a Service's namespace in each Service definition. See an example:

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

    2.  Expose the Services in their respective namespaces by creating an APIRule custom resource \(CR\) in its own namespace. You must specify a Service's namespace in each Service definition. See an example:

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

    3.  To call the endpoints, send requests to the exposed Services, for example:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/headers
        
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/get
        ```

        If successful, the calls return the `200 OK` response code.



