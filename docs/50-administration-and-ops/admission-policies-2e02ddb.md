<!-- loio2e02ddb5b3b9459da6056a5aaafaf421 -->

# Admission Policies

Learn about the validating admission policies deployed in SAP BTP, Kyma runtime clusters, why they block specific actions, and what you can do if you need an exception. These policies are enforced at admission time and protect cluster stability, security, and operational correctness.



<a name="loio2e02ddb5b3b9459da6056a5aaafaf421__section_bqd_wqd_bhc"/>

## Namespaces Delete Protection

This policy prevents the deletion of the `istio-system` and `kyma-system` namespaces unless the request comes from an allowed service account.

The `istio-system` and `kyma-system` namespaces host critical platform components. An accidental or unauthorized deletion of these namespaces can cause cluster-wide outages, break service mesh functionality, and interfere with platform lifecycle operations.

When you try to delete these namespaces, you encounter an API error. The validating admission policy returns a rejection with the message that you cannot delete the `istio-system` or `kyma-system` namespaces. This action requires an authorized service account.

Verify that you're targeting the correct namespace and use application namespaces instead of the system namespaces.



<a name="loio2e02ddb5b3b9459da6056a5aaafaf421__section_icm_mnb_dhc"/>

## Kyma System Protection \(Workload Deletion in `kyma-system`\)

This policy prevents the deletion of workloads \(Deployments, StatefulSets, DaemonSets, Jobs, CronJobs\) inside the `kyma-system` namespace unless the request comes from an allowed user, group, or service account.

The `kyma-system` namespace runs managed Kyma components. Deleting workloads there can break the control plane, integrations, and user-facing services. This policy prevents accidental disruption and enforces that only trusted controllers or processes make such changes.

When you try to delete a workload in `kyma-system`, you see a rejection at the API admission step with the message that you cannot delete workloads in the `kyma-system` namespace. This action requires an authorized user, group, or service account.

When you delete workloads, verify that you're targeting the correct namespace. For changes to customer workloads, use their application namespaces rather than `kyma-system`.



<a name="loio2e02ddb5b3b9459da6056a5aaafaf421__section_bzw_4nb_dhc"/>

## Kube-System Istio Injection Prevention

This policy prevents adding the label `istio-injection=enabled` to the `kube-system` namespace.

Enabling Istio sidecar injection in `kube-system` can unintentionally inject proxies into critical system components. These components can be incompatible with sidecars, which could lead to degraded performance, bootstrap failures, or networking issues for platform services.

The label add or patch requests that attempt to set `istio-injection=enabled` on the `kube-system` namespace are rejected with the message that this label cannot be added here.

Double-check why you need injection in `kube-system`. Commonly, you can isolate your components by enabling sidecar injection in the specific application namespaces instead.



<a name="loio2e02ddb5b3b9459da6056a5aaafaf421__section_a2j_qnb_dhc"/>

## Dynakube Kyma Exclusion

This policy validates that Dynatrace Dynakube custom resources include namespace-exclusion rules so that Kyma-managed namespaces \(for example, `kyma-system`, `istio-system`, `sap-transp-proxy-system`, `ztis-agent-system`, or namespaces with label `operator.kyma-project.io/managed-by=kyma`\) are excluded from automatic instrumentation.

If the required exclusions are missing, the admission policy denies the resource.

Automatic instrumentation across Kyma-managed infrastructure may interfere with Kyma's lifecycle management, generate noisy metrics or logs, or cause unexpected side effects in platform-managed namespaces. Explicit exclusions ensure that monitoring is applied where safe and desired without interfering with platform-managed components.

The policy checks the following fields depending on your Dynakube API version and configuration:

-   `spec.metadataEnrichment.namespaceSelector.matchExpressions` \(if `metadataEnrichment` is enabled\)
-   `spec.oneAgent.cloudNativeFullStack.namespaceSelector.matchExpressions` \(if `cloudNativeFullStack` is configured\)
-   `spec.oneAgent.applicationMonitoring.namespaceSelector.matchExpressions` \(if `applicationMonitoring` is configured\)
-   `spec.namespaceSelector.matchExpressions` \(for Dynakube API version v1beta1\)

If your Dynakube setup is missing required exclusions, an error message tells you to which field you must add them.

For configuration examples, see [Kyma: Dynatrace Setup](https://kyma-project.io/external-content/telemetry-manager/docs/user/integration/dynatrace/README.html#dynatrace-setup) and [Dynatrace: DynaKube parameters for Dynatrace Operator](https://docs.dynatrace.com/docs/ingest-from/setup-on-k8s/reference/dynakube-parameters).

