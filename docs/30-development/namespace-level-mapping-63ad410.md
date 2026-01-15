<!-- loio63ad410e87de465eba76ff44dd544d41 -->

# Namespace-Level Mapping

You can map a Kubernetes namespace to an SAP Service Manager instance in a given subaccount. The Service Manager instance is then used to provision all service instances in that namespace.



<a name="loio63ad410e87de465eba76ff44dd544d41__prereq_xll_cdf_xcc"/>

## Prerequisites

-   A subaccount in the SAP BTP cockpit.

-   You have the SAP BTP Operator module in your cluster. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).

-   For CLI interactions: [kubectl](https://kubernetes.io/docs/tasks/tools/) configured to communicate with your Kyma instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).




<a name="loio63ad410e87de465eba76ff44dd544d41__context_lhp_b1d_fdc"/>

## Context

To connect a namespace to a specific subaccount, maintain the access credentials to the subaccount in a Secret dedicated to a specific namespace. Create the `{NAMESPACE-NAME}-sap-btp-service-operator` Secret in the `kyma-system` namespace.

<a name="task_nnf_tdz_bdc"/>

<!-- task\_nnf\_tdz\_bdc -->

## Creating a Namespace-Based Secret



<a name="task_nnf_tdz_bdc__steps_ngk_vdz_bdc"/>

## Procedure

1.  In the SAP BTP cockpit, create a new SAP Service Manager service instance with the `service-operator-access` plan. See [Creating Instances in Other Environments](https://help.sap.com/docs/service-manager/sap-service-manager/creating-instances-in-other-environments?locale=en-US&version=Cloud).

2.  Create a service binding to the SAP Service Manager service instance you have created. See [Creating Service Bindings in Other Environments](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-bindings-in-other-environments?locale=en-US&version=Cloud).

3.  Get the access credentials of the SAP Service Manager instance from its service binding. Copy them from the SAP BTP cockpit as a JSON file.

4.  Create the `creds.json` file in your working directory and save the credentials there.

5.  In the same working directory, call the `create-secret-file.sh` script with the `operator` option as the first parameter and `namespace-name-sap-btp-service-operator` Secret as the second parameter:

    ```
    curl https://raw.githubusercontent.com/kyma-project/btp-manager/main/hack/create-secret-file.sh | bash -s operator {NAMESPACE_NAME}-sap-btp-service-operator
    ```

    The expected result is the `btp-access-credentials-secret.yaml` file created in your working directory:

    ```
    apiVersion: v1
    kind: Secret
    type: Opaque
    metadata:
      name: {NAMESPACE_NAME}-sap-btp-service-operator
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

    You see the status ***Created***.


<a name="task_uxw_fmz_bdc"/>

<!-- task\_uxw\_fmz\_bdc -->

## Creating a Service Instance with a Namespace-Based Secret



<a name="task_uxw_fmz_bdc__steps_yw4_54z_bdc"/>

## Procedure

1.  To create a service instance with a namespace-based Secret, follow the instructions in [Creating Service Instances and Service Bindings](creating-service-instances-and-service-bindings-17bd304.md#loio17bd304aeab34294a4ca34fa9564147c).

2.  To verify that you've correctly added the access credentials of the SAP Service Manager instance in your service instance, go to the custom resource \(CR\) `status` section, and make sure the subaccount ID to which the instance belongs is provided in the `subaccountID` field. The field must not be empty.


**Related Information**  


[Working with Multiple Subaccounts](working-with-multiple-subaccounts-862dd6a.md "With the SAP BTP Operator module, you can create configurations for several subaccounts in a single Kyma cluster.")

[Instance-Level Mapping](instance-level-mapping-d9e9c7f.md "You can map a Kubernetes service instance to an SAP Service Manager instance in a given subaccount. The Service Manager instance is then used to provision that service instance.")

