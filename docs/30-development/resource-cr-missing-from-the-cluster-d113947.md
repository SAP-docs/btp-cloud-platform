<!-- loiod113947c54184edfb875a6c833a76db0 -->

# Resource CR Missing from the Cluster



<a name="loiod113947c54184edfb875a6c833a76db0__section_njy_ctj_tgc"/>

## Symptom

Your service instance or binding is visible in SAP Business Technology Platform \(BTP\), but its corresponding custom resource \(CR\) is missing from your Kyma cluster.



<a name="loiod113947c54184edfb875a6c833a76db0__section_ehk_dtj_tgc"/>

## Cause

The CR representing an SAP BTP service instance or service binding is absent from the Kyma cluster. This happens if the CR was accidentally deleted or if there are issues preventing its synchronization or visibility in the cluster. While the resource still exists, the connection to your Kyma cluster is broken due to the absence of the CR.



<a name="loiod113947c54184edfb875a6c833a76db0__section_jw5_dtj_tgc"/>

## Solution

To address this issue, you can manually recreate the service instance CR or service binding CR using details from SAP BTP to restore the connection with the existing SAP BTP resource. For successful reconnection, ensure that the new CR matches the name, resides in the same namespace, and is linked to the same cluster ID as the original CR. Since the SAP BTP resource maintains its configuration, matching these attributes allows the new CR to reconnect to the existing SAP BTP resource without provisioning a new one.

To restore the CR, follow these steps:

1.  Retrieve the following CR details from the service instance or binding:
    -   The CR name
    -   The name of the namespace where the CR should reside

2.  Create your YAML manifest for the CR, including the exact name and namespace you retrieved from the SAP BTP service instance or binding.
3.  To recreate the CR in your Kyma cluster, run:

    ```
    kubectl apply -f {YAML_MANIFEST}
    ```

4.  To verify recreation of the CR in your Kyma cluster, replace the placeholders and run:

    ```
    kubectl get serviceinstances.services.cloud.sap.com {SERVICE_INSTANCE_NAME} -n {NAMESPACE}
    ```

    Or

    ```
    kubectl get servicebindings.services.cloud.sap.com {BINDING_NAME} -n {NAMESPACE}
    ```

5.  Review the service instance or binding in SAP BTP to confirm it recognizes the re-established connection with the CR in your Kyma cluster.

If the connection is not re-established, ensure that your Kyma cluster's ID matches the cluster ID associated with the SAP BTP service instance or binding. To view the cluster ID in the SAP BTP cockpit, go to *Services* \> *Instances and Subscriptions*. It's under *Instances*, in the `Scope` column, in the row that provides information about the service instance. Alternatively, you can view the cluster ID using the SAP BTP command line interface \(btp CLI\). If you discover mismatched IDs, reconfigure your Kyma cluster with the correct cluster ID.

