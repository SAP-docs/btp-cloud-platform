<!-- loio5deca69978eb471692743089ce1eed77 -->

# Deleting Service Bindings and Service Instances

Delete service bindings and service instances using Kyma dashboard or kubectl.



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



