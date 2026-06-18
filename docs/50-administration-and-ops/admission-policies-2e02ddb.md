<!-- loio2e02ddb5b3b9459da6056a5aaafaf421 -->

# Admission Policies

Learn about the validating admission policies deployed in SAP BTP, Kyma runtime clusters, why they block specific actions, and what you can do if you need an exception. These policies are enforced at admission time and protect cluster stability, security, and operational correctness.



<a name="loio2e02ddb5b3b9459da6056a5aaafaf421__section_bqd_wqd_bhc"/>

## Namespaces Delete Protection

This policy prevents the deletion of Kyma-managed namespaces unless the request comes from an allowed user, group, or service account.

The following namespaces host critical platform components and are protected from deletion:

-   `istio-system`
-   `kyma-system`
-   `sap-transp-proxy-system`
-   `ztis-agent-system`
-   `docker-registry`
-   `registry-proxy`

An accidental or unauthorized deletion of these namespaces can cause cluster-wide outages, break service mesh functionality, and interfere with platform lifecycle operations.

When you try to delete these namespaces, you receive an API error. The validating admission policy returns a rejection with the message that you cannot delete the Kyma-managed namespaces. This action requires an allowed user, group, or service account.

Verify that you're targeting the correct namespace and use application namespaces instead of the Kyma-managed system namespaces.



<a name="loio2e02ddb5b3b9459da6056a5aaafaf421__section_icm_mnb_dhc"/>

## Kyma System Protection \(Workload Deletion in `kyma-system`\)

This policy prevents the deletion of workloads \(Deployments, StatefulSets, DaemonSets, Jobs, CronJobs\) inside the `kyma-system` namespace unless the request comes from an allowed user, group, or service account.

The `kyma-system` namespace runs managed Kyma components. Deleting workloads there can break the control plane, integrations, and user-facing services. This policy prevents accidental disruption and enforces that only trusted controllers or processes make such changes.

When you try to delete a workload in `kyma-system`, you see a rejection at the API admission step with the message that you cannot delete workloads in the `kyma-system` namespace. This action requires an allowed user, group, or service account.

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



## Enforce Kyma Workload Traffic

This policy prevents the use of network policies with `default-deny-all` rules in the Kyma-managed namespaces. Such network policies block essential communication between Kyma components within a cluster, potentially leading to system failures.

If you attempt to create or update a network policy that violates this rule, the action is blocked, and you receive a warning. In such a case, review your network policy configuration and ensure it includes specific allow rules instead of denying all traffic. For applications that require strict network isolation, consider using your own namespaces instead of the Kyma-managed namespaces.



## Kyma Module Label Protection

This policy prevents you from setting labels with the `kyma-project.io/` prefix on any resource in Kyma-managed namespaces.

The `kyma-project.io/` label prefix is reserved exclusively for Kyma module operators to identify and manage their resources. When your resource in a protected namespace carries a `kyma-project.io/` label, Kyma module operators may misidentify it as a module operator-managed resource. This misidentification causes the operator to enter an error state.

The following namespaces are protected:

-   `kyma-system`
-   `istio-system`
-   `docker-registry`
-   `registry-proxy`
-   `sap-trans-proxy-system`
-   `ztis-agent-system`

When you create or update a resource with a `kyma-project.io/` label in one of these namespaces, you receive an API error message stating that setting reserved labels isn't allowed.

-   If you need to categorize or identify your resources, use your own label prefix instead of the reserved `kyma-project.io/` prefix.
-   If you're deploying workloads that require such a label, deploy them into your own application namespaces rather than into Kyma-managed system namespaces.



## Kyma Storage Protection

This policy prevents you from deleting PersistentVolumeClaims \(PVCs\) in the `kyma-system` namespace and PersistentVolumes \(PVs\) that are bound to a `kyma-system` PVC, unless the request comes from an allowed user, group, or service account.

The `kyma-system` namespace may use persistent storage for platform components. Deleting a PVC or its bound PV can result in permanent data loss for those components. This policy ensures that only trusted users, groups, or service accounts can remove storage resources tied to platform operations.

When you try to delete a PVC in `kyma-system`, or a PV that is bound to a PVC in `kyma-system`, you receive an API error. The error message states that this deletion isn't allowed and requires an allowed user, group, or service account.

Verify that you're targeting the correct resource. If you need to remove storage in `kyma-system`, contact your platform administrator to perform the operation with an allowed user, group, or service account.



<a name="loio2e02ddb5b3b9459da6056a5aaafaf421__section_kyverno_namespace_protection"/>

## Kyverno Namespace Protection

This policy validates that Kyverno ClusterPolicies and policies that affect workloads, such as Pods, Deployments, StatefulSets, DaemonSets, Jobs, CronJobs, ReplicaSets, include an `exclude` block that covers Kyma-managed namespaces.

Kyverno policies without explicit exclusions can inadvertently match resources in Kyma-managed namespaces, such as `kyma-system` and `istio-system`. This can cause mutations or validations to interfere with platform-managed components and lead to instability or failed reconciliation of Kyma modules.

When you create or update a Kyverno policy that affects workloads but is missing the required exclusions, you receive a warning. The operation isn't blocked, but you should address the warning to avoid unintended impact on Kyma components.

Add an `exclude` block to each rule that affects workloads. Use one of the following approaches:

-   Label-based exclusion \(recommended\): Exclude namespaces with the selector `operator.kyma-project.io/managed-by NotIn [kyma]`. This label automatically covers all current and future Kyma-managed namespaces.
-   Explicit namespace exclusion: List both `kyma-system` and `istio-system` in the `exclude` block's `namespaces` field.

