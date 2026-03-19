<!-- loio8b4897185c5949a6aae4ec15e0223408 -->

# Expose a Workload with noAuth

Learn how to expose an unsecured workload using the `noAuth` access strategy and call its endpoints.



<a name="loio8b4897185c5949a6aae4ec15e0223408__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have the Istio and API Gateway modules in your cluster. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have a deployed workload.

    > ### Note:  
    > To expose a workload using APIRule in version `v2`, the workload must be part of the Istio service mesh. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

-   To set up a custom Gateway, see [Configure a TLS Gateway](configure-a-tls-gateway-87a874c.md). Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`. See [Istio Gateways](istio-gateways-8297fa1.md).

    > ### Tip:  
    > To learn what the default domain of your Kyma cluster is, run the following command:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}'
    > ```




## Context

The intended functionality of the noAuth access strategy is to provide a simple configuration for exposing workloads. It allows public access to your workload without any authentication or authorization checks. This is useful for:

-   Development and testing environments
-   Public APIs that don't require authentication
-   Services that implement their own authentication logic

> ### Caution:  
> Exposing a workload to the outside world is a potential security vulnerability, so be careful. In a production environment, always secure the workload you expose.

To expose a workload without authentication, create an APIRule with `noAuth: true` configured for each path you want to expose publicly.



## Procedure

You can use either Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  In a namespace of your choice, go to *Discovery and Network → API Rules* and choose *Create*.

    2.  Provide all the required configuration details.

    3.  For each path you want to expose with `noAuth`, add a rule with the following configuration.

        -   `Access Strategy`: *noAuth*
        -   Add allowed methods and the request path.

    4.  Choose *Create*.


    You can access your Service at `https://${WORKLOAD_DOMAIN}`.

    -   Send a `GET` request to the exposed workload:

        ```
        curl -ik -X GET "https://${WORKLOAD_DOMAIN}/ip"
        ```

    -   Send a `POST` request to the exposed workload:

        ```
        curl -ik -X POST "https://${WORKLOAD_DOMAIN}/post" -d "test data"
        ```


    If successful, the calls return `200 OK` response codes.

-   Use kubectl.

    Replace the placeholders and apply the following configuration. Adjust the rules sections as needed.

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: gateway.kyma-project.io/v2
    kind: APIRule
    metadata:
      name: ${APIRULE_NAME}
      namespace: ${NAMESPACE}
    spec:
      hosts:
        - ${SUBDOMAIN}.${PARENT_DOMAIN}
      service:
        name: ${SERVICE_NAME}
        namespace: ${SERVICE_NAMESPACE}
        port: ${SERVICE_PORT}
      gateway: ${GATEWAY_NAMESPACE}/${GATEWAY_NAME}
      rules:
        - path: /post
          methods: ["POST"]
          noAuth: true
        - path: /{**}
          methods: ["GET"]
          noAuth: true
    EOF
    ```

    You can access your Service at `https://${WORKLOAD_DOMAIN}`.

    -   Send a `GET` request to the exposed workload:

        ```
        curl -ik -X GET "https://${WORKLOAD_DOMAIN}/ip"
        ```

    -   Send a `POST` request to the exposed workload:

        ```
        curl -ik -X POST "https://${WORKLOAD_DOMAIN}/post" -d "test data"
        ```


    If successful, the calls return `200 OK` response codes.




## Example

Choose one of the following methods to create an APIRule that exposes a sample HTTPBin Deployment. You can either follow the example using the Kyma dashboard or the one using kubectl.

-   Use Kyma dashboard:

    > ### Example:  
    > Go to *Namespaces* and create a namespace with enabled Istio sidecar proxy injection.
    > 
    > 1.  Select *\+ Upload YAML*, paste the following cofiguration and upload it.
    > 
    >     ```
    >     apiVersion: v1
    >     kind: ServiceAccount
    >     metadata:
    >       name: httpbin
    >     ---
    >     apiVersion: v1
    >     kind: Service
    >     metadata:
    >       name: httpbin
    >       labels:
    >         app: httpbin
    >         service: httpbin
    >     spec:
    >       ports:
    >       - name: http
    >         port: 8000
    >         targetPort: 80
    >       selector:
    >         app: httpbin
    >     ---
    >     apiVersion: apps/v1
    >     kind: Deployment
    >     metadata:
    >       name: httpbin
    >     spec:
    >       replicas: 1
    >       selector:
    >         matchLabels:
    >           app: httpbin
    >           version: v1
    >       template:
    >         metadata:
    >           labels:
    >             app: httpbin
    >             version: v1
    >         spec:
    >           serviceAccountName: httpbin
    >           containers:
    >           - image: docker.io/kennethreitz/httpbin
    >             imagePullPolicy: IfNotPresent
    >             name: httpbin
    >             ports:
    >             - containerPort: 80
    >     ```
    > 
    > 2.  Go to *Discovery and Network → API Rules* and select *Create*.
    > 3.  Provide the name of the APIRule CR.
    > 4.  In the *Service* section, add the name *httpbin* and port *8000*.
    > 5.  Use the default Gateway *kyma-system/kyma-gateway*.
    > 
    >     Alternatively, you can replace these values and use your custom Gateway. See [Configure a TLS Gateway](configure-a-tls-gateway-87a874c.md).
    > 
    > 6.  Add the host `httpbin.${PARENT_DOMAIN}`.
    > 
    >     To learn what your default parent domain is, go to the Kyma Environment section of your subaccount overview, and copy the part of the *APIServerURL* link after `https://api.`. For example, if your *APIServerURL* link is `https://api.c123abc.kyma.ondemand.com`, use *httpbin.c123abc.kyma.ondemand.com* as the host. If you use a custom Gateway, add the host configured in the Gateway.
    > 
    > 7.  Add a rule with the following configuration:
    > 
    > 
    >     <table>
    >     <tr>
    >     <th valign="top">
    > 
    >     Option
    >     
    >     </th>
    >     <th valign="top">
    > 
    >     Description
    >     
    >     </th>
    >     </tr>
    >     <tr>
    >     <td valign="top">
    >     
    >     `Path`
    >     
    >     </td>
    >     <td valign="top">
    >     
    >     */post*
    >     
    >     </td>
    >     </tr>
    >     <tr>
    >     <td valign="top">
    >     
    >     `Handler`
    >     
    >     </td>
    >     <td valign="top">
    >     
    >     *noAuth*
    >     
    >     </td>
    >     </tr>
    >     <tr>
    >     <td valign="top">
    >     
    >     `Methods`
    >     
    >     </td>
    >     <td valign="top">
    >     
    >     *POST*
    >     
    >     </td>
    >     </tr>
    >     </table>
    >     
    > 8.  Add one more rule with the following configuration:
    > 
    > 
    >     <table>
    >     <tr>
    >     <th valign="top">
    > 
    >     Option
    >     
    >     </th>
    >     <th valign="top">
    > 
    >     Description
    >     
    >     </th>
    >     </tr>
    >     <tr>
    >     <td valign="top">
    >     
    >     `Path`
    >     
    >     </td>
    >     <td valign="top">
    >     
    >     */\{\*\*\}*
    >     
    >     </td>
    >     </tr>
    >     <tr>
    >     <td valign="top">
    >     
    >     `Handler`
    >     
    >     </td>
    >     <td valign="top">
    >     
    >     *noAuth*
    >     
    >     </td>
    >     </tr>
    >     <tr>
    >     <td valign="top">
    >     
    >     `Methods`
    >     
    >     </td>
    >     <td valign="top">
    >     
    >     *GET*
    >     
    >     </td>
    >     </tr>
    >     </table>
    >     
    > 9.  Choose *Create*.
    > 10. Access the Service at `https://${WORKLOAD_DOMAIN}`.

-   Use kubectl:

    > ### Example:  
    > Use kubectl:
    > 
    > 1.  Create a namespace with enabled Istio sidecar proxy injection.
    > 
    >     ```
    >     NAMESPACE="test"
    >     kubectl create ns "${NAMESPACE}"
    >     kubectl label namespace "${NAMESPACE}" istio-injection=enabled --overwrite
    >     ```
    > 
    > 2.  Get the default domain of your Kyma cluster.
    > 
    >     ```
    >     PARENT_DOMAIN=$(kubectl get configmap -n kube-system shoot-info -o jsonpath="{.data.domain}")
    >     WORKLOAD_DOMAIN="httpbin.${PARENT_DOMAIN}"
    >     GATEWAY="kyma-system/kyma-gateway"
    >     echo "Parent domain: ${PARENT_DOMAIN}"
    >     echo "Workload domain: ${WORKLOAD_DOMAIN}"
    >     echo "Gateway namespace and name: ${GATEWAY}"
    >     ```
    > 
    >     This procedure uses the default domain of your Kyma cluster and the default Gateway. Alternatively, you can replace these values and use your custom domain and Gateway instead. See [Istio Gateways](istio-gateways-8297fa1.md) and [Configure a TLS Gateway](configure-a-tls-gateway-87a874c.md).
    > 
    > 3.  Deploy a sample instance of the HTTPBin Service.
    > 
    >     ```
    >     cat <<EOF | kubectl -n "${NAMESPACE}" apply -f -
    >     apiVersion: v1
    >     kind: ServiceAccount
    >     metadata:
    >       name: httpbin
    >     ---
    >     apiVersion: v1
    >     kind: Service
    >     metadata:
    >       name: httpbin
    >       labels:
    >         app: httpbin
    >         service: httpbin
    >     spec:
    >       ports:
    >       - name: http
    >         port: 8000
    >         targetPort: 80
    >       selector:
    >         app: httpbin
    >     ---
    >     apiVersion: apps/v1
    >     kind: Deployment
    >     metadata:
    >       name: httpbin
    >     spec:
    >       replicas: 1
    >       selector:
    >         matchLabels:
    >           app: httpbin
    >           version: v1
    >       template:
    >         metadata:
    >           labels:
    >             app: httpbin
    >             version: v1
    >         spec:
    >           serviceAccountName: httpbin
    >           containers:
    >           - image: docker.io/kennethreitz/httpbin
    >             imagePullPolicy: IfNotPresent
    >             name: httpbin
    >             ports:
    >             - containerPort: 80
    >     EOF
    >     ```
    > 
    >     To verify if an instance of the HTTPBin Service is successfully created, run:
    > 
    >     ```
    >     kubectl get pods -l app=httpbin -n "${NAMESPACE}"
    >     ```
    > 
    >     If successful, you get a result similar to this one:
    > 
    >     ```
    >     NAME                 READY    STATUS     RESTARTS    AGE
    >     httpbin-{SUFFIX}     2/2      Running    0           96s
    >     ```
    > 
    > 4.  Expose the workload with an APIRule using the `noAuth` access strategy.
    > 
    >     ```
    >     cat <<EOF | kubectl apply -n "${NAMESPACE}" -f -
    >     apiVersion: gateway.kyma-project.io/v2
    >     kind: APIRule
    >     metadata:
    >       name: apirule-noauth
    >     spec:
    >       hosts:
    >         - ${WORKLOAD_DOMAIN}
    >       service:
    >         name: httpbin
    >         namespace: ${NAMESPACE}
    >         port: 8000
    >       gateway: ${GATEWAY}
    >       rules:
    >         - path: /post
    >           methods: ["POST"]
    >           noAuth: true
    >         - path: /{**}
    >           methods: ["GET"]
    >           noAuth: true
    >     EOF
    >     ```
    > 
    > 5.  Check if the APIRule's status is ready:
    > 
    >     ```
    >     kubectl get apirules apirule-noauth -n "${NAMESPACE}" 
    >     ```
    > 
    > 6.  Send `GET` and `POST` request to the exposed workload:
    > 
    >     ```
    >     curl -ik -X GET "https://${WORKLOAD_DOMAIN}/ip"
    >     curl -ik -X POST "https://${WORKLOAD_DOMAIN}/post" -d "test data"
    >     ```
    > 
    >     If successful, the calls return `200 OK` response codes.


