<!-- loiodbf7960f2b9d44c0a5b29b398d9f6dd5 -->

# Updating Service Instances

Use Kyma dashboard or kubectl to update service instances.



<a name="loiodbf7960f2b9d44c0a5b29b398d9f6dd5__prereq_etr_35r_kfc"/>

## Prerequisites

-   You have the SAP BTP Operator module added.

    For instructions on adding modules, see [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   For CLI interactions: [kubectl](https://kubernetes.io/docs/tasks/tools/) configured to communicate with your Kyma instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).




## Context

You are using a service instance in the Kyma environment and want to update the service's plan or other service-specific parameters.

> ### Note:  
> You can only update service instances in Kyma using Kyma dashboard or kubectl. You can't perform the operation using the SAP BTP cockpit.



## Procedure

To update a service instance, use either Kyma dashboard or kubectl.

Kyma dashboard is a web-based UI providing a graphical overview of your cluster and all its resources. To access Kyma dashboard, use the link in the **Kyma Environment** section of your subaccount *Overview*.

-   Use Kyma dashboard.

    1.  In the navigation area, choose *Namespaces*, and go to the namespace with the service instance you want to update.

    2.  Go to *Service Management* \> *Service Instances*, and choose the service instance from the list.

    3.  Choose *Edit*.

    4.  Update the required service details in *Form* and save your changes. Alternatively, you can switch to the *YAML* tab to edit or upload your file, and save your changes.

        You see the message confirming the service instance update.


-   Use kubectl.

    1.  To update a ServiceInstance custom resource \(CR\), replace the placeholders with the following:

        -   The name of the service instance you want to update
        -   The namespace in which the service instance resides
        -   The name of the service offering you are using
        -   The name of the service plan associated with the service offering
        -   Updated or new parameters in the `parameters` section

        Then, run:

        ```
        kubectl apply -f - <<EOF 
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
        NAME                      OFFERING                  PLAN                  STATUS    AGE
        {SERVICE_INSTANCE_NAME}   {SERVICE_OFFERING_NAME}   {SERVICE_PLAN_NAME}   UPDATED   30m27s
        ```



