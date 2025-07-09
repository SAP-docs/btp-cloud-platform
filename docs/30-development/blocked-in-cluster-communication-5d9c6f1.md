<!-- loio5d9c6f147b42422cab9025fe61cbe3da -->

# Blocked In-Cluster Communication



<a name="loio5d9c6f147b42422cab9025fe61cbe3da__section_kgs_lyg_2fc"/>

## Symptom

After switching from APIRule custom resource \(CR\) `v1beta1` to version `v2`, in-cluster communication is blocked. Attempts to connect internally to the workload result in the error ***RBAC: access denied***.



<a name="loio5d9c6f147b42422cab9025fe61cbe3da__section_szg_myg_2fc"/>

## Cause

By default, access to the workload from internal traffic is blocked if an APIRule CR in version `v2` or `v2alpha1` is applied. This approach aligns with Kyma’s “secure by default” principle.



<a name="loio5d9c6f147b42422cab9025fe61cbe3da__section_gzl_myg_2fc"/>

## Solution

If APIRule is applied, internal traffic is blocked by default. To allow it, you must create an ALLOW-type AuthorizationPolicy.

See the following example of an `AuthorizationPolicy` that allows internal traffic to the given workload. Note that it excludes traffic coming from `istio-ingressgateway` not to interfere with policies applied by APIRule to external traffic.

To use this code sample, replace `{NAMESPACE}`, `{LABEL_KEY}`, and `{LABEL_VALUE}` with the values appropriate for your environment.


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*\{NAMESPACE\}*

</td>
<td valign="top">

The namespace to which the AuthorizationPolicy applies. This namespace must include the target workload for which you allow internal traffic. The selector matches workloads in the same namespace as the AuthorizationPolicy.

</td>
</tr>
<tr>
<td valign="top">

*\{LABEL\_KEY\}: \{LABEL\_VALUE\}*

</td>
<td valign="top">

To further restrict the scope of the AuthorizationPolicy, specify label selectors that match the target workload. Replace these placeholders with the actual key and value of the label. The label indicates a specific set of Pods to which a policy should be applied. The scope of the label search is restricted to the configuration namespace in which the AuthorizationPolicy is present.

For more information, see [Authorization Policy](https://istio.io/latest/docs/reference/config/security/authorization-policy/).

</td>
</tr>
</table>

```
apiVersion: security.istio.io/v1
kind: AuthorizationPolicy
metadata:
  name: allow-internal
  namespace: {NAMESPACE}
spec:
  selector:
    matchLabels:
      {LABEL_KEY}: {LABEL_VALUE} 
  action: ALLOW
  rules:
  - from:
    - source:
        notPrincipals: ["cluster.local/ns/istio-system/sa/istio-ingressgateway-service-account"]
```

For example, let's suppose you have deployed the [HTTPBin Service](https://github.com/istio/istio/blob/master/samples/httpbin/httpbin.yaml) and exposed it using an APIRule `v2` or `v2alpha1`. To apply this policy to the HTTPBin Service labeled with `app: httpbin` deployed in the `default` namespace, you must set `{NAMESPACE}` to *default*, `{LABEL_KEY}` to *app*, and `{LABEL_VALUE}` to *httpbin*.

```
apiVersion: security.istio.io/v1
kind: AuthorizationPolicy
metadata:
  name: allow-internal
  namespace: default
spec:
  selector:
    matchLabels:
      app: httpbin
  action: ALLOW
  rules:
  - from:
    - source:
        notPrincipals: ["cluster.local/ns/istio-system/sa/istio-ingressgateway-service-account"]
```



<a name="loio5d9c6f147b42422cab9025fe61cbe3da__section_s5d_jvw_vfc"/>

## Verification

To test if the internal traffic reaches the exposed workload, follow the steps:

1.  Create a sample namespace with enabled Istio sidecar proxy injection:

    ```
    kubectl create ns curl-test
    kubectl label namespace curl-test istio-injection=enabled --overwrite
    ```

2.  Run a Pod inside the Istio service mesh:

    ```
    kubectl run -n curl-test --image=curlimages/curl test-internal -- /bin/sleep 3600
    ```

3.  To test the internal communication, replace the placeholders and run the following command:


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *\{SERVICE\_NAME\}*
    
    </td>
    <td valign="top">
    
    The name of the exposed Service.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *\{NAMESPACE\}*
    
    </td>
    <td valign="top">
    
    The namespace in which the Service is deployed.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *\{PORT\}*
    
    </td>
    <td valign="top">
    
    The port number on which the Service is listening for incoming traffic. Defined in the `port` field of the Service's configuration.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *\{EXPOSED\_PATH\}*
    
    </td>
    <td valign="top">
    
    A path exposed by the Service that you want to access.
    
    </td>
    </tr>
    </table>
    
    ```
    kubectl exec -ti -n curl-test test-internal -- curl http://{SERVICE_NAME}.{NAMESPACE}.svc.cluster.local:{PORT}/{EXPOSED_PATH}
    ```

    For example, to test the connection to the [HTTPBin Service](https://github.com/istio/istio/blob/master/samples/httpbin/httpbin.yaml) exposed using an APIRule `v2` or `v2alpha1` on the */get* path, you can use the following command:

    ```
    kubectl exec -ti -n curl-test test-internal -- curl http://httpbin.default.svc.cluster.local:8000/get
    ```

    If successful, the command returns the contents of the specified path.

4.  To clean up the resources created for testing, delete the namespace `curl-test` from the cluster. Deleting the namespace removes all resources within it.

    ```
    kubectl delete namespace curl-test
    ```


