<!-- loio08507ba3ef604993aef000ead96b5000 -->

# Init Containers Can’t Access the Network



<a name="loio08507ba3ef604993aef000ead96b5000__section_ahg_ckb_4gc"/>

## Symptom

Init containers can’t access the network.



<a name="loio08507ba3ef604993aef000ead96b5000__section_zkk_ckb_4gc"/>

## Cause

If Istio injection is enabled, the `istio-proxy` container intercepts all network traffic from all containers. Init containers are started before regular containers. This means that `istio-proxy` running as a regular sidecar doesn’t work when init containers are running. As a result, init containers don’t have network access.



<a name="loio08507ba3ef604993aef000ead96b5000__section_iml_ckb_4gc"/>

## Solution

Inject `istio-proxy` as a native sidecar container.

To do this, set the `sidecar.istio.io/nativeSidecar` annotation in the Pod to `"true"`.

See the following example:

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

This annotation instructs Istio to run `istio-proxy` as a native sidecar container. In this case, Istio injects `istio-proxy` as the first init container, so all containers running later are able to access the network.

**Related Information**  


[Istio Proxy as Native Sidecar Container](https://kyma-project.io/#/istio/user/00--istio-proxy-as-native-sidecar)

