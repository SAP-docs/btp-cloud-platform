<!-- loio6bbd26b74ffd48c9bb304cf04cf2cabb -->

# Adapting Your Workloads to Kyma Landscape Requirements

Learn how to use Runtime Bootstrapper, a built-in Kyma component, to automatically adapt your Pods to landscape-specific requirements such as private registries, custom TLS certificates, and FIPS mode signaling.

> ### Note:  
> The content in this topic is only relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

When you deploy workloads on SAP BTP, Kyma runtime in certain regions, such as China \(Shanghai\) and Government Cloud \(US\), Pods need specific configurations. For example, Pods may need to pull images from a private registry or trust landscape-specific TLS certificates. Runtime Bootstrapper automatically applies these configurations to your Pods at creation time. This process is transparent and requires no changes to your application code.

Runtime Bootstrapper only modifies Pods. It doesn't affect any other Kubernetes resources, such as Deployments, Services, ConfigMaps, or Secrets.



<a name="loio6bbd26b74ffd48c9bb304cf04cf2cabb__section_enabling_rtb_fkz"/>

## Enabling Runtime Bootstrapper

To enable Runtime Bootstrapper features, annotate either a namespace or a Pod \(or Pod template\).



### Annotating a Namespace

Add one or more feature annotations to your namespace. All Pods created in that namespace then receive the corresponding adjustments automatically. You don't need to change individual workload manifests.

```
apiVersion: v1
kind: Namespace
metadata:
  name: my-namespace
  annotations:
    rt-cfg.kyma-project.io/alter-img-registry: "true"
    rt-cfg.kyma-project.io/add-img-pull-secret: "true"
```



### Annotating a Pod or a Pod Template

Add annotations directly to your Pod or to the `spec.template.metadata.annotations` section of a Deployment, StatefulSet, or a similar resource. As a result, only that specific Pod or Pods from that template are adjusted.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  template:
    metadata:
      annotations:
        rt-cfg.kyma-project.io/alter-img-registry: "true"
        rt-cfg.kyma-project.io/add-img-pull-secret: "true"
    spec:
      containers:
        - name: my-container
          image: my-registry.example.com/my-app:1.0.0
```

You can combine both methods. If you enable a feature on a namespace, all Pods in that namespace benefit from it. There is no way to opt out at the Pod level.



<a name="loio6bbd26b74ffd48c9bb304cf04cf2cabb__section_supported_annotations_wqx"/>

## Supported Annotations

Each annotation enables one specific feature. To activate it, set the value to *true*.

The availability shown below may change. To confirm a feature is active in your landscape, see [Confirming a Pod Was Modified](adapting-your-workloads-to-kyma-landscape-requirements-6bbd26b.md#loio6bbd26b74ffd48c9bb304cf04cf2cabb__section_confirming_pod_modified_bnz). If a feature appears inactive despite being listed as available, contact your landscape operator.


<table>
<tr>
<th valign="top">

Annotation

</th>
<th valign="top">

Typical use case

</th>
<th valign="top">

Relevant to Government Cloud \(US\)

</th>
<th valign="top">

Relevant to China \(Shanghai\)

</th>
</tr>
<tr>
<td valign="top">

[`rt-cfg.kyma-project.io/add-cluster-trust-bundle`](adapting-your-workloads-to-kyma-landscape-requirements-6bbd26b.md#loio6bbd26b74ffd48c9bb304cf04cf2cabb__annotation_trust_bundle)

</td>
<td valign="top">

Mounts custom CA certificates required to trust SAP backend endpoints

</td>
<td valign="top">

Yes, it's a primary feature. The CA bundle is managed by the landscape operator team. If TLS communication fails due to missing or outdated certificates, create a support ticket. See [Getting Support](https://help.sap.com/docs/btp/sap-business-technology-platform/btp-getting-support?locale=en-US&version=Cloud&state=PRODUCTION).

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

[`rt-cfg.kyma-project.io/add-img-pull-secret`](adapting-your-workloads-to-kyma-landscape-requirements-6bbd26b.md#loio6bbd26b74ffd48c9bb304cf04cf2cabb__annotation_add_img_pull_secret)

</td>
<td valign="top">

Only relevant when pulling images from a private registry that requires authentication

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

[`rt-cfg.kyma-project.io/alter-img-registry`](adapting-your-workloads-to-kyma-landscape-requirements-6bbd26b.md#loio6bbd26b74ffd48c9bb304cf04cf2cabb__annotation_alter_img_registry)

</td>
<td valign="top">

Only required when the container registry hostname must be rewritten to a landscape-specific mirror

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

[`rt-cfg.kyma-project.io/set-fips-mode`](adapting-your-workloads-to-kyma-landscape-requirements-6bbd26b.md#loio6bbd26b74ffd48c9bb304cf04cf2cabb__annotation_set_fips_mode)

</td>
<td valign="top">

Signals to workloads that FIPS 140-compliant cryptography should be used

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
</table>

> ### Tip:  
> To enable all features available in your region at once, use the shorthand annotation [`rt-cfg.kyma-project.io/all: "true"`](adapting-your-workloads-to-kyma-landscape-requirements-6bbd26b.md#loio6bbd26b74ffd48c9bb304cf04cf2cabb__annotation_all) on either a namespace or a Pod.



### `rt-cfg.kyma-project.io/add-cluster-trust-bundle`

The annotation mounts the cluster's TLS certificate bundle into your containers and automatically restarts Pods when the CA bundle changes

Some landscapes use custom TLS certificates that are not included in the standard operating system trust store. When you enable this feature, Runtime Bootstrapper mounts the cluster's certificate bundle as a read-only volume into every container \(including init-containers\) under the path `/etc/ssl/certs`. As a result, your application can trust landscape-specific HTTPS endpoints without any code changes.

The annotation accepts the following values:


<table>
<tr>
<th valign="top">

Value

</th>
<th valign="top">

Behavior

</th>
</tr>
<tr>
<td valign="top">

*"true"*

</td>
<td valign="top">

Mount the CA bundle and automatically restart the Pod when the bundle changes

</td>
</tr>
<tr>
<td valign="top">

*"false"*

</td>
<td valign="top">

Explicit opt-out - no CA bundle mount, even if namespace defaults enable it

</td>
</tr>
</table>

The annotation causes the following changes in your Pod:

-   `.spec.volumes[]` - a projected volume named `rt-bootstrapper-certs` is added
-   `.spec.containers[*].volumeMounts` - the volume is mounted read-only at `/etc/ssl/certs`
-   `.spec.initContainers[*].volumeMounts` - same mount applied to init-containers
-   `.metadata.annotations["rt-bootstrapper.kyma-project.io/ctb-hash"]` - a SHA-256 hash of the current CA bundle content, used to detect changes. This annotation is stamped on every Pod that receives the CA bundle, regardless of whether the opt-in came from a Pod annotation, namespace annotation, or namespace defaults.

**Explicit Opt-Out**

If you set the annotation to `"false"` on a Pod, it explicitly opts out of the CA bundle mount. This overrides namespace-level defaults. Use it when a specific workload must not receive the certificate bundle.

```
annotations:
  rt-cfg.kyma-project.io/add-cluster-trust-bundle: "false"
```

**Automatic Restart on Certificate Rotation**

Runtime Bootstrapper automatically restarts Pods when the `ClusterTrustBundle` CA changes. A built-in controller watches the `ClusterTrustBundle` resource and computes a SHA-256 hash of its content. When the hash changes, the controller scans all namespaces for Pods whose stamped hash no longer matches and deletes them. The owning controller \(for example, a Deployment's ReplicaSet\) recreates the Pods, and the webhook stamps the new hash during admission.

Only Pods managed by an owner \(for example, a ReplicaSet or StatefulSet\) are restarted. Standalone Pods without an owner still receive the CA bundle and the hash annotation but are never deleted to avoid data loss.

This means your application does not need to implement file watching or any other mechanism to handle certificate rotation. The restart ensures the new certificate is loaded at startup.

> ### Tip:  
> If your application can reload TLS trust stores at runtime \(for example, by watching for file changes under `/etc/ssl/certs`\), it can pick up the new certificates without a restart. The automatic restart acts as a safety net for applications that load certificates only at startup.

**Enabling Automatic Restart in Your Namespace**

The restart controller can only operate in namespaces where the Runtime Bootstrapper ServiceAccount has Pods *get*, *list*, and *delete* permissions. By default, these permissions are configured for Kyma-managed namespaces \(for example, `kyma-system`, `istio-system`\). To enable automatic restarts in your own namespace, create a RoleBinding that grants the required permissions. Replace `my-namespace` with your namespace name:

```
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: rt-bootstrapper-pod-restarter-my-namespace
  namespace: my-namespace
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: rt-bootstrapper-pod-restarter-role
subjects:
- kind: ServiceAccount
  name: rt-bootstrapper-controller-manager
  namespace: kyma-system
```

Without this binding, the controller logs a warning and skips the namespace.



### `rt-cfg.kyma-project.io/add-img-pull-secret`

The annotation injects image pull credentials into your Pod.

When a private container registry requires authentication, Runtime Bootstrapper adds a reference to the landscape's image pull Secret \(`registry-credentials`\) to your Pod. Your Pod can then pull images - you don't have to manage registry credentials yourself.

The annotation causes the following change in your Pod:

-   `.spec.imagePullSecrets[]` - the `registry-credentials` entry is appended

If the Secret reference is already present, it is not added again.



### `rt-cfg.kyma-project.io/alter-img-registry`

The annotation rewrites the container registry host in image references.

Some landscapes require container images to be pulled from a private or landscape-specific registry rather than the original public registry. When you enable this feature, Runtime Bootstrapper automatically rewrites the registry hostname in the `image` field of every container and init-container in your Pod. You don't need to know the target registry address, because it's configured centrally for the landscape.

The annotation causes the following changes in your Pod:

-   `.spec.containers[*].image` - registry hostname is replaced
-   `.spec.initContainers[*].image` - registry hostname is replaced



### `rt-cfg.kyma-project.io/set-fips-mode`

The annotation signals FIPS 140 compliance mode to your workloads.

Federal Information Processing Standards \(FIPS\) mode restricts cryptographic operations to approved algorithms. When you enable this feature, Runtime Bootstrapper sets two environment variables in every container and init-container. Your application can read these variables to activate its own FIPS-compliant code paths.

The annotation causes the following changes in your Pod:

-   `.spec.containers[*].env[]` - the following variables are added to every container:
    -   `KYMA_FIPS_MODE_ENABLED=true`
    -   `FIPS_MODE_ENABLED=true` \(legacy compatibility\)

-   `.spec.initContainers[*].env[]` - the following variables are added to init-containers:
    -   `KYMA_FIPS_MODE_ENABLED=true`
    -   `FIPS_MODE_ENABLED=true` \(legacy compatibility\)




### `rt-cfg.kyma-project.io/all`

The annotation enables all features available for your region at once.

Setting this annotation to *true* applies all features available for your region \(see [Supported Annotations](adapting-your-workloads-to-kyma-landscape-requirements-6bbd26b.md#loio6bbd26b74ffd48c9bb304cf04cf2cabb__section_supported_annotations_wqx)\) that are enabled in the operator's configuration. Use it when you want your namespace or Pod to receive all applicable landscape adaptations without listing them individually.

```
annotations:
  rt-cfg.kyma-project.io/all: "true"
```



<a name="loio6bbd26b74ffd48c9bb304cf04cf2cabb__section_confirming_pod_modified_bnz"/>

## Confirming a Pod Was Modified

After Runtime Bootstrapper processes a Pod, it adds the following annotation to the Pod metadata:

```
rt-bootstrapper.kyma-project.io/modified: "true"
```

To verify this, replace the placeholder and run:

```
kubectl get pod <pod-name> -o jsonpath='{.metadata.annotations.rt-bootstrapper\.kyma-project\.io/modified}'
```

If the output is ***true***, Runtime Bootstrapper applied at least one modification when the Pod was created. This annotation reflects the state at creation time only. If the landscape configuration changes later, recreated Pods might silently receive fewer modifications without automatic notification. If you suspect a feature is no longer active, contact your landscape operator and check the Runtime Bootstrapper logs for relevant warnings:

```
kubectl logs -n kyma-system -l app.kubernetes.io/name=rt-bootstrapper
```

If the output is empty or ***false***, either no feature annotations were set on the Pod or its namespace, or the annotations used are not supported in this landscape. See [Supported Annotations](adapting-your-workloads-to-kyma-landscape-requirements-6bbd26b.md#loio6bbd26b74ffd48c9bb304cf04cf2cabb__section_supported_annotations_wqx).

