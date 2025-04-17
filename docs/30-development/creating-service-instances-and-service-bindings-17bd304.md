<!-- loio17bd304aeab34294a4ca34fa9564147c -->

# Creating Service Instances and Service Bindings

To use an SAP BTP service in your Kyma cluster, create its service instance and service binding using Kyma dashboard or kubectl.



<a name="loio17bd304aeab34294a4ca34fa9564147c__prereq_wyw_t4w_ycc"/>

## Prerequisites

-   The [SAP BTP Operator module](sap-btp-operator-module-50347ea.md) is added.

    For instructions on adding modules, see [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   For CLI interactions: [kubectl](https://kubernetes.io/docs/tasks/tools/) v1.17 or higher.

-   For an enterprise account, you have added quotas to the services you purchased in your subaccount. Otherwise, only default free-of-charge services are listed in the service marketplace. Quotas are automatically assigned to the resources available in trial accounts.

    For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-entitlements-and-quotas-for-subaccounts?&version=Cloud).

-   You know the service offering name and service plan name for the SAP BTP service you want to connect to your Kyma cluster.

    > ### Tip:  
    > To find the service and service plan names, in the SAP BTP cockpit, go to *Services* \> *Service Marketplace*. Click on the service tile and find its *name* and *Plan*.


<a name="loio3ca9284699c44180b12e7be513bdac06"/>

<!-- loio3ca9284699c44180b12e7be513bdac06 -->

## Creating a Service Instance

To create a service instance, use either Kyma dashboard or kubectl.

<a name="task_unp_3d5_s2c"/>

<!-- task\_unp\_3d5\_s2c -->

### Use Kyma Dashboard

Kyma dashboard is a web-based UI providing a graphical overview of your cluster and all its resources. To access Kyma dashboard, use the link available in the **Kyma Environment** section of your subaccount *Overview*.



## Procedure

1.  In the navigation area, choose *Namespaces*, and go to the namespace you want to work in.

2.  Go to *Service Management* \> *Service Instances*, and choose *Create*.

3.  Provide the required service details in *Form*. Alternatively, you can switch to the *YAML* tab, and edit or upload your file.

4.  Choose *Create*.

    You see the status ***PROVISIONED***.


<a name="task_rxw_225_s2c"/>

<!-- task\_rxw\_225\_s2c -->

### Use kubectl



## Procedure

1.  To create a `ServiceInstance` custom resource \(CR\), replace the placeholders and run the following command:

    ```
        kubectl create -f - <<EOF 
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
    
    NAME                      OFFERING                    PLAN                     STATUS    AGE
    {SERVICE_INSTANCE_NAME}   {SERVICE_OFFERING_NAME}     {SERVICE_PLAN_NAME}      Created   44s
    ```


<a name="loioab5ca11be3bf4c029982332fe7092f74"/>

<!-- loioab5ca11be3bf4c029982332fe7092f74 -->

## Creating a Service Binding

To create a service binding, use either Kyma dashboard or kubectl.

With a `ServiceBinding` custom resource \(CR\), your application can get access credentials for communicating with an SAP BTP service. These access credentials are available to applications through a Secret resource generated in your cluster.

<a name="task_jpv_x25_s2c"/>

<!-- task\_jpv\_x25\_s2c -->

### Use Kyma Dashboard

Kyma dashboard is a web-based UI providing a graphical overview of your cluster and all its resources. To access Kyma dashboard, use the link available in the **Kyma Environment** section of your subaccount *Overview*.



## Procedure

1.  In the navigation area, choose *Namespaces*, and go to the namespace you want to work in.

2.  Go to *Service Management* \> *Service Bindings*, and choose *Create*.

3.  Provide the required details, and choose your service instance name from the dropdown list. Alternatively, you can provide the required details by switching from the *Form* to *YAML* tab, and editing or uploading your file.

4.  Choose *Create*.

    You see the status ***PROVISIONED***.


<a name="task_tjn_z25_s2c"/>

<!-- task\_tjn\_z25\_s2c -->

### Use kubectl



## Procedure

1.  To create a `ServiceBinding` CR, replace the placeholders and run the following command:

    ```
    kubectl create -f - <<EOF
    apiVersion: services.cloud.sap.com/v1
    kind: ServiceBinding
    metadata:
      name: {BINDING_NAME}
    spec:
      serviceInstanceName: {SERVICE_INSTANCE_NAME}
      externalName: {EXTERNAL_NAME}
      secretName: {SECRET_NAME}
      parameters:
        key1: val1
        key2: val2   
    EOF        
    ```

    > ### Remember:  
    > In the `serviceInstanceName` field of the service binding, enter the name of the `ServiceInstance` resource you previously created.

2.  To check your service binding status, run:

    ```
    kubectl get servicebindings {BINDING_NAME} -n {NAMESPACE}
    
    ```

    You see the status ***Created***.

3.  Verify the Secret is created with the name specified in the `spec.secretName` field of the `ServiceBinding` CR. The Secret contains access credentials that the applications need to use the service. Run:

    ```
    kubectl get secrets {SECRET_NAME} -n {NAMESPACE}
    
    ```

    You see the same Secret name as in the `spec.secretName` field of the `ServiceBinding` CR.


