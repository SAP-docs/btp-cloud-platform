<!-- loiocfc1c3184653405e83870951fec3548f -->

# Bind Service Instances to Applications Using kubectl

As an alternative to the Kyma Console/Dashboard, you can use **kubectl** to bind your service to the application and establish a connection between the two.



<a name="loiocfc1c3184653405e83870951fec3548f__prereq_mdr_w5d_hmb"/>

## Prerequisites

You have created the credentials the binding uses to access the service. For details, see [Create Credentials Using kubectl](create-credentials-using-kubectl-3875280.md).



<a name="loiocfc1c3184653405e83870951fec3548f__context_f33_vrc_hmb"/>

## Context

To enable the connection between the application and the service instance, manually create a ServiceBindingUsage custom resource that is a link between the service instance and the application that you create.



## Procedure

1.  Create a ServiceBindingUsage resource:

    > ### Note:  
    > To create a proper service instance, replace the placeholders with actual values.

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: servicecatalog.kyma-project.io/v1alpha1
    kind: ServiceBindingUsage
    metadata:
     name: {SERVICE_BINDING_USAGE_NAME}
     namespace: {NAMESPACE_NAME}
    spec:
     serviceBindingRef:
       name: {SERVICE_BINDING_NAME}
     usedBy:
       kind: deployment 
       name: {APPLICATION_NAME}
     parameters:
       envPrefix:
         name: "PREFIX_"
    EOF 
    ```




<a name="loiocfc1c3184653405e83870951fec3548f__result_lvv_tfj_5pb"/>

## Results

Applying such a resource allows the system to inject the Secret created along with the ServiceBinding to the application.



<a name="loiocfc1c3184653405e83870951fec3548f__postreq_qcb_vfj_5pb"/>

## Next Steps

To inspect your ServiceBindingUsage resource, run:

```
kubectl get servicebindingusage -n {YOUR_NAMESPACE} {SERVICE_BINDING_USAGE_NAME} -o yaml
```

> ### Note:  
> When you bind a Function to the ServiceInstance from the remote API, the created Secret is not able to reflect API credential changes made on the remote system. As a result, when you update API credentials in the connected remote system, those changes are not propagated to Kyma and the already-existing Function fails to authenticate in the remote system. To recreate API credentials for existing Functions, delete the ServiceInstance, provision it again from Service Catalog, and recreate the Function binding. This action requires verification of the Function code and updating environment variables for API binding.

