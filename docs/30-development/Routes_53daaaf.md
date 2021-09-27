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
> -   if you do not define the route using the `routes` parameter or the `host` and `domain` parameters, a placeholder `default-uri` is automatically applied. This placeholder is resolved to `${default-host}.${default-domain}`. The `default-host`, as part of the URI, is resolved to `${org}-${space}-<module_name>`. See [Modules](Modules_177d34d.md), table *MTA Development and Deployment Module Parameters* for more information about `default-` parameters.
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



## Deploy applications to hostless domains

If you want an app to be to bound to a route that is a subdomain of an existing domain without having an attached host, you have to use the `routes` parameter in combination with `no-hostname`. Note that `no-hostname` is a boolean parameter, and must be included with every route it affects. For example, if you have 2 or more hostless routes in your MTA then you need to add that parameter under each of those routes. If the parameter is not present for a given route, the value for it defaults to `false`.

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

