<!-- loioea4dd81e49254dd482d32e3c20f4477a -->

# Using SAP BTP Services in the Kyma Environment

With the Kyma environment, you can connect SAP BTP services to your cluster and manage them using SAP BTP Service Operator.



<a name="loioea4dd81e49254dd482d32e3c20f4477a__prereq_vbj_qf2_qtb"/>

## Prerequisites

-   For CLI interactions: You have installed [kubectl](https://kubernetes.io/docs/tasks/tools/) v1.17 or higher.

-   You know the `serviceOfferingName` and `servicePlanName` for the SAP BTP service you want to connect to the Kyma cluster. You find these values in the Service Marketplace of the SAP BTP cockpit. Click on the service's tile and find *name* and *Plan*, respectively.


> ### Note:  
> You can use [SAP BTP kubectl plugin](https://github.com/SAP/sap-btp-service-operator#sap-btp-kubectl-plugin-experimental) to get the available services in your SAP BTP account by using the access credentials stored in the cluster. However, the plugin is still experimental.



<a name="loioea4dd81e49254dd482d32e3c20f4477a__steps_ayb_vch_ypb"/>

## Procedure

1.  > ### Note:  
    > You can choose to create and manage resources such as Service Instances and Service Bindings in Kyma Dashboard, in the *Namespace* view, under *Service Management*. Still, you need the service details, such as service name and plan, from the SAP BTP cockpit.

2.  Create a Service Instance:

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

3.  To see the output, run:

    ```
    kubectl get serviceinstances.services.cloud.sap.com {INSTANCE_NAME} -o yaml
    ```

    You can see the status ***created*** and the message ***ServiceInstance provisioned successfully***.

4.  Create a Service Binding:

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

5.  To see the output, run:

    ```
    kubectl get servicebindings.services.cloud.sap.com {BINDING_NAME} -o yaml
    ```

    You can see the status ***created*** and the message ***ServiceBinding provisioned successfully***.

6.  You can now use a given service in your Kyma cluster. To see credentials, run:

    ```
    kubectl get secret {BINDING_NAME} -o yaml
    ```

7.  Clean up your resources:

    ```
    kubectl delete servicebindings.services.cloud.sap.com {BINDING_NAME}
    kubectl delete serviceinstances.services.cloud.sap.com {INSTANCE_NAME}
    
    ```


**Related Information**  


[SAP BTPService Operator](https://github.com/SAP/sap-btp-service-operator)

