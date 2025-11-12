<!-- loiod3f20b6b01a34987a0ae3e6097d3c69a -->

# Configure Observability for the Istio Service Mesh

Learn how the Telemetry module collects logs, traces, and metrics from the Istio service mesh, and how you can configure each telemetry signal for your workloads.

The Istio service mesh generates detailed telemetry data, including access logs, traces, and metrics. The Telemetry module collects, processes, and exports this data, so you can analyze your mesh's traffic, performance, and behavior.

When you have both the Istio and Telemetry modules in your cluster, they integrate automatically. The Telemetry module's components are injected with an Istio sidecar, which adds them to the service mesh. This enables secure, mTLS-encrypted communication for all telemetry data by default. For details, see [Istio Integration](istio-integration-d31499b.md).

To monitor your service mesh, configure the Telemetry module to collect the specific signals you need:

-   To monitor traffic details like latency, traffic volume, and errors, configure Istio to send access logs \(see [Configure Istio Access Logs](configure-istio-access-logs-808c167.md) \).
-   To get an end-to-end view of requests, configure Istio to send trace data \(see [Configure Istio Tracing](configure-istio-tracing-3f504d8.md)\).
-   To monitor the health and performance of your service mesh, enable the `istio` input in the Telemetry module. This scrapes metrics directly from Istio proxies \(sidecars\) and the control plan \(see [Collect Istio Metrics](collect-istio-metrics-aa786e0.md)\).

