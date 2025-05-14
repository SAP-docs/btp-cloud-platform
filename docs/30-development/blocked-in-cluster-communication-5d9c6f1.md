<!-- loio5d9c6f147b42422cab9025fe61cbe3da -->

# Blocked In-Cluster Communication



<a name="loio5d9c6f147b42422cab9025fe61cbe3da__section_kgs_lyg_2fc"/>

## Symptom

After switching from APIRule custom resource \(CR\) `v1beta1` to version `v2`, in-cluster communication is blocked.



<a name="loio5d9c6f147b42422cab9025fe61cbe3da__section_szg_myg_2fc"/>

## Cause

By default, access to the workload from internal traffic is blocked if an APIRule CR in version `v2` or `v2alpha1` is applied. This approach aligns with Kyma’s “secure by default” principle.



<a name="loio5d9c6f147b42422cab9025fe61cbe3da__section_gzl_myg_2fc"/>

## Solution

If APIRule is applied, internal traffic is blocked by default. To allow it, you must create an ALLOW-type AuthorizationPolicy.

See the following example of an `AuthorizationPolicy` that allows internal traffic to the given workload. Note that it excludes traffic coming from `istio-ingressgateway` not to interfere with policies applied by APIRule to external traffic.

To use this code sample, replace `${NAMESPACE}`, `${KEY}`, and `${TARGET_WORKLOAD}` with the values appropriate for your environment.

```
apiVersion: security.istio.io/v1
kind: AuthorizationPolicy
metadata:
  name: allow-internal
  namespace: ${NAMESPACE}
spec:
  selector:
    matchLabels:
      ${KEY}: ${TARGET_WORKLOAD}
  action: ALLOW
  rules:
  - from:
    - source:
        notPrincipals: ["cluster.local/ns/istio-system/sa/istio-ingressgateway-service-account"]
```

