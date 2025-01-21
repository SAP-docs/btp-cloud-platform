<!-- loio8f4471de8a0d433aa9f688e599cfe2c0 -->

# Optimizing Sidecars

Configure Istio using the Sidecar resource to minimize the load and footprint.

With automatic Istio sidecar proxy injection enabled, all of your workloads’ Pods get their own sidecar proxy container running next to the application. Using sidecar proxies is beneficial but also has some side effects.



<a name="loio8f4471de8a0d433aa9f688e599cfe2c0__section_xwz_15p_tdc"/>

## **Default Behavior**

By default, Istio enables communication between all the services in the service mesh. As a result, each sidecar proxy receives all the configurations for every service. The configurations contain a lot of Istio-based resource details. Also, when a service scales or a Pod restarts, the Istio control plane always propagates the configurations of all other services to Istio sidecar proxies.

If you have only a few services in your Kyma cluster, this is not a problem. However, as you start expanding your microservice architecture and the number of services grows, you can notice the following effects:

-   Increased network traffic and CPU usage for the Istio control plane.
-   Increased memory usage due to the growing number of configurations stored by each sidecar proxy.
-   Slower changes propagation to the services in the mesh.

All these effects can be solved with the optimized usage of the Istio Sidecar resource.



<a name="loio8f4471de8a0d433aa9f688e599cfe2c0__section_uqr_25p_tdc"/>

## **Optimization**

To select which services communicate with each other, specify the configurations the proxy should get from the Istio control plane using the Sidecar custom resource \(CR\).

In plain language, using the Sidecar CR, you can tell the Istio control plane the following: *There are 500 services in my Kyma runtime, but my application/scenario needs to access only 5. I need details only about those 5.*

See the following example of the Sidecar CR configuration:

> ### Sample Code:  
> ```
> apiVersion: networking.istio.io/v1beta1
> kind: Sidecar
> metadata:
>   name: default
>   namespace: my-namespace
> spec:
>   egress:
>   - hosts:
>     - ./*
>     - istio-system/*
>     - kyma-system/eventing-event-publisher-proxy.kyma-system.svc.cluster.local
> ```

The following table presents the example `egress.hosts` values from the sample code and their corresponding access details.

**Example egress.hosts Values**


<table>
<tr>
<th valign="top">

Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`./*`

</td>
<td valign="top">

Access all services in this namespace.

</td>
</tr>
<tr>
<td valign="top">

`istio-system/*`

</td>
<td valign="top">

Access all services in the `istio-system` namespace.

</td>
</tr>
<tr>
<td valign="top">

`kyma-system/eventing-event-publisher-proxy.kyma-system.svc.cluster.local`

</td>
<td valign="top">

Access the `eventing-event-publisher-proxy` service to publish events.

</td>
</tr>
</table>

> ### Tip:  
> If you want to apply the configuration to specific workloads, configure the `workloadSelector`. For more information, see [Sidecar](https://istio.io/latest/docs/reference/config/networking/sidecar/) in the official Istio documentation.

