<!-- loiob53be623b96547cdb5545577b1804ba9 -->

# Create Service Instances Using kubectl

You can use the Kubernetes command-line tool, **kubectl**, to create your service instances.



<a name="loiob53be623b96547cdb5545577b1804ba9__prereq_myq_bfj_fmb"/>

## Prerequisites

Before you proceed, make sure you addressed the prerequisites listed in the table:


<table>
<tr>
<th>

Action



</th>
<th>

Mandatory



</th>
<th>

Link / Remarks



</th>
</tr>
<tr>
<td>

Install and set up **kubectl**.



</td>
<td>

Yes



</td>
<td>

[Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)



</td>
</tr>
<tr>
<td>

Download the **kubeconfig** file to access the cluster using the command line.



</td>
<td>

Yes



</td>
<td>

To download the kubeconfig file from the Kyma Console, click on the user icon in the top right corner of the page and choose *Get Kubeconfig*. For more information, read [this](https://kyma-project.io/docs/components/security/#tutorials-get-the-kubeconfig-file) document.



</td>
</tr>
<tr>
<td>

Enable the Kyma environment.



</td>
<td>

Yes



</td>
<td>

[Enable Kyma Environment](../50-administration-and-ops/Enable_Kyma_Environment_09dd313.md)



</td>
</tr>
<tr>
<td>

Register cloud providers if you want to use the services they provide.



</td>
<td>

No



</td>
<td>

[Register Cloud Providers](Register_Cloud_Providers_740132a.md)



</td>
</tr>
</table>



## Context

Open the terminal and follow the steps to create a service instance:



## Procedure

1.  If you do not have a Namespace already, create one:

    ```
    kubectl create namespace {YOUR_NAMESPACE}
    ```

2.  Create a service instance:

    > ### Note:  
    > To create a proper service instance, replace the placeholders with actual values.

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: servicecatalog.k8s.io/v1beta1
    kind: ServiceInstance
    metadata:
      name: {INSTANCE_NAME}
      namespace: {YOUR_NAMESPACE}
    spec:
      ServiceClassExternalName: {SERVICE_NAME}
      ServicePlanExternalName: {PLAN_NAME}
      parameters:
        param-1: value-1
        param-2: value-2
    EOF
    ```

    > ### Tip:  
    > To list the services available in your Namespace, run:
    > 
    > ```
    > kubectl get serviceclasses -n {YOUR_NAMESPACE}
    > ```
    > 
    > To view the details of the external service, run:
    > 
    > ```
    > kubectl get serviceclasses -n {YOUR_NAMESPACE} {SERVICE_NAME} -o yaml
    > ```
    > 
    > To list service plans available in your Namespace, run:
    > 
    > ```
    > kubectl get serviceplans -n {YOUR_NAMESPACE}
    > ```
    > 
    > To view the details of a particular service plan, run:
    > 
    > ```
    > kubectl get serviceplans -n {YOUR_NAMESPACE} {SERVICE_NAME} -o yaml
    > ```




<a name="loiob53be623b96547cdb5545577b1804ba9__postreq_mkt_p2f_gmb"/>

## Next Steps

Once your service instance is up and running, you can bind it to the application. See [Bind Service Instances to Applications Using kubectl](Bind_Service_Instances_to_Applications_Using_kubectl_cfc1c31.md) for details.

