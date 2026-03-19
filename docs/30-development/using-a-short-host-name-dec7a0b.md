<!-- loiodec7a0b1573c474293d7e36412a4b9a8 -->

# Using a Short Host Name

Simplify your APIRule configuration by using a short host name instead of a fully qualified domain name \(FQDN\).



## What Is a Short Host Name?

A short host name is a single lowercase [RFC 1123](https://datatracker.ietf.org/doc/html/rfc1123) subdomain label without the domain suffix. For example, instead of specifying the FQDN `myapp.example.com` in APIRule, you use `myapp`. The domain `example.com` is automatically appended from the referenced Gateway resource.

Using a short host is especially useful when you move or recreate workloads in a new cluster. With a short host name, the APIRule does not hard-code the domain. Instead of updating every APIRule when the cluster’s domain changes, you only update the Gateway configuration once, and all APIRules that use short hosts start using the new domain automatically. This reduces the risk of mistakes and makes cluster migration easier.



## Gateway Requirements

The referenced Gateway must meet these requirements:

-   Define a single wildcard host across all [Server](https://istio.io/latest/docs/reference/config/networking/gateway/#Server) definitions.
-   Use the wildcard prefix `*.` \(for example, `*.example.com`\).



## Example

See an example Gateway resource:

```
apiVersion: networking.istio.io/v1beta1
kind: Gateway
metadata:
  name: kyma-gateway
  namespace: kyma-system
spec:
  selector:
    app: istio-ingressgateway
  servers:
  - hosts:
    - "*.example.com"
    port:
      name: https
      number: 443
      protocol: HTTPS
    tls:
      mode: SIMPLE
      credentialName: example-com-tls
```

The following APIRule uses a short host name and references the Gateway `kyma-gateway`:

```
apiVersion: gateway.kyma-project.io/v2
kind: APIRule
metadata:
  name: httpbin-short
  namespace: default
spec:
  hosts:
    - myapp
  service:
    name: httpbin
    port: 8000
  gateway: kyma-system/kyma-gateway
  rules:
    - path: /headers
      methods: ["GET"]
      noAuth: true
```

You can call your Service at `myapp.example.com` even though the domain suffix is not explicitly specified in the APIRule. The domain suffix is retrieved from the referenced Gateway.

