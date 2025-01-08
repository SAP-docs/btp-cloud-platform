<!-- loio17bd304aeab34294a4ca34fa9564147c -->

# Creating Service Instances and Service Bindings

To use an SAP BTP service in your Kyma cluster, create its service instance and service binding using Kyma dashboard or kubectl.



<a name="loio17bd304aeab34294a4ca34fa9564147c__prereq_wyw_t4w_ycc"/>

## Prerequisites

-   The [SAP BTP Operator module](sap-btp-operator-module-50347ea.md) is added.

    For instructions on adding modules, see [Add and Delete a Kyma Module](../50-administration-and-ops/add-and-delete-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   For CLI interactions: [kubectl](https://kubernetes.io/docs/tasks/tools/) v1.17 or higher.

-   You know the service offering name and service plan name for the SAP BTP service you want to connect to your Kyma cluster.

    To find the service and service plan names, in the SAP BTP cockpit, go to *Services* \> *Service Marketplace*. Click on the service tile and find its *name* and *Plan*.


<a name="task_tps_kqw_ycc"/>

<!-- task\_tps\_kqw\_ycc -->

## Creating a Service Instance



<a name="task_tps_kqw_ycc__context_xl3_m25_cdc"/>

## Context

To create a service instance, use either Kyma dashboard or kubectl.



<a name="task_tps_kqw_ycc__steps-unordered_hv2_nqw_ycc"/>

## Procedure

-   Use Kyma dashboard.

    1.  In the *Namespaces* view, go to the namespace you want to work in.

    2.  Go to *Service Management* \> *Service Instances*.

    3.  Provide the required service details and create a service instance.

        You see the status ***PROVISIONED***.


-   Use kubectl.

    1.  To create a `ServiceInstance` custom resource \(CR\), follow this example:

        ```
            kubectl create -f - <<EOF 
            apiVersion: services.cloud.sap.com/v1
            kind: ServiceInstance
            metadata:
                name: {SERVICE_INSTANCE_NAME}
                namespace: {NAMESPACE} 
            spec:
                serviceOfferingName: {SERVICE_OFFERING_NAME}
                servicePlanName: {SERVICE_PLAN_NAME}
                externalName: {SERVICE_INSTANCE_NAME}
                parameters:
                  key1: val1
                  key2: val2
            EOF
        ```

    2.  To check the service's status in your cluster, run:

        ```
        kubectl get serviceinstances.services.cloud.sap.com {SERVICE_INSTANCE_NAME} -n {NAMESPACE}
        ```

        You get an output similar to this one:

        ```
        
        NAME                      OFFERING                    PLAN                     STATUS    AGE
        {SERVICE_INSTANCE_NAME}   {SERVICE_OFFERING_NAME}     {SERVICE_PLAN_NAME}      Created   44s
        ```



<a name="task_jjq_5rw_ycc"/>

<!-- task\_jjq\_5rw\_ycc -->

## Creating a Service Binding



<a name="task_jjq_5rw_ycc__context_nw2_xrw_ycc"/>

## Context

With a `ServiceBinding` custom resource \(CR\), your application can get access credentials for communicating with an SAP BTP service. These access credentials are available to applications through a Secret resource generated in your cluster.

To create a service binding, use either Kyma dashboard or kubectl.



<a name="task_jjq_5rw_ycc__steps-unordered_zh5_zrw_ycc"/>

## Procedure

-   Use Kyma dashboard.

    1.  In the *Namespaces* view, go to the namespace you want to work in.

    2.  Go to *Service Management* \> *Service Bindings*.

    3.  Choose your service instance name from the dropdown list and create a service binding.

        You see the status ***PROVISIONED***.


-   Use kubectl.

    1.  To create a `ServiceBinding` CR, follow this example:

        ```
        kubectl create -f - <<EOF
        apiVersion: services.cloud.sap.com/v1
        kind: ServiceBinding
        metadata:
          name: {BINDING_NAME}
        spec:
          serviceInstanceName: {SERVICE_INSTANCE_NAME}
          externalName: {EXTERNAL_NAME}
          secretName: {SECRET_NAME}
          parameters:
            key1: val1
            key2: val2   
        EOF        
        ```

        > ### Remember:  
        > In the `serviceInstanceName` field of the service binding, enter the name of the `ServiceInstance` resource you previously created.

    2.  To check your service binding status, run:

        ```
        kubectl get servicebindings {BINDING_NAME} -n {NAMESPACE}
        
        ```

        You see the status ***Created***.

    3.  Verify the Secret is created with the name specified in the `spec.secretName` field of the `ServiceBinding` CR. The Secret contains access credentials that the applications need to use the service:

        ```
        kubectl get secrets {SECRET_NAME} -n {NAMESPACE}
        
        ```

        You see the same Secret name as in the `spec.secretName` field of the `ServiceBinding` CR.





<a name="task_jjq_5rw_ycc__result_lqh_wtw_ycc"/>

## Results

You can use a given service in your Kyma cluster.

