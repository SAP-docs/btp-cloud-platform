<!-- loioe7117e191622405ba628aa7c86c77238 -->

# Creating Service Instances or Bindings Fails After Deleting the Service Manager Binding



<a name="loioe7117e191622405ba628aa7c86c77238__section_symptom_qrx"/>

## Symptom

You deleted the SAP Service Manager service binding in the cockpit and now cannot create new SAP BTP service instances or bindings. The SAP BTP Operator module may be failing.



<a name="loioe7117e191622405ba628aa7c86c77238__section_cause_jkm"/>

## Cause

When your Kyma runtime was provisioned, a Service Manager service instance with the `service-operator-access` plan and a corresponding service binding were created automatically. The credentials from that binding are used to populate the `sap-btp-manager` Secret in your cluster, which the SAP BTP Operator module relies on to function.

When you delete the binding, the Kyma infrastructure still holds the old credentials and keeps refreshing the `sap-btp-manager` Secret with them. If you recreate the binding, the new binding has different credentials, but the Secret is still not updated. You can't create new service instances because the SAP BTP Operator module can't authenticate. The support team must manually update the credentials on your behalf.

> ### Note:  
> Alternatively, if the `sap-btp-manager` Secret itself was deleted from the cluster, Kyma's automatic reconciliation restores it within 24 hours — no support ticket is needed. To restore the Secret immediately, use the credentials from the existing binding and follow [Customizing the Default Credentials and Access](customizing-the-default-credentials-and-access-15f22d5.md).

Each Kyma runtime has a dedicated Service Manager instance in a one-to-one relationship. If you have multiple Kyma runtimes, you have multiple Service Manager instances, each with its own binding. The Service Manager instance name in the cockpit matches the instance ID of the corresponding Kyma runtime. You need this mapping to identify the correct instance when raising a support ticket.



<a name="loioe7117e191622405ba628aa7c86c77238__section_solution_wvp"/>

## Solution

1.  In the cockpit, open your Kyma runtime and note its instance ID.
2.  In the list of Service Manager service instances, find the one whose name matches your Kyma instance ID. This is the dedicated Service Manager instance for your Kyma runtime.
3.  In that Service Manager instance, check whether a binding exists.
    -   If no binding exists, recreate it, then proceed to the next step.
    -   If a binding already exists \(whether original or recreated\), proceed to the next step.

4.  Check the binding's creation timestamp and compare it with the Service Manager instance's creation timestamp:
    -   If the binding was created later than the Service Manager instance, it proves the binding was deleted and then recreated. This confirms you're in the scenario described by this guide.
    -   If the timestamps match, the binding has not been recreated and this guide does not apply. Instead, the issue may be caused by deletion of the `sap-btp-manager` Secret from the cluster. See [Cause](creating-service-instances-or-bindings-fails-after-deleting-the-service-manager-binding-e7117e1.md#loioe7117e191622405ba628aa7c86c77238__section_cause_jkm).

5.  Download the binding credentials as a JSON file.
6.  Create a support ticket and attach the credentials JSON file. Include the following information in the ticket:

    -   Your subaccount ID
    -   Your Kyma instance ID
    -   The Service Manager instance name \(which equals your Kyma instance ID\)

    For more information on creating a ticket, see [Getting Support](https://help.sap.com/docs/btp/sap-business-technology-platform/btp-getting-support?locale=en-US&version=Cloud&ai=true).

7.  Wait for the support team to confirm that the `sap-btp-manager` Secret in your cluster is updated with the new credentials.
8.  To verify the fix, create a service instance. If it's created without errors, the issue is resolved.

