<!-- loiob62ce80ca9934ebb98f38dbc0d91c234 -->

# Restart of Workloads in the Istio Service Mesh

When you add workloads to the Istio service mesh, you must be aware that the Istio module handles the automatic restart of these workloads. A restart happens in two scenarios:

-   During Istio updates
-   When you update certain fields in the Istio configuration

To effectively monitor your workloads, learn when and why they might be restarted. The Istio module restarts both types of sidecar containers: regular ones and Kubernetes native sidecars.

> ### Remember:  
> To improve resiliency and ensure continuous service operation during the Istio module's rollouts, you must properly configure [Pod Disruption Budgets \(PDBs\)](https://kubernetes.io/docs/tasks/run-application/configure-pdb/) in Kubernetes. Additionally, for PDBs to function correctly, your application must be well prepared to run in the Kubernetes environment. This includes implementing [Kubernetes probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/). For more information, see [Develop Resilient Applications in the Kyma Runtime](develop-resilient-applications-in-the-kyma-runtime-7c9496c.md). Adhering to these practices highly reduces the risk of disruptions caused by workload restarts.



<a name="loiob62ce80ca9934ebb98f38dbc0d91c234__section_eqx_n1c_hgc"/>

## Workload Restart During Istio Updates

The main function of the Istio module is to install Istio within your Kubernetes cluster and ensure it remains up-to-date. To achieve this, new versions of the Istio module often install updated versions of Istio in your Kyma runtime. The module handles the update process, saving you the time and effort of manually rolling the Istio updates.

When a new version of the Istio module installs an updated version of Istio, workloads that are part of the Istio service mesh \(those that have Istio sidecar proxies injected into them\) are automatically restarted.

To understand why the update is required in this scenario, it's important to grasp the architecture of the Istio service mesh. The Istio service mesh consists of two primary components: the data plane and the control plane. The data plane is a set of proxies mediating and controlling network communication between microservices, while the control plane is responsible for managing and configuring these proxies. During an Istio update, the module deploys an updated version of the control plane. Then, to maintain compatibility between the control plane and the data plane, the Istio module must restart any workloads with Istio sidecar proxies running alongside them. This step ensures that Istio sidecar proxies can properly communicate with the updated control plane. Without the Istio module managing this process, you must manually deploy the new control plane and manually restart the workloads with sidecar proxies to retrigger sidecar injection.

If you uninstall Istio from your Kyma runtime, the workloads are restarted to remove the Istio sidecar proxies.



<a name="loiob62ce80ca9934ebb98f38dbc0d91c234__section_rqw_41c_hgc"/>

## Workload Restart During Istio Configuration Updates

Another major feature of the Istio module is managing the Istio configuration. During Istio installation, the Istio module provides opinionated Istio configuration and ensures that it is correctly applied. Then, the module provides you with access to a subset of this configuration through the Istio CR. By editing the Istio CR, you can modify specific fields and apply your changes.

If you modify the Istio CR, the Istio module ensures that these changes are effective. In some cases, to successfully apply the updated settings, the module must restart Pods that have an Istio sidecar proxy injected. The restart is necessary in the following cases:

-   When you update the field `spec.config.telemetry.metrics.prometheusMerge` in the Istio CR.
-   When you enable the compatibility mode \(`spec.compatibilityMode`\), and the compatibility version introduces any flags to the Istio proxy component.
-   When you update the field `spec.config.NumTrustedProxies` in the Istio CR, only Istio sidecar proxies that are part of the `istio-ingressgateway` Deployment are restarted.



<a name="loiob62ce80ca9934ebb98f38dbc0d91c234__section_iwn_pbc_hgc"/>

## When a Workload Can't Be Restarted

Restarting the Istio sidecar proxies is possible for all resources that allow for a rolling restart. However, if a resource is a Job or a Pod that is not managed by any other resource, the restart can't be performed automatically. In such cases, a warning is logged, and you must manually restart the resources. See [Incompatible Sidecar Version After the Istio Module’s Update](incompatible-sidecar-version-after-the-istio-module-s-update-31a52b9.md).

The Istio module does not restart an Istio sidecar proxy if it has a custom image set. See [Resource Annotations](https://istio.io/latest/docs/reference/config/annotations/#SidecarProxyImage).

> ### Caution:  
> Istio-injected Pods with `restartPolicy: Never` may end up in a permanently broken state due to a known issue in Istio. See [issue \#49210](https://github.com/istio/istio/issues/49210). If you need to use this setting, you must be aware of the risk until the issue is fixed. If you don’t have a specific need for setting `restartPolicy` to *Never*, consider using a different option.

