<!-- loio53daaafe8f8345fc9b8497b86d17c9d9 -->

# Routes

Configure application routes using the MTA modeling.

The `routes` parameter defines the HTTP routes that are created \(if they don't already exist\) and bound to an application module during deployment. It accepts a list of one or more route entries and replaces the older `host`, `domain`, `port`, and `route-path` parameters. If both the `routes` parameter and the older parameters are present in a descriptor, the `routes` value takes precedence and the older parameters are ignored.

Each `route` entry in the list is a map of key-value pairs. The key `route` is required and specifies the Cloud Foundry route \(cf route\) to be created and bound to the application. The deployer reads the `route` entry in the same way as a Cloud Foundry app Manifest. It interprets everything up to the first dot `'.'` as the host, then everything between the first dot and the first forward slash `'/'` as the domain, and the rest \(if present\) as the path. Multiple optional keys are supported, including `apply-namespace` and `no-hostname`.

The host and domain parts of a route must meet the following requirements:


<table>
<tr>
<th valign="top">

Part

</th>
<th valign="top">

Maximum Length

</th>
<th valign="top">

Allowed Characters

</th>
<th valign="top">

General Requirements

</th>
</tr>
<tr>
<td valign="top">

Host

</td>
<td valign="top">

63 characters

</td>
<td valign="top">

Lowercase letters \(a–z\), digits \(0–9\), and hyphens \(-\)

</td>
<td valign="top" rowspan="2">

Must both start and end with a letter or a digit

</td>
</tr>
<tr>
<td valign="top">

Domain

</td>
<td valign="top">

253 characters

</td>
<td valign="top">

Lowercase letters \(a–z\), digits \(0–9\), hyphens \(-\), and dots \(.\)

</td>
</tr>
</table>

If you do not define the route using the `routes` parameter or the `host` and `domain` parameters, a placeholder `default-uri` is automatically applied. This placeholder is resolved to `${default-host}.${default-domain}`. The `default-host`, as part of the URI, is resolved to `${org}-${space}-<module_name>`.

> ### Note:  
> Concatenating the org, space, and module names can exceed the 63-character DNS host label limit and cause deployment failures. For this reason, we recommend that you explicitly set the `routes` parameter instead of using the automatically set default route.

For more information about `default-` parameters, see [Module-Specific Parameters](modules-177d34d.md#loio177d34d45e3d4fd99f4eeeffc5814cf1__section_moduleSpecificParameters).

If you want to create a route with a wildcard host name, use an asterisk in quotes \("\*"\).

```
modules:
- name: my-app
  type: application
  parameters:
    routes:
      - route: "*foo.my.custom.domain/path"
      - route: "foo.my.custom.domain/path"
      - route: "foo.${default-domain}/path"

```

To reference a specific route inside the deployment descriptor \(for example for a `provides` section\), use the following syntax. The index 0 retrieves the first route in the list:

> ### Example:  
> ```
> provides:
>   - name: foo
>     properties:
>       url: "${protocol}://${routes/0/route}"
> 
> ```



## Deploy applications to a route without a host name

To bind an app to a route without a host name, you can use the `routes` and `no-hostname` parameters. Such a route is a subdomain of an existing domain with no host attached at the front. Note that `no-hostname` is a boolean parameter, and must follow every route definition. For example, if you have two or more routes without host names in your MTA, then you need to add that parameter under each of those routes. If for a given route the `no-hostname` parameter is missing, its value defaults to `false`.

> ### Sample Code:  
> ```
> routes:
>         - route: host1.some-domain.com
>         - route: host2.some-domain.com
>           no-hostname: false
>         - route: subdomain.some-domain.com
>           no-hostname: true
> ```

In the example above, `no-hostname: false` has no effect on the second route, since that is the default value, while `host2` is registered as a host to the route. The `no-hostname: true` parameter, however conveys to the deployer that `subdomain` is not a separate host, and the whole route is used as a Cloud Foundry domain \(subdomain of `some-domain.com`, if present\).

> ### Caution:  
> The MTA deployer attempts to create the subdomain if it does not exist, but cannot resolve any specific corner cases about subdomain/domain ownership permissions. If the subdomain has already been created, the deployer maps the application to it.



<a name="loio53daaafe8f8345fc9b8497b86d17c9d9__section_dxq_1y3_pzb"/>

## Deploy applications to http2 routes

If you want to enable http2 routing traffic to MTA modules \(applications\) you can use the `protocol: http2` parameter on route level.

Note that the protocol value must be `http1` or `http2` and must be included in every route in order for it to take effect. If the `protocol` parameter is not specified, the value will be set to `http1` by default.

> ### Sample Code:  
> ```
> routes:
>   - route: http1-route.some-domain.com
>   - route: http1- route.some-domain.com
>     protocol: http1 # The default value if not provided
>   - route: http2- route.some-domain.com
>     protocol: http2
> ```



<a name="loio53daaafe8f8345fc9b8497b86d17c9d9__section_mpm_dwl_xcc"/>

## Deploy applications to a route with a namespace

To bind an application to a route with a namespace, use the `routes` and `apply-namespace` parameters. When the value of the `apply-namespace` parameter is set to `true`, a prefix with the namespace value will be added to the route.

> ### Sample Code:  
> ```
> routes:
>         - route: host1.some-domain.com
>           apply-namespace: true
>         - route: host2.some-domain.com
>           apply-namespace: false
> ```

If you don't explicitly set the `apply-namespace` parameter for a specific route, its value will be determined by the application's `apply-namespace` parameter. This means that if the application has a namespace defined, that namespace will also be applied to the bound route. Conversely, if the application does not have a namespace, the route will not have one either.

For more information, see [Fine-Grained Configuration](namespaces-b28fd77.md#loiob28fd77836d44bde8c404618bf0f1228__section_hmf_khn_xcc).



## Route validation and automatic correction

When a route defined in the MTA deployment descriptor contains characters that are not allowed, or exceeds the allowed length, SAP Cloud Deployment service attempts to automatically correct it before deployment:

-   Uppercase letters are converted to lowercase.
-   Disallowed characters \(for example, underscores, `@` signs, or spaces\) are replaced with a hyphen \(-\).
-   Leading and trailing hyphens are removed.
-   Parts that exceed the maximum length are shortened to fit.

> ### Note:  
> These corrections are applied silently. Your application may be assigned a route that differs from the one you specified in the descriptor. If the exact route matters, define a route that already meets the requirements above.

The deployment fails in the following cases:

-   The route cannot be corrected into a valid route — for example, when a host or domain contains no usable characters after normalization. The deployment fails with a similar error:`Could not create a valid host from "…"`, `Could not create a valid domain from "…"`, or `Could not create a valid route from "…"`.
-   The `routes` parameter is malformed — for example, it is not a valid list of route entries or contains an unsupported attribute. The deployment fails with a similar error: `Cannot parse 'routes' - check documentation for correct format.`
-   Cloud Foundry rejects the corrected route — for example, because the domain does not exist or the route conflicts with an existing one. The deployment fails with the corresponding Cloud Foundry level.

> ### Note:  
> -   Automatic route correction cannot be disabled. To ensure a route is used exactly as written, define it so that it already meets the host and domain requirements. A route that is already valid is left unchanged.
> 
> -   To detect unintended corrections, compare the routes in your descriptor with the resolved routes reported in the deployment output.

