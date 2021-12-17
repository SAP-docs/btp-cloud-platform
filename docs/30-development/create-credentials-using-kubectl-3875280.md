<!-- loio38752803e8594b7fb4c59bcbc2634cb8 -->

# Create Credentials Using kubectl

To allow your application to call the service, you need specific credentials.



<a name="loio38752803e8594b7fb4c59bcbc2634cb8__context_f33_vrc_hmb"/>

## Context

To ensure your application can call the service instance, you must create a ServiceBinding resource. This resource is a link between a service instance and an application that you create to request credentials or configuration details for a given service.



<a name="loio38752803e8594b7fb4c59bcbc2634cb8__steps_vzt_nvc_hmb"/>

## Procedure

1.  Create a ServiceBinding resource:

    > ### Note:  
    > To create a proper service instance, replace the placeholders with actual values.

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: servicecatalog.k8s.io/v1beta1
    kind: ServiceBinding
    metadata:
      name: {SERVICE_BINDING_NAME}
      namespace: {YOUR_NAMESPACE}
    spec:
      instanceRef:
        name: {SERVICE_INSTANCE_NAME}
    EOF
    ```

    Applying such a resource allows the system to create credentials in the form of a Kubernetes Secret resource. To inspect your ServiceBinding resource, run:

    ```
    kubectl get servicebindings -n {YOUR_NAMESPACE} {SERVICE_INSTANCE_NAME} -o yaml
    ```

2.  To check if the Secret containing the service credentials is available in your Namespace, run:

    ```
    kubectl get secrets -n {YOUR_NAMESPACE}
    ```

    The result should be similar to the following:

    ```
    NAME                   	   TYPE                                  DATA    AGE
    {SERVICE_BINDING_NAME}         Opaque                                   8    91s
    ```

    > ### Note:  
    > To use the credentials, make sure your application is bound to the service instance. For details, see [Bind Service Instances to Applications Using kubectl](bind-service-instances-to-applications-using-kubectl-cfc1c31.md).


