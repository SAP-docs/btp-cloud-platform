<!-- loiod9e9c7f2c6aa4bc4a2ca0e4b0d089dc4 -->

# Instance-Level Mapping

You can map a Kubernetes service instance to an SAP Service Manager instance in a given subaccount. The Service Manager instance is then used to provision that service instance.



<a name="loiod9e9c7f2c6aa4bc4a2ca0e4b0d089dc4__prereq_ot4_bwx_bdc"/>

## Prerequisites

-   A subaccount in the SAP BTP cockpit.
-   kubectl configured for communicating with your Kyma instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).



<a name="loiod9e9c7f2c6aa4bc4a2ca0e4b0d089dc4__context_dds_yhs_bdc"/>

## Context

To have multiple service instances from different subaccounts associated with one namespace, you must store access credentials for each subaccount in a custom Secret in the `kyma-system` namespace. To create a service instance with the custom Secret, you must use the `btpAccessCredentialsSecret` field in the `spec` of the service instance. In it, you pass the Secret from the `kyma-system` namespace to create your service instance. You can use different Secrets for different service instances.

<a name="task_an3_twx_bdc"/>

<!-- task\_an3\_twx\_bdc -->

## Creating Your Custom Secret



<a name="task_an3_twx_bdc__steps_fyz_wwx_bdc"/>

## Procedure

1.  In the SAP BTP cockpit, create an SAP Service Manager service instance with the `service-operator-access` plan. See [Creating Instances in Other Environments](https://help.sap.com/docs/service-manager/sap-service-manager/creating-instances-in-other-environments?locale=en-US&version=Cloud).

2.  Create a service binding to the SAP Service Manager service instance you have created. See [Creating Service Bindings in Other Environments](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-bindings-in-other-environments?locale=en-US&version=Cloud).

3.  Get the access credentials of the SAP Service Manager instance from its service binding. Copy them from the SAP BTP cockpit as a JSON file.

4.  Create the `creds.json` file in your working directory and save the credentials there.

5.  In the same working directory, generate the Secret by calling the `create-secret-file.sh` script with the `operator` option as the first parameter and `your-secret-name` as the second parameter:

    ```
    curl https://raw.githubusercontent.com/kyma-project/btp-manager/main/hack/create-secret-file.sh | bash -s operator {YOUR_SECRET_NAME}
    ```

    The expected result is the file `btp-access-credentials-secret.yaml` created in your working directory:

    ```
    apiVersion: v1
    kind: Secret
    type: Opaque
    metadata:
      name: {YOUR_SECRET_NAME}
      namespace: kyma-system
    data:
      clientid: {CLIENT_ID}
      clientsecret: {CLIENT_SECRET}
      sm_url: {SM_URL}
      tokenurl: {AUTH_URL}
      tokenurlsuffix: "/oauth/token"
    ```

6.  To create the Secret, run:

    ```
    kubectl create -f ./btp-access-credentials-secret.yaml
    ```

7.  To verify if the Secret has been successfully created, run:

    ```
    kubectl get secret -n kyma-system {YOUR_SECRET_NAME}
    ```

    You see the status ***Created***.

    > ### Note:  
    > You can also view the Secret in Kyma dashboard. In the `kyma-system` namespace, go to *Configuration* \> *Secrets*, and check the list of Secrets.


<a name="task_etb_jfy_ddc"/>

<!-- task\_etb\_jfy\_ddc -->

## Creating a Service Instance with the Custom Secret



<a name="task_etb_jfy_ddc__context_mv5_kfy_ddc"/>

## Context

To create the service instance, use either Kyma dashboard or kubectl.

Kyma dashboard is a web-based UI providing a graphical overview of your cluster and all its resources. To access Kyma dashboard, use the link available in the **Kyma Environment** section of your subaccount *Overview*.



<a name="task_etb_jfy_ddc__steps-unordered_lbf_4fy_ddc"/>

## Procedure

-   Use Kyma dashboard.

    1.  In the *Namespaces* view, go to the namespace you want to work in.

    2.  Go to *Service Management* \> *Service Instances*.

    3.  In the *BTP Access Credentials Secret* field, add the name of the custom Secret you have created.

    4.  Provide other required service details and create a service instance.

        > ### Caution:  
        > Once you set a Secret name in the service instance, you cannot change it in the future.

        You see the status ***PROVISIONED***.


-   Use kubectl.

    1.  Create your service instance with:

        -   The `btpAccessCredentialsSecret` field in the `spec` pointing to the custom pointing to the custom Secret you have created.

        -   other parameters as needed


        > ### Caution:  
        > Once you set a Secret name in the service instance, you cannot change it in the future.

        See an example of a `ServiceInstance` CR:

        ```
        kubectl create -f - <<EOF
        apiVersion: services.cloud.sap.com/v1
        kind: ServiceInstance
        metadata:
          name: {SERVICE_INSTANCE_NAME}
          namespace: {NAMESPACE_NAME}
        spec:
          serviceOfferingName: {SERVICE_OFFERING_NAME}
          servicePlanName: {SERVICE_PLAN_NAME}
          btpAccessCredentialsSecret: {YOUR_SECRET_NAME}
        EOF
        ```

    2.  To verify that your service instance has been created successfully, run:

        ```
        kubectl get serviceinstances.services.cloud.sap.com {SERVICE_INSTANCE_NAME} -n {NAMESPACE}
        ```

        You see the status ***Created*** and the message that your service instance has been created successfully. You also see your Secret name in the `btpAccessCredentialsSecret` field of the `spec`.

    3.  To verify that you've correctly added the access credentials of the SAP Service Manager instance in your service instance, go to the custom resource \(CR\) `status` section, and make sure the subaccount ID to which the instance belongs is provided in the `subaccountID` field. The field must not be empty.



