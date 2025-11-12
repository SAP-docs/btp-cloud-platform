<!-- loio4c78f5830663468588f3d45fac976e0e -->

# Verify Image Signatures in the Kyma Environment

Image signing and image signature verification are important countermeasures against security threats. They help you ensure the authenticity and integrity of the application you deploy in the runtime. You can be sure that what you deploy is what you have built in the build pipeline. While image signing happens in the automated Continuous Delivery \(CD\) workflow, image signature verification takes place at the time the workload is scheduled in the runtime. For this purpose, Kyma uses Warden, a mandatory security feature, which is added to your cluster by default and ensures that the Kyma workloads are authentic.

Warden is automatically enabled in the namespaces managed by Kyma, which can be identified by the `operator.kyma-project.io/managed-by: kyma` label. Therefore, you can be sure the Kyma-managed workloads are authentic. Use the `kubectl get namespace -l operator.kyma-project.io/managed-by=kyma` command to list the Kyma system namespaces, protected by Warden.

> ### Caution:  
> When you enable third-party Kubernetes tools that mutate workloads \(for example, Dynatrace that adds init containers\), you must exclude the Kyma-managed namespaces, which are protected by Warden, from the tool config. Otherwise, Warden blocks unknown images. Mind that disrupting the Kyma-managed namespaces may lead to an inability to uphold the Service Level Agreement \(SLA\).

You can enable Warden also in your namespaces. All you need to do is add the `namespaces.warden.kyma-project.io/validate=user` label to a namespace and provide a notary service URL as an annotation. Warden then verifies if the images used for the workloads in these namespaces are signed by the configured notary service.

If an image is not signed or explicitly allowed by a dedicated annotation and is used to schedule a Pod in the protected namespace, the Pod admission is rejected.



<a name="loio4c78f5830663468588f3d45fac976e0e__section_zgg_my4_hdc"/>

## Configuration

To enable Warden in your namespace, add the `namespaces.warden.kyma-project.io/validate: user` label to the given namespace. You can configure Warden on each namespace by adding the following annotations:


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Required

</th>
<th valign="top">

Description

</th>
<th valign="top">

Default value

</th>
</tr>
<tr>
<td valign="top">

`namespaces.warden.kyma-project.io/notary-url`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

URL of the Notary server used for image verification.

</td>
<td valign="top">

""

</td>
</tr>
<tr>
<td valign="top">

`namespaces.warden.kyma-project.io/allowed-registries`

</td>
<td valign="top">

No

</td>
<td valign="top">

Comma-separated list of image URL prefixes for which the signature verification should be skipped. With that, you can configure exceptions for selected images, registry folders, or whole registries. For example, to let Warden skip the verification of the `foo:0.0.1` and `bar:0.0.1` images \(and tags\) use the following value:

`acme.common.repositories.cloud.sap/foo:0.0.1, acme.common.repositories.cloud.sap/bar:0.0.1`

To skip all images from a given registry, use:

`acme.common.repositories.cloud.sap/`

</td>
<td valign="top">

""

</td>
</tr>
<tr>
<td valign="top">

`namespaces.warden.kyma-project.io/notary-timeout`

</td>
<td valign="top">

No

</td>
<td valign="top">

Timeout for the Notary server connection.

</td>
<td valign="top">

"30s"

</td>
</tr>
<tr>
<td valign="top">

`namespaces.warden.kyma-project.io/strict-mode`

</td>
<td valign="top">

No

</td>
<td valign="top">

If set to `true`, Warden rejects all images when the Notary server is unavailable. If set to `false`, Warden adds the label `pods.warden.kyma-project.io/validate: pending` to the Pod and retries the validation later.

</td>
<td valign="top">

"true"

</td>
</tr>
</table>



### Example Configuration

Example namespace configuration verified by Warden.

```
apiVersion: v1
kind: Namespace
metadata:
  name: my-namespace
  labels:
    namespaces.warden.kyma-project.io/validate: "user"
  annotations:
    namespaces.warden.kyma-project.io/notary-url: "https://signing.repositories.cloud.sap"
    namespaces.warden.kyma-project.io/allowed-registries: "acme.common.repositories.cloud.sap/foo:0.0.1, acme.common.repositories.cloud.sap/bar:0.0.1"
    namespaces.warden.kyma-project.io/notary-timeout: "30s"
    namespaces.warden.kyma-project.io/strict-mode: "true"
```

