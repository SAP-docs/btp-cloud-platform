<!-- loio37ac30af6f7c48a8a10723d8a18f49d5 -->

# Rotating Service Bindings

Enhance security by automatically rotating the credentials associated with your service bindings. This process involves generating a new service binding while keeping the old credentials active for a specified period to ensure a smooth transition.



<a name="loio37ac30af6f7c48a8a10723d8a18f49d5__section_ydz_twx_wcc"/>

## Enabling Automatic Rotation

To enable automatic service binding rotation, use the `credentialsRotationPolicy` field within the `spec` section of the `ServiceBinding` resource. You can configure the following parameters:

**Automatic Rotation Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
<th valign="top">

Valid Values

</th>
</tr>
<tr>
<td valign="top">

`enabled`

</td>
<td valign="top">

bool

</td>
<td valign="top">

Turns automatic rotation on or off.

</td>
<td valign="top">

*true* or *false*

</td>
</tr>
<tr>
<td valign="top">

`rotationFrequency`

</td>
<td valign="top">

string

</td>
<td valign="top">

Defines the desired interval between binding rotations.

</td>
<td valign="top">

*m* \(minutes\) or *h* \(hours\)

</td>
</tr>
<tr>
<td valign="top">

`rotatedBindingTTL`

</td>
<td valign="top">

string

</td>
<td valign="top">

Determines how long to keep the old`ServiceBinding` resource after rotation and before deletion. The actual TTL may be slightly longer.

</td>
<td valign="top">

*m* \(minutes\) or *h* \(hours\)

</td>
</tr>
</table>

> ### Note:  
> The `credentialsRotationPolicy` does not manage the validity or expiration of the credentials themselves. This is determined by the service you are using.

The `credentialsRotationPolicy` is evaluated periodically during a [control loop](https://kubernetes.io/docs/concepts/architecture/controller/) on every service binding update or during a complete reconciliation process. This means the actual rotation occurs in the closest upcoming reconciliation loop.



<a name="loio37ac30af6f7c48a8a10723d8a18f49d5__section_h43_51y_wcc"/>

## Enabling Immediate Rotation

To trigger an immediate rotation regardless of the configured rotation frequency, add the `services.cloud.sap.com/forceRotate: "true"` annotation to the`ServiceBinding` resource. The immediate rotation only works if automatic rotation is already enabled.

The following example shows the configuration of a `ServiceBinding` resource for rotating credentials every 25 days \(600 hours\) and keeping the old `ServiceBinding` resource for 2 days \(48 hours\) before deleting it:

```
apiVersion: services.cloud.sap.com/v1
kind: ServiceBinding
metadata:
  name: {BINDING_NAME}
spec:
  serviceInstanceName: {SERVICE_INSTANCE_NAME}
  credentialsRotationPolicy:
    enabled: true
    rotatedBindingTTL: 48h
    rotationFrequency: 600h
```



<a name="loio37ac30af6f7c48a8a10723d8a18f49d5__section_b4d_lhy_wcc"/>

## Result

Rotating the service binding has the following results:

-   The Secret is updated with the latest credentials.

-   The old credentials are kept in a newly-created Secret named `original-secret-name(variable)-guid(variable)`. This temporary Secret is kept until the configured deletion time \(TTL\).

    To see the timestamp of the last service binding rotation, go to the `status.lastCredentialsRotationTime` field.




<a name="loio37ac30af6f7c48a8a10723d8a18f49d5__section_b4m_q3y_wcc"/>

## Limitations

You cannot enable automatic credential rotation for a backup service binding \(named: `original-binding-name(variable)-guid(variable)`\) marked with the *services.cloud.sap.com/stale* label. This backup service binding is created during the credentials rotation process to facilitate the process.

