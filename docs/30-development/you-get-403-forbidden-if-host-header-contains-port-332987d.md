<!-- loio332987def0774a3595dfc9c0bb22640a -->

# You Get 403 Forbidden if Host Header Contains Port



<a name="loio332987def0774a3595dfc9c0bb22640a__section_symptom"/>

## Symptom

When you try to access a Kyma endpoint protected by an `AuthorizationPolicy` allowing a given hostname, it reports a ***403 Forbidden*** error.



<a name="loio332987def0774a3595dfc9c0bb22640a__section_cause"/>

## Cause

The error might be caused by the unnecessary port number in the `Host` header. Istio checks the host as-is, so if the `Host` header contains a port number and the `AuthorizationPolicy` defines only a hostname, the request is denied.

Example:

```
apiVersion: security.istio.io/v1
kind: AuthorizationPolicy
metadata:
  name: ingress-allow-headers
  namespace: istio-system
spec:
  action: ALLOW
  rules:
  - to:
    - operation:
        hosts: [ "httpbin.local.kyma.dev" ]
        methods: ["GET"]
        paths: ["/headers"]
  selector:
    matchLabels:
      app: istio-ingressgateway
```

```
curl -k -H "Host: httpbin.local.kyma.dev:443" https://httpbin.local.kyma.dev/headers
```

```
RBAC: access denied
```



<a name="loio332987def0774a3595dfc9c0bb22640a__section_solution"/>

## Solution

The [RFC 9110](https://datatracker.ietf.org/doc/html/rfc9110#section-4.2.3) and [RFC 3986](https://datatracker.ietf.org/doc/html/rfc3986#section-3.2.3) documents define that HTTP clients should remove the port if it is the default port for a given protocol. The general recommendation is to fix the client implementation.

If this solution cannot be implemented, the workaround is to modify the `AuthorizationPolicy` to also include the port number.

```
apiVersion: security.istio.io/v1
kind: AuthorizationPolicy
metadata:
  name: ingress-allow-headers
  namespace: istio-system
spec:
  action: ALLOW
  rules:
  - to:
    - operation:
        hosts: [ "httpbin.local.kyma.dev", "httpbin.local.kyma.dev:443" ]
        methods: ["GET"]
        paths: ["/headers"]
  selector:
    matchLabels:
      app: istio-ingressgateway
```

