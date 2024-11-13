<!-- loio5deca69978eb471692743089ce1eed77 -->

# Deleting Service Bindings and Service Instances

Delete service bindings and service instances using Kyma dashboard or kubectl.



## Context

You can only delete service instances or service bindings created in Kyma using Kyma dashboard or kubectl. You can't perform these operations using the SAP BTP cockpit.

> ### Caution:  
> Once you delete your service instances and service bindings, you cannot revert the operation.

If you haven't deleted all the service instances and service bindings associated with the `sap-btp-service-operator` Secret in the `kyma-system` namespace, you can't delete your Kyma cluster from the SAP BTP cockpit. To delete the remaining service instances and service bindings, go to Kyma dashboard.

If you have not deleted service instances and bindings connected to your expired free tier service, you can still find the service binding credentials in the SAP Service Manager instance details in the SAP BTP cockpit. Use them to delete the leftover service instances and bindings.

> ### Tip:  
> To successfully delete a service instance, first delete its service bindings.

Use either Kyma dashboard or kubectl to delete a service binding or a service instance.



<a name="loio5deca69978eb471692743089ce1eed77__steps-unordered_bkr_vp2_xcc"/>

## Procedure

-   Use Kyma dashboard

    1.  In the *Namespaces* view, go to the namespace you want to delete a service binding/instance from.

    2.  Go to *Service Management* and then to *Service Bindings* or *Service Instances*.

    3.  Delete the service binding/instance.


-   Use kubectl

    -   To delete a service binding, run:

        ```
        kubectl delete servicebindings.services.cloud.sap.com {BINDING_NAME}
        ```

    -   To delete a service instance, run:

        ```
        kubectl delete serviceinstances.services.cloud.sap.com {SERVICE_INSTANCE_NAME}
        ```



