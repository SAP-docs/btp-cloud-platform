<!-- loio479a43e8c8f84b4ca8fe3436e1dd15ef -->

# Apply Third-Party Cookie Deprecation Trial Tokens for Kyma Runtime Workloads

Learn how to use EnvoyFilter or Istio VirtualService to add a third-party cookie deprecation token to an HTTP response for a particular workload exposed under the domain `ondemand.com`.



<a name="loio479a43e8c8f84b4ca8fe3436e1dd15ef__prereq_ksy_jdj_kbc"/>

## Prerequisites

-   You have the Istio module added.
-   You have a workload deployed.

<a name="task_mxj_wdj_kbc"/>

<!-- task\_mxj\_wdj\_kbc -->

## Add a Third-Party Cookie Deprecation Trial Token Using EnvoyFilter



<a name="task_mxj_wdj_kbc__context_ijp_b2j_kbc"/>

## Context

To modify the responses for a particular workload within the Istio service mesh, you can use EnvoyFilter with an additional HTTP filter added to the Envoy proxy configuration of the workload's sidecar. To do this, use the HTTP Lua filter.



<a name="task_mxj_wdj_kbc__steps_ix4_mfj_kbc"/>

## Procedure

1.  In the following EnvoyFilter's configuration, replace the placeholders.


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
    
    `<workload-tpcd-ef-name>`
    
    </td>
    <td valign="top">
    
    The name of your EnvoyFilter.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `<workload-namespace>`
    
    </td>
    <td valign="top">
    
    The namespace with the workload for which you apply the third-party cookie deprecation token.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `<workload-label-selector>`
    
    </td>
    <td valign="top">
    
    The label selector for the workload.
    
    </td>
    </tr>
    </table>
    
    ```
    apiVersion: networking.istio.io/v1alpha3
    kind: EnvoyFilter
    metadata:
      name: <workload-tpcd-ef-name>
      namespace: <workload-namespace>
    spec:
      workloadSelector:
        labels:
          <workload-label-selector>
      configPatches:
      - applyTo: HTTP_FILTER
        match:
          listener:
            filterChain:
              filter:
                name: "envoy.filters.network.http_connection_manager"
                subFilter:
                  name: "envoy.filters.http.router"
        patch:
          operation: INSERT_BEFORE
          value:
            name: envoy.lua
            typed_config:
              "@type": "type.googleapis.com/envoy.extensions.filters.http.lua.v3.Lua"
              inlineCode: |
                function envoy_on_response(response_handle)
                  response_handle:headers():add("Origin-Trial", "Avu6rn7emV5gK8gvyGHlX8TMqM9uo1FacP2j/RWTq+8j+yKnqcTO0TQh0bXJ/7QntxD4/JzXv8aXoqxxZQuqXgYAAABdeyJvcmlnaW4iOiJodHRwczovL29uZGVtYW5kLmNvbTo0NDMiLCJmZWF0dXJlIjoiVHBjZCIsImV4cGlyeSI6MTczNTM0Mzk5OSwiaXNTdWJkb21haW4iOnRydWV9")
                  response_handle:headers():add("Critical-Origin-Trial", "Tpcd")
                end
    ```

2.  Apply the EnvoyFilter configuration.

    Once the EnvoyFilter is applied, any request that includes the specified token will always have the necessary HTTP response headers added.




<a name="task_mxj_wdj_kbc__result_afh_5dn_kbc"/>

## Results

Responses from the workload endpoint include the specified HTTP headers. See an example response:

```
HTTP/2 200
server: istio-envoy
date: Thu, 11 Apr 2024 13:17:11 GMT
content-type: application/json
content-length: 599
access-control-allow-origin: *
access-control-allow-credentials: true
x-envoy-upstream-service-time: 3
origin-trial: Avu6rn7emV5gK8gvyGHlX8TMqM9uo1FacP2j/RWTq+8j+yKnqcTO0TQh0bXJ/7QntxD4/JzXv8aXoqxxZQuqXgYAAABdeyJvcmlnaW4iOiJodHRwczovL29uZGVtYW5kLmNvbTo0NDMiLCJmZWF0dXJlIjoiVHBjZCIsImV4cGlyeSI6MTczNTM0Mzk5OSwiaXNTdWJkb21haW4iOnRydWV9
critical-origin-trial: Tpcd

{
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.xxx.ondemand.com",
    "User-Agent": "curl/8.4.0",
    "X-Envoy-Attempt-Count": "1",
    "X-Envoy-Expected-Rq-Timeout-Ms": "180000",
    "X-Envoy-Internal": "true",
    "X-Forwarded-Client-Cert": "...",
    "X-Forwarded-Host": "httpbin.xxx.ondemand.com"
  }
}
```

<a name="task_etf_qdj_kbc"/>

<!-- task\_etf\_qdj\_kbc -->

## Add a Third-Party Cookie Deprecation Trial Token Using Istio VirtualService



<a name="task_etf_qdj_kbc__context_avs_jh4_kbc"/>

## Context

If you use Istio VirtualServices rather than APIRules to expose Kyma workloads, adapt your Istio VirtualService configuration to include the third-party cookie deprecation token in HTTP response headers.



<a name="task_etf_qdj_kbc__steps_lcd_kc4_kbc"/>

## Procedure

1.  In the following configuration of Istio VirtualService, replace the placeholders.


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
    
    `<workload-with-tpcd-trial-token>`
    
    </td>
    <td valign="top">
    
    The name of the workload for which you apply a third-party cookie depreation token.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `<workload-namespace>`
    
    </td>
    <td valign="top">
    
    The namespace of the workload.
    
    </td>
    </tr>
    </table>
    
    ```
    apiVersion: networking.istio.io/v1alpha3
    kind: VirtualService
    metadata:
      name: <workload-with-tpcd-trial-token>
      namespace: <workload-namespace>
    spec:
      gateways:
        - kyma-system/kyma-gateway
      hosts:
        - httpbin.xxx.ondemand.com
      http:
        - corsPolicy:
            allowHeaders:
              - Authorization
              - Content-Type
              - '*'
            allowMethods:
              - GET
              - POST
              - PUT
              - DELETE
              - PATCH
            allowOrigins:
              - regex: .*
          headers:
            request:
              set:
                x-forwarded-host: httpbin.xxx.ondemand.com
            response:
              set:
                origin-trial: <Avu6rn7emV5gK8gvyGHlX8TMqM9uo1FacP2j/RWTq+8j+yKnqcTO0TQh0bXJ/7QntxD4/JzXv8aXoqxxZQuqXgYAAABdeyJvcmlnaW4iOiJodHRwczovL29uZGVtYW5kLmNvbTo0NDMiLCJmZWF0dXJlIjoiVHBjZCIsImV4cGlyeSI6MTczNTM0Mzk5OSwiaXNTdWJkb21haW4iOnRydWV9>
                critical-origin-trial: Tpcd
          match:
            - method:
                regex: ^(GET)$
              uri:
                regex: /.*
          route:
            - destination:
                host: httpbin.<workload-namespace>.svc.cluster.local
                port:
                  number: 8000
              weight: 100
    ```

2.  Apply the Istio VirtualService configuration.

    Once the Istio VirtualService configuration is applied, any request that includes the specified token will always have the necessary HTTP response headers added.




<a name="task_etf_qdj_kbc__result_tqw_324_kbc"/>

## Results

Responses from the workload endpoint include the specified HTTP headers.

