<!-- loio2269fc21e58144a5acf1eafe75e61bd3 -->

# Default Istio Configuration

Within the Istio module, Istio Operator provides baseline values for the Istio installation, which you can override in the Istio custom resource \(CR\).



See the major differences in the configuration of Istio Operator compared to upstream Istio:

-   The Istiod \(Pilot\) and Ingress Gateway components are enabled by default.
-   Automatic Istio sidecar proxy injection is disabled by default.
-   To enhance security and performance, both [Istio control plane and data plane](https://istio.io/latest/docs/ops/deployment/architecture/) use the distroless version of Istio images. Those images are not Debian-based and are slimmed down to reduce any potential attack surface. To learn more, see [Harden Docker Container Images](https://istio.io/latest/docs/ops/configuration/security/harden-docker-images/).
-   Resource requests and limits for Istio sidecars proxies are modified to best suit the needs of the evaluation and production profiles.
-   [Mutual TLS](https://istio.io/docs/concepts/security/#mutual-tls-authentication) \(mTLS\) is enabled in the *STRICT* mode for workloads in the Istio service mesh.
-   Egress traffic is not controlled. All applications deployed in the Kyma cluster can access outside resources without limitations.
-   The CNI component, used for the installation of an Istio sidecar, is provided as a DaemonSet. This means that one replica is present on every node of the target cluster.
-   The self-signed CA certificate’s bit length is set to *4096* instead of the default *2048*.



### Configuration Based on the Cluster Size

The configuration of Istio resources depends on the cluster capabilities. If your cluster has less than 5 total virtual CPU cores or its total memory capacity is less than 10 gigabytes, the default setup for resources and autoscaling is lighter. If your cluster exceeds both of these thresholds, Istio is installed with the higher resource configuration.

**Default Resource Configuration for Smaller Clusters**


<table>
<tr>
<th valign="top">

Component

</th>
<th valign="top">

CPU Requests

</th>
<th valign="top">

CPU Limits

</th>
<th valign="top">

Memory Requests

</th>
<th valign="top">

Memory Limits

</th>
</tr>
<tr>
<td valign="top">

Proxy

</td>
<td valign="top">

10 m

</td>
<td valign="top">

250 m

</td>
<td valign="top">

32 Mi

</td>
<td valign="top">

254 Mi

</td>
</tr>
<tr>
<td valign="top">

Ingress Gateway

</td>
<td valign="top">

10 m

</td>
<td valign="top">

1000 m

</td>
<td valign="top">

32 Mi

</td>
<td valign="top">

1024 Mi

</td>
</tr>
<tr>
<td valign="top">

Pilot

</td>
<td valign="top">

50 m

</td>
<td valign="top">

1000 m

</td>
<td valign="top">

128 Mi

</td>
<td valign="top">

1024 Mi

</td>
</tr>
<tr>
<td valign="top">

CNI

</td>
<td valign="top">

10 m

</td>
<td valign="top">

250 m

</td>
<td valign="top">

128 Mi

</td>
<td valign="top">

384 Mi

</td>
</tr>
</table>

**Default Resource Configuration for Larger Clusters**


<table>
<tr>
<th valign="top">

Component

</th>
<th valign="top">

CPU Requests

</th>
<th valign="top">

CPU Limits

</th>
<th valign="top">

Memory Requests

</th>
<th valign="top">

Memory Limits

</th>
</tr>
<tr>
<td valign="top">

Proxy

</td>
<td valign="top">

10 m

</td>
<td valign="top">

1000 m

</td>
<td valign="top">

192 Mi

</td>
<td valign="top">

1024 Mi

</td>
</tr>
<tr>
<td valign="top">

Ingress Gateway

</td>
<td valign="top">

100 m

</td>
<td valign="top">

2000 m

</td>
<td valign="top">

128 Mi

</td>
<td valign="top">

1024 Mi

</td>
</tr>
<tr>
<td valign="top">

Pilot

</td>
<td valign="top">

100 m

</td>
<td valign="top">

4000 m

</td>
<td valign="top">

512 Mi

</td>
<td valign="top">

2 Gi

</td>
</tr>
<tr>
<td valign="top">

CNI

</td>
<td valign="top">

100 m

</td>
<td valign="top">

500 m

</td>
<td valign="top">

512 Mi

</td>
<td valign="top">

1024 Mi

</td>
</tr>
</table>

**Default Autoscaling Configuration for Smaller Clusters**


<table>
<tr>
<th valign="top">

Component

</th>
<th valign="top">

minReplicas

</th>
<th valign="top">

maxReplicas

</th>
</tr>
<tr>
<td valign="top">

Ingress Gateway

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

Pilot

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
</tr>
</table>

**Default Autoscaling Configuration for Larger Clusters**


<table>
<tr>
<th valign="top">

Component

</th>
<th valign="top">

Minimum Number of Replicas

</th>
<th valign="top">

Maximum Number of Replicas

</th>
</tr>
<tr>
<td valign="top">

Ingress Gateway

</td>
<td valign="top">

3

</td>
<td valign="top">

10

</td>
</tr>
<tr>
<td valign="top">

Pilot

</td>
<td valign="top">

2

</td>
<td valign="top">

5

</td>
</tr>
</table>

