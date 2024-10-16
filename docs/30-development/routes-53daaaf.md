<!-- loio53daaafe8f8345fc9b8497b86d17c9d9 -->

# Routes

This section describes how developers or administrators have to configure application routes using the MTA modelling.

Routes are defined on module level by using the `routes` parameter. The parameter accepts list of one or many HTTP routes. It is a combination of the old parameters `host`, `domain`, `port` and `route-path`, which encompasses the full addresses to which to bind a module.

In case the new routes parameter and the old ones are available, the `routes` value is used and the values of the old parameters are ignored. Each route for the application is created if it does not already exist.

> ### Note:  
> -   The `routes` parameter is a list of entries, where every entry is a map of key-value pairs describing a route. Key `route` is required - this is the Cloud Foundry route \(cf route\) to be created and bound to the application. Multiple optional keys are supported, including `apply-namespace` and `no-hostname`.
> -   The deployer reads the `route` entry in a way consistent with cf App Manifest files. It interprets all included data up to the first full-stop `'.'` as the host, then everything up the forward-slash `'/'` as the domain, and the rest \(if present\) as the path.

> ### Remember:  
> Note the following:
> 
> -   if you do not define the route using the `routes` parameter or the `host` and `domain` parameters, a placeholder `default-uri` is automatically applied. This placeholder is resolved to `${default-host}.${default-domain}`. The `default-host`, as part of the URI, is resolved to `${org}-${space}-<module_name>`. For more information about `default-` parameters, see [Module-Specific Parameters](modules-177d34d.md#loio177d34d45e3d4fd99f4eeeffc5814cf1__section_moduleSpecificParameters).
> -   We recommend that you explicitly set the `routes` parameter instead of using the automatically set default route.

> ### Example:  
> In order to reference a specific given route inside a deployment descriptor \(for example for a `provides` section\), use the following syntax, which provides the first given route:
> 
> ```
> provides:
>   - name: foo
>     properties:
>       url: "${protocol}://${routes/0/route}"
> 
> ```

If you want to create a route with a wildcard hostname, use an asterisk in quotes \("\*"\).

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



## Deploy applications to a route without a host name

To bind an app to a route without a host name you can use the `routes` and `no-hostname` parameters. Such a route is a subdomain of an existing domain with no host attached at the front. Note that `no-hostname` is a boolean parameter, and must follow every route definition. For example, if you have 2 or more routes without host names in your MTA then you need to add that parameter under each of those routes. If for a given route the `no-hostname` parameter is missing, its value defaults to `false`.

> ### Sample Code:  
> ```
> routes:
>         - route: host1.some-domain.com
>         - route: host2.some-domain.com
>           no-hostname: false
>         - route: subdomain.some-domain.com
>           no-hostname: true
> ```

In the example above, `no-hostname: false` has no effect on the second route, since that is the default value, while `host2` is registered as a host to the route. The `no-hostname: true` parameter, however conveys to the deployer that `subdomain` is not a separate host, and the whole route is used as a Cloud Foundry domain - subdomain of `some-domain.com`, if present.

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

For more information, see [Fine-Grained Configuration](experimental-namespaces-b28fd77.md#loiob28fd77836d44bde8c404618bf0f1228__section_hmf_khn_xcc).

