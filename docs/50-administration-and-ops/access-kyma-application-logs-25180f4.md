<!-- loio25180f491b7c4b3fafa5d3e68786981d -->

# Access Kyma Application Logs

Get insights into your applications, microservices, and Functions by viewing the respective logs. To check out real-time logs immediately, use the Kubernetes functionalities - either in Kyma dashboard, or with kubectl.



## Context

-   If you prefer to see the logs in your terminal, replace the placeholders in the following command and run it:

    ```
    kubectl logs <{POD_NAME}> --namespace <{NAMESPACE_NAME}> --container <{CONTAINER_NAME}>
    
    ```

-   To see real-time logs in Kyma dashboard, follow these steps:




## Procedure

1.  Open Kyma dashboard and select the namespace.

2.  Access the Pod.

3.  Find the container and select *View Logs*.




<a name="loio25180f491b7c4b3fafa5d3e68786981d__result_zyn_mfs_5zb"/>

## Results

You have access to short-term logs of every container in your Kyma runtime.



<a name="loio25180f491b7c4b3fafa5d3e68786981d__postreq_s4b_2yy_5zb"/>

## Next Steps

> ### Recommendation:  
> To enable long-term storage of logs with advanced querying, dashboarding, and alerting capabilities, use SAP Cloud Logging with the Kyma Telemetry module for integration.

**Related Information**  


[Auditing and Logging Information in Kyma](../60-security/auditing-and-logging-information-in-kyma-935e241.md "Kyma runtime collects audit and application logs.")

[Create an SAP Cloud Logging Instance through SAP BTP Service Operator](https://help.sap.com/docs/cloud-logging/cloud-logging/create-sap-cloud-logging-instance-through-sap-btp-service-operator?locale=en-US&version=Cloud)

[Ingest via Kyma Runtime](https://help.sap.com/docs/cloud-logging/cloud-logging/ingest-via-kyma-runtime?version=Cloud)

