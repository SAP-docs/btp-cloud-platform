<!-- loio5deca69978eb471692743089ce1eed77 -->

# Deleting Service Bindings and Service Instances

Delete service bindings and service instances using Kyma dashboard or kubectl.



<a name="loio5deca69978eb471692743089ce1eed77__prereq_nhw_xm3_mfc"/>

## Prerequisites

-   You have the SAP BTP Operator module in your cluster. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   For CLI interactions: [kubectl](https://kubernetes.io/docs/tasks/tools/) configured to communicate with your Kyma instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).




## Context

You can only delete service instances or service bindings created in Kyma using Kyma dashboard or kubectl. You can't perform these operations using the SAP BTP cockpit. To delete a service instance, first delete its service bindings.

> ### Caution:  
> Once you delete your service instances and service bindings, you cannot revert the operation.



<a name="loio5deca69978eb471692743089ce1eed77__steps-unordered_bkr_vp2_xcc"/>

## Procedure

Use either Kyma dashboard or kubectl to delete a service binding or a service instance.

Kyma dashboard is a web-based UI providing a graphical overview of your cluster and all its resources. To access Kyma dashboard, use the link available in the **Kyma Environment** section of your subaccount *Overview*.

-   **Use Kyma dashboard**

    1.  In the navigation area, choose *Namespaces*, and go to the namespace you want to delete a service binding/instance from.

    2.  Go to *Service Management*, and then to *Service Bindings* or *Service Instances*.

    3.  Choose the service binding/instance and delete it.


-   **Use kubectl**

    -   To delete a service binding, run:

        ```
        kubectl delete servicebindings.services.cloud.sap.com {BINDING_NAME}
        ```

    -   To delete a service instance, run:

        ```
        kubectl delete serviceinstances.services.cloud.sap.com {SERVICE_INSTANCE_NAME}
        ```



