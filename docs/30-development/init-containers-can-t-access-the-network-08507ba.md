<!-- loio08507ba3ef604993aef000ead96b5000 -->

# Init Containers Can’t Access the Network



<a name="loio08507ba3ef604993aef000ead96b5000__section_ahg_ckb_4gc"/>

## Symptom

Init containers can’t access the network.



<a name="loio08507ba3ef604993aef000ead96b5000__section_zkk_ckb_4gc"/>

## Cause

If Istio injection is enabled, the `istio-proxy` container intercepts all network traffic from all containers. By default, the Istio module 1.22 and later versions inject `istio-proxy` containers as native sidecars. However, you can also set the `sidecar.istio.io/nativeSidecar` annotation to *"false"* for a specific Pod. This annotation overwrites the default setting and indicates that instead of native sidecars, the annotated Pod must be injected with a regular sidecar container.

Init containers are started before regular containers. If `istio-proxy` is a regular sidecar, it doesn't work when init containers are running. As a result, init containers don't have network access.



<a name="loio08507ba3ef604993aef000ead96b5000__section_iml_ckb_4gc"/>

## Solution

Check whether `istio-proxy` is declared as `initContainer` or `container`.

-   If it is an `initContainer`, it means that `istio-proxy` already runs as a native sidecar. Since native sidecars do not cause networking problems with init containers, the root cause of the issue is not related to the type of containers used by Istio proxies.
-   If `istio-proxy` is declared as a regular container, switch to using a native sidecar instead. To do this, apply the annotation `sidecar.istio.io/nativeSidecar="true"` on the Pod or in the Pod template. See the following example:

    > ### Sample Code:  
    > ```
    > apiVersion: v1
    > kind: Pod
    > metadata:
    >   name: init-container-network-check
    >   namespace: test
    >   annotations:
    >     sidecar.istio.io/nativeSidecar: "true"
    > spec:
    >   initContainers:
    >   - name: init
    >     image: curlimages/curl
    >     command: [ "curl", "httpbin.org/get" ]
    >   containers:
    >   - name: main
    >     image: alpine:latest
    >     command: ["/bin/sleep", "10"]
    >   restartPolicy: Never
    > ```


When `istio-proxy` is a native sidecar, Istio injects it as the first init container, so all containers running later are able to access the network.

**Related Information**  


[Regular and Native Sidecar Containers](regular-and-native-sidecar-containers-b1e4cd0.md "Understand the differences between Istio proxies running as regular containers and as native sidecars, learn about the default settings applied by the Istio module, and find out how to override these settings for specific workloads as needed.")

