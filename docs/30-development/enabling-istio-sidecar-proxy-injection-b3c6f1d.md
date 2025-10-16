<!-- loiob3c6f1dfc75542dc913a08dc36e13893 -->

# Enabling Istio Sidecar Proxy Injection

To include your workloads into the Istio service mesh, enable the Istio sidecar proxy injection. You can do this for either an entire namespace or a single Deployment. Learn how to perform both these operations.

<a name="task_jwk_3cr_rcc"/>

<!-- task\_jwk\_3cr\_rcc -->

## Enabling Injection for a Namespace



<a name="task_jwk_3cr_rcc__prereq_dl3_m44_vcc"/>

## Prerequisites

-   You have the Istio module added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl).



<a name="task_jwk_3cr_rcc__context_lvn_4cr_rcc"/>

## Context

Enabling Istio sidecar proxy injection for a namespace allows istiod to watch all Pod creation operations in this namespace and automatically inject newly created Pods with an Istio sidecar proxy.

> ### Note:  
> A Pod is not injected with an Istio sidecar proxy if:
> 
> -   Istio sidecar proxy injection is disabled at the namespace level
> -   The `sidecar.istio.io/inject` label on the Pod is set to *false*
> -   The Pod's `spec` contains `hostNetwork: true`



<a name="task_jwk_3cr_rcc__steps-unordered_bxl_sdr_rcc"/>

## Procedure

You can either use Kyma dashboard, or kubectl.

-   Use Kyma dashboard.

    1.  Select the namespace where you want to enable Istio sidecar proxy injection.

    2.  Choose *Edit*.

    3.  In the *UI Form* section, switch the toggle to enable Istio sidecar proxy injection.

    4.  Choose *Save*.


-   Use kubectl.

    Replace the placeholder and run the command:

    ```
    kubectl label namespace <namespace-name> istio-injection=enabled
    ```




<a name="task_jwk_3cr_rcc__result_ldr_43f_scc"/>

## Results

You've enabled Istio sidecar proxy injection for the specified namespace. The namespace is labeled with `istio-injection: enabled`, which means that all Pods created in it from now on will have the Istio sidecar proxy injected.

<a name="task_ols_3cr_rcc"/>

<!-- task\_ols\_3cr\_rcc -->

## Enabling Injection for a Deployment



<a name="task_ols_3cr_rcc__prereq_nbl_xhb_tcc"/>

## Prerequisites

-   You have the Istio module added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   To use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl). Alternatively, you can use Kyma dashboard.



<a name="task_ols_3cr_rcc__context_cl1_scr_rcc"/>

## Context

Enabling Istio sidecar proxy injection for a Deployment injects an Istio sidecar proxy into all the Deployment's Pods.

> ### Note:  
> A Pod is not injected with an Istio sidecar proxy if:
> 
> -   Istio sidecar proxy injection is disabled at the namespace level
> -   The `sidecar.istio.io/inject` label on the Pod is set to *false*
> -   The Pod's `spec` contains `hostNetwork: true`



<a name="task_ols_3cr_rcc__steps-unordered_ebc_r4x_rcc"/>

## Procedure

-   Use Kyma dashboard.

    1.  Select the namespace of the Deployment for which you want to enable Istio sidecar proxy injection.

    2.  In the *Workloads* section, choose *Deployments*.

    3.  Choose the Deployment.

    4.  Choose *Edit*.

    5.  In the *UI Form* section, switch the toggle to enable Istio sidecar proxy injection.

    6.  Choose *Save*.


-   Use kubectl.

    Replace the placeholders and run the following command:

    ```
    kubectl patch -n <namespace-name> deployments/<deployment-name> -p '{"spec":{"template":{"metadata":{"labels":{"sidecar.istio.io/inject":"true"}}}}}'
    ```




<a name="task_ols_3cr_rcc__result_ass_p3f_scc"/>

## Results

You've enabled Istio sidecar proxy injection for the specified Deployment. The Deployment and all its Pods are labeled with `istio-injection: enabled`. All the Deployment's Pods are instantly injected with an Istio sidecar proxy.

