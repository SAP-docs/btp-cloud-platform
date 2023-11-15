<!-- loioea4dd81e49254dd482d32e3c20f4477a -->

# Using SAP BTP Services in the Kyma Environment

With the Kyma environment, you can connect SAP BTP services to your cluster and manage them using SAP BTP Service Operator.



<a name="loioea4dd81e49254dd482d32e3c20f4477a__prereq_vbj_qf2_qtb"/>

## Prerequisites

-   The SAP BTP Operator module is enabled, see [Enable and Disable a Kyma Module](../50-administration-and-ops/enable-and-disable-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c). Otherwise, you get the following error message: `resource mapping not found for {...} ensure CRDs are installed first`.

-   For CLI interactions: [kubectl](https://kubernetes.io/docs/tasks/tools/) v1.17 or higher.

-   You know the `serviceOfferingName` and `servicePlanName` for the SAP BTP service you want to connect to the Kyma cluster. You find these values in the Service Marketplace of the SAP BTP cockpit. Click on the service's tile and find *name* and *Plan*, respectively.


> ### Note:  
> You can use [SAP BTP kubectl plugin](https://github.com/SAP/sap-btp-service-operator#sap-btp-kubectl-plugin-experimental) to get the available services in your SAP BTP account by using the access credentials stored in the cluster. However, the plugin is still experimental.

<a name="loio975983821be040f0b7886791abcf3b7e"/>

<!-- loio975983821be040f0b7886791abcf3b7e -->

## Creating and Managing Services Using Kyma dashboard

Create and manage Service Instances and Service Bindings using Kyma dashboard.



## Context

Use Kyma dashboard to create and manage your resources.



## Procedure

1.  In the *Namespace* view, go to *Service Management**→Service Instances*.

2.  Create Service Instance using the required service details.

    You see the status `PROVISIONED`.

3.  Go to *Service Management**→Service Bindings* and create Service Binding, choosing your instance name from the dropdown list.

    You see the status `PROVISIONED`.




<a name="loio975983821be040f0b7886791abcf3b7e__result_m43_t3y_bzb"/>

## Results

You can now use a given service in your Kyma cluster.

<a name="loioc8520b1c5c67409eb2d6e06c519eef18"/>

<!-- loioc8520b1c5c67409eb2d6e06c519eef18 -->

## Creating and Managing Services Using kubectl

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

