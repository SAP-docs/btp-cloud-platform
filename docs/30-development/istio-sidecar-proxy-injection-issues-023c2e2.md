<!-- loio023c2e253b4341afb431e14274ac3744 -->

# Istio Sidecar Proxy Injection Issues



<a name="loio023c2e253b4341afb431e14274ac3744__section_nmr_mwg_vcc"/>

## Symptom

Some Pods don't have an Istio sidecar proxy injected.



<a name="loio023c2e253b4341afb431e14274ac3744__section_o3x_nwg_vcc"/>

## Cause

By default, the Istio module does not automatically inject an Istio sidecar proxy into any Pods you create. To inject a Pod with an Istio sidecar proxy, you must explicitly enable injection for the Pod's Deployment or for the entire namespace. If you have done this and the sidecar is still not installed, follow the remedy steps to identify which settings are preventing the injection.

A Pod is not injected with an Istio sidecar proxy if:

-   Istio sidecar proxy injection is disabled at the namespace level
-   The `sidecar.istio.io/inject` label on the Pod is set to *false*
-   The Pod's `spec` contains `hostNetwork: true`



<a name="loio023c2e253b4341afb431e14274ac3744__section_hsc_1dg_xcc"/>

## Solution

Find out which Pods do not have Istio sidecar proxy injection enabled and why. You can either inspect Pods across all namespaces, focus on a specific namespace, or verify why a selective Pod is not injected.



### Check Pods in All Namespaces

1.  Download the [script](https://github.com/kyma-project/istio/blob/main/docs/assets/sidecar-analysis.sh).
2.  Run the script.

    ```
    ./sidecar-analysis.sh
    ```

    You get an output similar to this one:

    ```
    See all Pods that are not part of the Istio service mesh:
      Pods in namespaces labeled with "istio-injection=disabled":
        - namespace/Pod
        ...
      Pods labeled with "sidecar.istio.io/inject=false" in namespaces labeled with "istio-injection=enabled":
        - namespace/Pod
        ...
      Pods not labeled with "sidecar.istio.io/inject=true" in unlabeled namespaces:
        - namespace/Pod
        ...
       
    ```

3.  To learn how to include a Pod into the Istio service mesh, see [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).



### Check Pods in a Selective Namespace

1.  Download the [script](https://github.com/kyma-project/istio/blob/main/docs/assets/sidecar-analysis.sh).
2.  Run the script passing the namespace name as a parameter.

    ```
    ./sidecar-analysis.sh {YOUR_NAMEPSACE}
    ```

    You get an output similar to this one:

    ```
    In the namespace default, the following Pods are not part of the Istio service mesh:
      - Pod
      - Pod
      ...
    Reason: The namespace default has Istio sidecar proxy injection disabled, so none of its Pods have been injected with an Istio sidecar proxy.
    ```

3.  To learn how to include a Pod into the Istio service mesh, see [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).



### Check a Selective Pod

-   Use Kyma dashboard.
    1.  Go to the Pod's namespace.
    2.  Check if Istio sidecar proxy injection is enabled at the namespace level.

        Verify if the `Labels` section contains `istio-injection=disabled` or `istio-injection=enabled`. If Istio sidecar proxy injection is disabled at the namespace level, none of its Pods are injected with an Istio sidecar proxy.

    3.  Check if Istio sidecar proxy injection is enabled for the Pod's Deployment.

        In the **Workloads** section, select **Deployments** and choose *Edit*. In the `UI Form` section, check if the `Enable Sidecar Injection` toggle is switched.

    4.  Check if the label `sidecar.istio.io/inject: false` is set on a Pod.

        In the **Workloads** section, select **Pods**. Search for `sidecar.istio.io/inject: false`. If your Pod is displayed on the list, it has the label set.

    5.  To learn how to include a Pod into the Istio service mesh, see [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

-   Use kubectl.
    1.  Check if Istio sidecar proxy injection is enabled at the namespace level.

        Run the command:

        ```
        kubectl get namespaces {POD_NAMESPACE} -o jsonpath='{ .metadata.labels.istio-injection }'
        ```

    2.  Check if Istio sidecar proxy injection is enabled for the Pod's Deployment.

        Run the command:

        ```
        kubectl get deployments {POD_DEPLOYMENT} -n {NAMESPACE} -o jsonpath='{ .spec.template.metadata.labels }'
        ```

    3.  Check if the label `sidecar.istio.io/inject: false` is set on a Pod.

        ```
         kubectl get pod {POD} -n default -o=jsonpath='{.metadata.labels.sidecar\.istio\.io/inject}
        ```

    4.  To learn how to include a Pod into the Istio service mesh, see [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).


