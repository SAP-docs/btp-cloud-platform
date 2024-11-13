<!-- loioc8520b1c5c67409eb2d6e06c519eef18 -->

# Creating and Managing Services Using kubectl

Create and manage Service Instances and Service Bindings using kubectl.



## Context

Use kubectl to create and manage your resources.



<a name="loioc8520b1c5c67409eb2d6e06c519eef18__steps_ayb_vch_ypb"/>

## Procedure

1.  Create a Service Instance:

    ```
    kubectl create -f - <<EOF
    apiVersion: services.cloud.sap.com/v1
    kind: ServiceInstance
    metadata:
      name: {INSTANCE_NAME}
      namespace: {NAMESPACE}
    spec:
      serviceOfferingName: {NAME_FROM_SERVICE_MARKETPLACE}
      servicePlanName: {PLAN_FROM_SERVICE_MARKETPLACE}
      externalName: {INSTANCE_NAME}
    EOF
    ```

2.  To see the output, run:

    ```
    kubectl get serviceinstances.services.cloud.sap.com {INSTANCE_NAME} -o yaml
    ```

    You can see the status ***created*** and the message ***ServiceInstance provisioned successfully***.

3.  Create a Service Binding:

    ```
    kubectl create -f - <<EOF
    apiVersion: services.cloud.sap.com/v1
    kind: ServiceBinding
    metadata:
      name: {BINDING_NAME}
      namespace: {NAMESPACE}
    spec:
      serviceInstanceName: {INSTANCE_NAME}
      externalName: {BINDING_NAME}
      secretName: {BINDING_NAME}
      parameters:
          key1: val1
          key2: val2
    EOF
    ```

4.  To see the output, run:

    ```
    kubectl get servicebindings.services.cloud.sap.com {BINDING_NAME} -o yaml
    ```

    You can see the status ***created*** and the message ***ServiceBinding provisioned successfully***.




<a name="loioc8520b1c5c67409eb2d6e06c519eef18__result_sch_bjy_bzb"/>

## Results

You can now use a given service in your Kyma cluster. To see credentials, run:

```
kubectl get secret {BINDING_NAME} -o yaml
```



<a name="loioc8520b1c5c67409eb2d6e06c519eef18__postreq_jqd_mjy_bzb"/>

## Next Steps

To clean up your resources, run:

```
kubectl delete servicebindings.services.cloud.sap.com {BINDING_NAME}
kubectl delete serviceinstances.services.cloud.sap.com {INSTANCE_NAME}
```

