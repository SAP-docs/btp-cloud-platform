<!-- loiof4afb1a4afa64405995815e3f181d89a -->

# Managing Kyma Runtime Using the Provisioning Service API

The SAP Cloud Management service \(technical name: `cis`\) provides the Provisioning Service API to create and manage available environments. Use the Provisioning Service API to automatically manage and access SAP BTP, Kyma runtime.



<a name="loiof4afb1a4afa64405995815e3f181d89a__prereq_ntr_t3n_ldc"/>

## Prerequisites

-   Your subaccount must have entitlements for SAP BTP, Kyma runtime and the SAP Cloud Management service for SAP BTP. See [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).
-   Command line interface \(CLI\) tools:
    -   [kubectl](https://kubernetes.io/docs/reference/kubectl/)
    -   [jq](https://jqlang.github.io/jq/)
    -   [curl](https://curl.se/)
    -   SAP BTP command line interface \(btp CLI\). See [Download and Start Using the btp CLI Client](download-and-start-using-the-btp-cli-client-8a8f17f.md#loio8a8f17f5fd334fb583438edbd831d506).




## Context

To manage a Kyma instance automatically, create a Kyma service binding. The Kyma service binding enables getting a Kyma kubeconfig, which in turn allows for accessing a Kyma cluster, deploying applications, running tests, and deleting the resources in a fully automated way.



## Procedure

1.  Provision the SAP Cloud Management service instance with the `local` plan and create a binding to get the credentials for the Provisioning Service API. To do that, you can use:

    -   SAP BTP cockpit, as described in [Getting an Access Token for SAP Cloud Management Service APIs](getting-an-access-token-for-sap-cloud-management-service-apis-3670474.md).

    -   btp CLI and follow these steps:


    1.  Set the `CIS_INSTANCE_NAME` environment variable with the name of the SAP Cloud Management service instance.

        ```
        export CIS_INSTANCE_NAME={CIS_INSTANCE_NAME}
        ```

    2.  Provision the SAP Cloud Management service instance with the Client Credentials grant type passed as parameters.

        ```
        btp create services/instance --offering-name cis --plan-name local --name ${CIS_INSTANCE_NAME} --parameters {\"grantType\":\"clientCredentials\"}
        ```

    3.  Create a binding for the instance.

        ```
        btp create services/binding --name ${CIS_INSTANCE_NAME}-binding --instance-name ${CIS_INSTANCE_NAME}
        ```


2.  Set the `CLIENT_ID`, `CLIENT_SECRET`, `UAA_URL`, and `PROVISIONING_SERVICE_URL` environment variables using the credentials from the binding stored in the `clientid`, `clientsecret`, `url`, and `provisioning_service_url` fields. Use the btp CLI to get the credentials.

    ```
    export CLIENT_ID=$(btp --format json get services/binding --name ${CIS_INSTANCE_NAME}-binding | jq -r '.credentials.uaa.clientid')
    export CLIENT_SECRET=$(btp --format json get services/binding --name ${CIS_INSTANCE_NAME}-binding | jq -r '.credentials.uaa.clientsecret')
    export UAA_URL=$(btp --format json get services/binding --name ${CIS_INSTANCE_NAME}-binding | jq -r '.credentials.uaa.url')
    export PROVISIONING_SERVICE_URL=$(btp --format json get services/binding --name ${CIS_INSTANCE_NAME}-binding | jq -r '.credentials.endpoints.provisioning_service_url')
    ```

3.  Get the access token for the Provisioning Service API using the client credentials.

    ```
    TOKEN=$(curl -s -X POST "${UAA_URL}/oauth/token" -H "Content-Type: application/x-www-form-urlencoded" -u "${CLIENT_ID}:${CLIENT_SECRET}" --data-urlencode "grant_type=client_credentials" | jq -r '.access_token')
    ```

4.  Check if Kyma runtime is available for provisioning.

    ```
    curl -s "$PROVISIONING_SERVICE_URL/provisioning/v1/availableEnvironments" -H "accept: application/json" -H "Authorization: bearer $TOKEN" | jq
    ```

5.  Set the `ENVIRONMENT_TYPE` and `SERVICE_NAME` environment variables to const values *kyma* and *kymaruntime*, and provide values for the `NAME`, `REGION`, `PLAN`, and `USER_ID` environment variables.

    ```
    export ENVIRONMENT_TYPE="kyma"
    export SERVICE_NAME="kymaruntime"
    export NAME={RUNTIME_NAME}
    export REGION={CLUSTER_REGION}
    export PLAN={KYMA_RUNTIME_PLAN_NAME}
    export USER_ID={USER_ID}
    ```

6.  Provision the Kyma runtime and save the instance ID in the `INSTANCE_ID` environment variable.

    ```
    INSTANCE_ID=$(curl -s -X POST "$PROVISIONING_SERVICE_URL/provisioning/v1/environments" -H "accept: application/json" -H "Authorization: bearer $TOKEN" -H "Content-Type: application/json" -d "{\"environmentType\":\"$ENVIRONMENT_TYPE\",\"parameters\":{\"name\":\"$NAME\",\"region\":\"$REGION\"},\"planName\":\"$PLAN\",\"serviceName\":\"$SERVICE_NAME\",\"user\":\"$USER_ID\"}" | jq -r '.id')
    ```

7.  **Optional:** Set the `EXPIRATION_SECONDS` environment variable to the number of seconds \(from 600 to 7200\) after which a binding expires.

    ```
    export EXPIRATION_SECONDS={EXPIRATION_SECONDS}
    ```

8.  After the provisioning is completed, create the binding and save the binding ID in the `BINDING_ID` environment variable.

    ```
    [ -z "$EXPIRATION_SECONDS" ] && \
    BINDING_ID=$(curl -sS -D - -X PUT "$PROVISIONING_SERVICE_URL/provisioning/v1/environments/$INSTANCE_ID/bindings" -H "accept: application/json" -H "Authorization: bearer $TOKEN" -H "Content-Type: application/json" -d "{\"parameters\":{\"expiration_seconds\":600}}" -o /dev/null | sed -n 's/^.*location: //p' | sed 's/\r$//g') || \
    BINDING_ID=$(curl -sS -D - -X PUT "$PROVISIONING_SERVICE_URL/provisioning/v1/environments/$INSTANCE_ID/bindings" -H "accept: application/json" -H "Authorization: bearer $TOKEN" -H "Content-Type: application/json" -d "{\"parameters\":{\"expiration_seconds\":$EXPIRATION_SECONDS}}" -o /dev/null | sed -n 's/^.*location: //p' | sed 's/\r$//g')
    ```

    > ### Note:  
    > You can have a maximum of 10 non-expired bindings. If you try to create more, you get the message stating that you've reached the maximum number of non-expired bindings.

9.  Get the binding credentials and save them in a kubeconfig file.

    ```
    curl -s -X GET "$PROVISIONING_SERVICE_URL/provisioning/v1/environments/$INSTANCE_ID/bindings/$BINDING_ID" -H "accept: application/json" -H "Authorization: bearer $TOKEN" | jq -r '.credentials.kubeconfig' > kubeconfig.yaml
    ```

10. To access the cluster through kubectl, set the `KUBECONFIG` environment variable to the path of the kubeconfig file.

    ```
    export KUBECONFIG=kubeconfig.yaml
    ```

11. Verify the connection to the cluster. Run a kubectl command to get Pods:

    ```
    kubectl get pods
    ```

    kubectl should return the list of Pods in the `default` namespace running in the cluster, which means that the cluster is accessible.

12. **Optional:** To view the details of the binding you have created, list all bindings for the instance.

    ```
    curl -s "$PROVISIONING_SERVICE_URL/provisioning/v1/environments/$INSTANCE_ID/bindings" -H "accept: application/json" -H "Authorization: bearer $TOKEN"
    ```

13. **Optional:** For extra security, revoke the credentials by deleting the binding sooner than it is set to expire in the `EXPIRATION_SECONDS` environment variable.

    ```
    curl -s -X DELETE "$PROVISIONING_SERVICE_URL/provisioning/v1/environments/$INSTANCE_ID/bindings/$BINDING_ID" -H "accept: application/json" -H "Authorization: bearer $TOKEN"
    ```

    Try to access the cluster using kubectl. The connection should be refused, which means that the binding was successfully deleted and credentials revoked.

    ```
    kubectl get pods
    ```

    > ### Note:  
    > If you skip this step, the binding is automatically deleted after the maximum allowed expiration time \(7200 seconds\) passes.




<a name="loiof4afb1a4afa64405995815e3f181d89a__postreq_f2p_2ns_ldc"/>

## Next Steps

To deprovision Kyma runtime, run:

```
curl -s -X DELETE "$PROVISIONING_SERVICE_URL/provisioning/v1/environments/$INSTANCE_ID" -H "accept: application/json" -H "Authorization: bearer $TOKEN"
```

> ### Note:  
> You can delete the runtime independently of the bindings. Existing bindings do not block the runtime deprovisioning.

**Related Information**  


[Account Administration Using APIs of the SAP Cloud Management Service](account-administration-using-apis-of-the-sap-cloud-management-service-17b6a17.md "Provides information about using the APIs of the SAP Cloud Management service for SAP BTP (technical name: cis) to manage some of the administrative operations in your accounts.")

