<!-- loio8b4897185c5949a6aae4ec15e0223408 -->

# Exposing Workloads with noAuth

Expose your workload using the `noAuth` access strategy, which allows access to the workload through the specified HTTP methods without requiring authentication.



<a name="loio8b4897185c5949a6aae4ec15e0223408__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and configure it to communicate with your Kyma runtime instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).
-   You have installed [curl](https://curl.se/).
-   You have a deployed workload.
-   You have [set up your custom domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload). Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`.

    > ### Note:  
    > Because the default Kyma domain is a wildcard domain, which uses a simple TLS Gateway, it is recommended that you set up your custom domain for use in a production environment.

    > ### Tip:  
    > To learn what the default domain of your Kyma cluster is, run the following command:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}'
    > ```




## Context

The intended functionality of the noAuth access strategy is to provide a simple configuration for exposing workloads. It only allows access to the specified HTTP methods of the exposed workload.

> ### Caution:  
> Exposing a workload to the outside world is a potential security vulnerability, so be careful. In a production environment, always secure the workload you expose.



## Procedure

You can use either Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  Go to the namespace in which you want to create an APIRule CR.

    2.  Go to *Discovery and Network \> API Rules* and select *Create*.

    3.  Provide the name of the APIRule CR.

    4.  Add the name and port of the service you want to expose.

    5.  Add a Gateway.

    6.  Add a rule with the following configuration:


        <table>
        <tr>
        <th valign="top">

        Option
        
        </th>
        <th valign="top">

        Description
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        `Path`
        
        </td>
        <td valign="top">
        
        */.\**
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Handler`
        
        </td>
        <td valign="top">
        
        *No Auth*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Methods`
        
        </td>
        <td valign="top">
        
        *GET*
        
        </td>
        </tr>
        </table>
        
    7.  Add one more rule with the following configuration:


        <table>
        <tr>
        <th valign="top">

        Option
        
        </th>
        <th valign="top">

        Description
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        `Path`
        
        </td>
        <td valign="top">
        
        */post*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Handler`
        
        </td>
        <td valign="top">
        
        *No Auth*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Methods`
        
        </td>
        <td valign="top">
        
        *POST*
        
        </td>
        </tr>
        </table>
        
    8.  Send a `GET` request to the exposed workload:

        ```
        curl -ik -X GET https://{SUBDOMAIN}.{DOMAIN_NAME}/ip
        ```

        If successful, the call returns the `200 OK` response code.

    9.  Send a `POST` request to the exposed workload:

        ```
        curl -ik -X POST https://{SUBDOMAIN}.{DOMAIN_NAME}/post -d "test data"
        ```

        If successful, the call returns the `200 OK` response code.


-   Use kubectl.

    1.  To create an APIRule CR with `noAuth` configuration, replace the placeholders and run the following command. You can adjust the configuration, if needed.

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



