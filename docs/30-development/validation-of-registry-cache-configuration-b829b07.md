<!-- loiob829b07d96f94269a23259983263b4d4 -->

# Validation of Registry Cache Configuration

Learn how the Registry Cache webhook validates `RegistryCacheConfig` custom resources \(CRs\), how Kyma Control Plane \(KCP\) processes them, and what validation rules apply to each field.

When you apply a `RegistryCacheConfig` resource, the Registry Cache webhook validates the configuration on the Kyma runtime side before the Kubernetes API accepts it. If the configuration is invalid, the API rejects the request and returns an error - no custom resource is created.

Example error message:

```
admission webhook "registrycacheconfig-v1beta1.kb.io" denied the request: spec.upstream: Invalid value: "dockerrrrr.io": upstream is not DNS resolvable
```

If the CR is accepted, KCP processes it. The status transitions from *Pending* to *Ready* on success, or to *Error* if KCP-side processing fails. For details, check `status.conditions`.

KCP periodically reconciles `RegistryCacheConfig` resources. During reconciliation, a CR in *Ready* state transitions back to *Pending* and then returns to *Ready* once reconciliation completes. This is expected behavior.

The following table describes the validation rules for each field.

**Validation Rules**


<table>
<tr>
<th valign="top">

Field

</th>
<th valign="top">

Validation

</th>
</tr>
<tr>
<td valign="top">

`spec.upstream`

</td>
<td valign="top">

Must be a valid DNS-resolvable host \(no scheme\). Must be unique across all `RegistryCacheConfig` resources in the cluster. Port, if specified, must be in the range 1–65535.

</td>
</tr>
<tr>
<td valign="top">

`spec.remoteURL`

</td>
<td valign="top">

Must have the format `<scheme><host>[:<port>]` where `<scheme>` is `https://` or `http://` and `<host>[:<port>]` corresponds to the upstream. Must be DNS resolvable.

</td>
</tr>
<tr>
<td valign="top">

`spec.secretReferenceName`

</td>
<td valign="top">

The referenced Secret must exist in the same namespace as the `RegistryCacheConfig` resource, be immutable, and contain exactly the `username` and `password` data keys.

</td>
</tr>
<tr>
<td valign="top">

`spec.volume.size`

</td>
<td valign="top">

Must be a positive value in a format recognized by Go's `resource.Quantity` \(for example, `10Gi`\). Immutable after creation.

</td>
</tr>
<tr>
<td valign="top">

`spec.volume.storageClassName`

</td>
<td valign="top">

The referenced storage class must be available. Immutable after creation.

</td>
</tr>
<tr>
<td valign="top">

`spec.garbageCollection.ttl`

</td>
<td valign="top">

Must be in a format recognized by Go's `time.ParseDuration` \(for example, `24h`\). Set to `0s` to disable garbage collection. Cannot be re-enabled once disabled.

</td>
</tr>
<tr>
<td valign="top">

`spec.proxy.httpProxy`

</td>
<td valign="top">

Must be a valid URL starting with `http://` or `https://`.

</td>
</tr>
<tr>
<td valign="top">

`spec.proxy.httpsProxy`

</td>
<td valign="top">

Must be a valid URL starting with `http://` or `https://`.

</td>
</tr>
<tr>
<td valign="top">

`spec.http.tls`

</td>
<td valign="top">

Must be a valid boolean indicating whether TLS is enabled.

</td>
</tr>
</table>

