<!-- loio6a13459bcf164a05a2be2c2766c77e0b -->

# Automatic Data Enrichment

The Telemetry gateways automatically enrich your data with OTel resource attributes, so you can easily identify the source of the data in your backend.

> ### Tip:  
> For custom enrichment, such as adding your own business-specific attributes, see [Transform with OTTL](transform-with-ottl-f7bed2c.md).



<a name="loio6a13459bcf164a05a2be2c2766c77e0b__section_enrichment_service_name"/>

## Service Name

The service name is the logical name of the service that emits the telemetry data. The gateway ensures that this attribute always has a valid value.

If you don't provide a service name, or if its value follows the pattern <code>unknown_service:<i class="varname">&lt;process.executable.name&gt;</i></code> as described in the [specification](https://opentelemetry.io/docs/specs/semconv/resource/#service), the gateway generates it from Kubernetes metadata.

The gateway determines the service name based on the following hierarchy of labels and names:

1.  `app.kubernetes.io/name`: Pod label value

2.  `app`: Pod label value

3.  Deployment/DaemonSet/StatefulSet/Job name

4.  Pod name

5.  If none of the above is available, the value is *unknown\_service*




<a name="loio6a13459bcf164a05a2be2c2766c77e0b__section_enrichment_kubernetes"/>

## Kubernetes Metadata

`k8s.*` attributes encapsulate various pieces of Kubernetes metadata associated with the Pod, such as:

-   `k8s.pod.name`: The Kubernetes Pod name of the Pod that emitted the data.

-   `k8s.pod.uid`: The Kubernetes Pod ID of the Pod that emitted the data.

-   `k8s.<workload kind>.name`: The Kubernetes workload name to which the emitting Pod belongs. Workload is either Deployment, DaemonSet, StatefulSet, Job, or CronJob.

-   `k8s.namespace.name`: The Kubernetes namespace name with which the emitting Pod is associated.

-   `k8s.cluster.name`: A logical identifier of the cluster, which, by default, is the API Server URL. To set a custom name, configure the `enrichments.cluster.name` field in the Telemetry CRD.

-   `k8s.cluster.uid`: A unique identifier of the cluster, realized by the UID of the `kube-system` namespace.

-   `k8s.node.name`: The Kubernetes node name to which the emitting Pod is scheduled.

-   `k8s.node.uid`: The Kubernetes Node ID to which the emitting Pod belongs.




<a name="loio6a13459bcf164a05a2be2c2766c77e0b__section_enrichment_pod_label"/>

## Pod Label Attributes

In the [Telemetry CRD](https://kyma-project.io/#/telemetry-manager/user/resources/01-telemetry), you can also specify your own enrichments of telemetry data based on Pod labels.

To capture custom application metadata \(for example, for filtering, grouping, or correlation\), configure specific label keys or label key prefixes to include in the enrichment process. The gateway adds all matching Pod labels to the telemetry data as resource attributes, using the label key format `k8s.pod.label.<label_key>`.

The following example configuration enriches the telemetry data with Pod labels that match the specified keys or key prefixes:

-   `k8s.pod.label.app.kubernetes.io/name`: The value of the exact label key `app.kubernetes.io/name` from the Pod.

-   `k8s.pod.label.app.kubernetes.io.*`: All labels that start with the prefix `app.kubernetes.io` from the Pod, where `*` is replaced by the actual label key.


```
apiVersion: operator.kyma-project.io/v1alpha1
kind: Telemetry
metadata:
  name: default
  namespace: kyma-system
spec:
  enrichments:
    extractPodLabels:
    - key: "<myExactLabelKey>" # for example, "app.kubernetes.io/name"
    - keyPrefix: "<myLabelPrefix>" # for example, "app.kubernetes.io"
```



<a name="loio6a13459bcf164a05a2be2c2766c77e0b__section_enrichment_cloud_provider"/>

## Cloud Provider Attributes

If data is available, the gateway automatically adds [cloud provider](https://opentelemetry.io/docs/specs/semconv/resource/cloud/) attributes to the telemetry data:

-   `cloud.provider`: Cloud provider name
-   `cloud.region`: Region where the Node runs \(from Node label `topology.kubernetes.io/region`\)
-   `cloud.availability_zone`: Zone where the Node runs \(from Node label `topology.kubernetes.io/zone`\)



<a name="loio6a13459bcf164a05a2be2c2766c77e0b__section_enrichment_host"/>

## Host Attributes

If data is available, the gateway automatically adds [host](https://opentelemetry.io/docs/specs/semconv/resource/host/) attributes to the telemetry data:

-   `host.type`: Machine type of the Node \(from Node label `node.kubernetes.io/instance-type`\)
-   `host.arch`: CPU architecture of the system the Node runs on \(from Node label `kubernetes.io/arch`\)

