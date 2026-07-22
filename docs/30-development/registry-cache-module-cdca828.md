<!-- loiocdca828ea4ef4fd6a08088e0ba19b66c -->

# Registry Cache Module

The Registry Cache module adds a caching layer for container image registries in SAP BTP, Kyma runtime instances.



<a name="loiocdca828ea4ef4fd6a08088e0ba19b66c__section_what_is_registry_cache"/>

## What Is Registry Cache?

The Registry Cache module adds a caching layer for container image registries in SAP BTP, Kyma runtime instances. It reduces outbound traffic to upstream registries, improving image pull performance. With Registry Cache, you can also cache images from private registries. To do so, provide credentials for the caching layer to use when authenticating against those registries.

The Registry Cache feature is built on top of the Gardener's registry cache extension. See [Configuring the Registry Cache Extension](https://gardener.cloud/docs/extensions/others/gardener-extension-registry-cache/registry-cache/configuration/).



<a name="loiocdca828ea4ef4fd6a08088e0ba19b66c__section_features"/>

## Features

The Registry Cache module provides the following features:

-   Caches container images from upstream registries to reduce outbound network traffic.
-   Supports private registries using credential Secrets referenced in `RegistryCacheConfig`.
-   Configurable cache volume size and storage class per upstream registry.
-   Configurable garbage collection Time to Live \(TTL\); you can disable garbage collection.
-   Proxy support for HTTP and HTTPS connections used by the cache.
-   TLS-enabled HTTP server for the Registry Cache endpoint.



<a name="loiocdca828ea4ef4fd6a08088e0ba19b66c__section_architecture"/>

## Architecture

The Registry Cache module consists of two main runtime components: the `RegistryCache` controller and the `RegistryCacheConfig` admission webhook. Both run in the same Registry Cache Manager process.

![Architecture diagram of the Registry Cache Manager process. The RegistryCache Reconciler communicates bidirectionally with the Webhook Server running on TLS port 9443. The Webhook Server hosts the RegistryCacheConfig Webhook for validation and triggers certificate renewal. On certificate renewal, the Webhook Server calls the Certificate Manager, which patches the ValidatingWebhookConfiguration CA bundle. The /healthz and /readyz endpoints delegate to webhook.StartedChecker().](images/Registry_Cache_Module_Architecture_78cd8ec.png)

-   `RegistryCache` controller — reconciles `RegistryCache` custom resources \(CRs\) and drives status transitions.
-   Webhook Server — TLS server on port 9443 that validates `RegistryCacheConfig` resources on create and update.
-   Certificate Manager — watches TLS certificate files and rotates the CA bundle in `ValidatingWebhookConfiguration` on renewal.



<a name="loiocdca828ea4ef4fd6a08088e0ba19b66c__section_api_crds"/>

## API / Custom Resource Definitions

The Registry Cache module defines the following custom resources:

**Custom Resource Definitions**


<table>
<tr>
<th valign="top">

CRD

</th>
<th valign="top">

Scope

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`RegistryCache`

</td>
<td valign="top">

Namespaced

</td>
<td valign="top">

Module CR managed by the lifecycle infrastructure. Tracks the installation health of the Registry Cache module.

See [RegistryCache Custom Resource](https://github.com/kyma-project/registry-cache/blob/main/docs/user/resources/RegistryCache.md).

</td>
</tr>
<tr>
<td valign="top">

`RegistryCacheConfig`

</td>
<td valign="top">

Namespaced

</td>
<td valign="top">

User-created CR that configures a caching layer for a specific upstream container image registry.

See [RegistryCacheConfig Custom Resource](https://github.com/kyma-project/registry-cache/blob/main/docs/user/resources/RegistryCacheConfig.md).

</td>
</tr>
</table>

