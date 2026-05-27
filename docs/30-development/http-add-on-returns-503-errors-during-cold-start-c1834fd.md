<!-- loioc1834fdd767145d7b7085c2442804e55 -->

# HTTP Add-on Returns 503 Errors During Cold Start



<a name="loioc1834fdd767145d7b7085c2442804e55__section_symptom_rcc"/>

## Symptom

When your application is scaled to zero, and a new request arrives, the client receives a ***502*** or ***503*** error instead of a successful response.



<a name="loioc1834fdd767145d7b7085c2442804e55__section_cause_rcc"/>

## Cause

The HTTP Add-on `Interceptor` queues requests while the target `Deployment` has zero replicas. Once it detects at least one ready endpoint, it immediately forwards the queued request without retrying on failure. In an Istio mesh, this creates a race condition during cold start:

1.  The `Interceptor` receives the request and queues it.
2.  KEDA detects pending requests and scales the `Deployment` from 0 to 1.
3.  The `Pod` starts: container pull, init containers, readiness probes, Istio sidecar injection.
4.  The readiness probe passes, but the Istio sidecar or the application is not yet fully ready to handle traffic.
5.  The `Interceptor` sees a ready endpoint and forwards the queued request.
6.  The upstream returns ***503*** or refuses the connection.

Additionally, in some edge cases the `Istio Ingress Gateway` can return a ***502*** or ***503*** from the `Interceptor` if it is temporarily overloaded during scale-up.



<a name="loioc1834fdd767145d7b7085c2442804e55__section_solution_rcc"/>

## Solution

Configure an `EnvoyFilter` on the `Istio Ingress Gateway` to transparently retry failed requests during the cold-start window:

```
apiVersion: networking.istio.io/v1alpha3
kind: EnvoyFilter
metadata:
  name: my-app-keda-retry
  namespace: istio-system
spec:
  workloadSelector:
    labels:
      istio: ingressgateway
  configPatches:
  - applyTo: HTTP_ROUTE
    match:
      context: GATEWAY
      routeConfiguration:
        vhost:
          name: "my-app.example.com:443"
          route:
            name: ""
    patch:
      operation: MERGE
      value:
        route:
          retry_policy:
            retry_on: "5xx,connect-failure,reset,refused-stream"
            num_retries: 100
            per_try_timeout: 3s
```

> ### Note:  
> The `vhost.name` must match the actual virtual host name in Envoy's configuration. To find the correct name, run <code>istioctl proxy-config routes <i class="varname">&lt;ingressgateway-pod&gt;</i> -o json</code>. The format is typically `hostname:port` \(for example, `my-app.example.com:443`\), not `https://hostname`.

With this retry policy in place, failed attempts \(***502***, ***503***, connection refused\) are transparently retried. The client receives a successful response once the `Pod` is ready — up to 100 × 3s = 5 minutes of retries.

Also set `KEDA_HTTP_REQUEST_TIMEOUT` to *0* \(the default\) on the `Interceptor` `Deployment`. This makes the `Interceptor` wait indefinitely for the target to scale up, letting the `EnvoyFilter` retry policy handle all client-facing timeouts.

