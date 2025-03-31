<!-- loio19e332b59c084a928d4117b1f0d53d9b -->

# Expose Workloads Using the API Gateway Module

The API Gateway module introduces an APIRule custom resource \(CR\), which allows you to define the security configuration for an exposed endpoint using the concept of access strategies. The supported access strategies for APIRule v2 are noAuth and jwt.



<a name="loio19e332b59c084a928d4117b1f0d53d9b__section_twv_rjn_s2c"/>

## noAuth Configuration

The intended functionality of this access strategy is to provide a simple configuration for exposing workloads. It only allows access to the specified HTTP methods of the exposed workload.

See an example `noAuth` configuration:

> ### Sample Code:  
> ```
> ...
> rules:
>   - path: /headers
>     methods: ["GET"]
>     noAuth: true
> 
> ```



<a name="loio19e332b59c084a928d4117b1f0d53d9b__section_rt5_2kn_s2c"/>

## jwt Configuration

You can use this access strategy to define the Istio JWT configuration. Additionally, defining only one issuer is supported.

> ### Sample Code:  
> ```
> ...
> rules:
>   - path: /headers
>     methods: ["GET"]
>     jwt:
>       authentications:
>         - issuer: https://example.com
>           jwksUri: https://example.com/.well-known/jwks.json
>       authorizations:
>         - audiences: ["app1"]
> ```



### Authentications



### Authorizations

