<!-- loiof70ddbf2bbf34e719bd2f0203310223f -->

# Issues when Creating APIRule CRs

This document offers solutions for common problems that may arise when creating an APIRule custom resource \(CR\) and outlines possible reasons why the CR might be in an error state after creation.

To check the state of an APIRule CR, run:

```
kubectl get apirules httpbin
```

If the CR is in the error state, you get a response similar to this one:

```
NAME      STATUS   HOST
httpbin   ERROR    httpbin.xxx.shoot.canary.k8s-hana.ondemand.com
```

The error may signify that your APIRule CR is in an inconsistent state and the service cannot be properly exposed. To check the error message of the APIRule CR, run:

```
kubectl get apirules -n {NAMESPACE} {APIRULE_NAME} -o=jsonpath='{.status.description}'

```



<a name="loiof70ddbf2bbf34e719bd2f0203310223f__section_et3_sy5_52c"/>

## The `issuer` Configuration of the `jwt` Access Strategy is Missing



### Symptom

You get the following error:

```
{"code":"ERROR","description":"Validation error: Attribute \".spec.rules[0].jwt\": supplied config cannot be empty"}

```



### Cause

Your APIRule is missing the `issuer` configuration for the `jwt` access strategy. See an example:

```
apiVersion: gateway.kyma-project.io/v2
kind: APIRule
metadata:
  ...
spec:
  ...
  rules:
    - path: /.*
      jwt:

```



### Solution

Add JWT configuration for the **issuer** or use the ```` symbols. Here’s an example of a valid configuration:

```
spec:
  ...
  rules:
    - path: /.*
      methods: ["GET"]
      jwt:
        authentications:
          - issuer: "https://dev.kyma.local"
            jwksUri: "https://example.com/.well-known/jwks.json"


```



<a name="loiof70ddbf2bbf34e719bd2f0203310223f__section_kpv_sbv_52c"/>

## Invalid `issuer` Configuration for the `jwt` Access Strategy



### Symptom

You get the following error and the APIRule CR is not created:

```
The APIRule "httpbin" is invalid: .spec.rules[0].jwt.authentications[0].issuer: value is empty or not a valid URI

```



### Cause

If the `issuer` contains a colon '`:`', it must be a valid URI. Here’s an example of the APIRule CR with an invalid `issuer` URL configuration:

```
apiVersion: gateway.kyma-project.io/v2
kind: APIRule
metadata:
  ...
spec:
  ...
  rules:
    - path: /.*
      jwt:
        authentications:
          - issuer: ://unsecured.or.not.valid.url
            jwksUri: https://example.com/.well-known/jwks.json


```



### Solution

The JWT **issuer** must not be empty and must be a valid URI, for example:

```
apiVersion: gateway.kyma-project.io/v2
kind: APIRule
metadata:
  ...
spec:
  ...
  rules:
    - path: /.*
      jwt:
        authentications:
          - issuer: https://dev.kyma.local
            jwksUri: https://dev.kyma.local/.well-known/jwks.json
```



<a name="loiof70ddbf2bbf34e719bd2f0203310223f__section_zxm_f3c_y2c"/>

## Both `noAuth` and `jwt` Access Strategies Defined on the Same Path



### Symptom

You get the following error:

```
{"code":"ERROR","description":"Validation error: Attribute \".spec.rules[0].noAuth\": noAuth access strategy is not allowed in combination with other access strategies"}
```



### Cause

You must not set the `noAuth` access strategy to *noAuth* and define the `jwt` configuration on the same path. See an example of APIRule CR with invalid configuration:

```
spec:
  ...
  rules:
    - path: /.*
      noAuth: true
      jwt:
        authentications:
          - issuer: https://dev.kyma.local
            jwksUri: https://dev.kyma.local/.well-known/jwks.json
```



### Solution

Decide on one configuration you want to use. You can either use `noAuth` access to the specific path or restrict it using a JWT security token.



<a name="loiof70ddbf2bbf34e719bd2f0203310223f__section_kzg_gkc_y2c"/>

## Occupied Host



### Symptom

You get the following error:

```
{"code":"ERROR","description":"Validation error: Attribute \".spec.host\": This host is occupied by another Virtual Service"}
```



### Cause

Your APIRule CR specifies a host that is already used by another APIRule or Virtual Service. See an example of two APIRule CRs that use the same host:

```
spec:
  host: httpbin.xxx.shoot.canary.k8s-hana.ondemand.com
```

```
spec:
  host: httpbin.xxx.shoot.canary.k8s-hana.ondemand.com
```



### Solution

Use a different host for one of the APIRule CRs. See an example:

```
spec:
  httpbin-new.xxx.shoot.canary.k8s-hana.ondemand.com
```

```
spec:
  host: httpbin.xxx.shoot.canary.k8s-hana.ondemand.com
```

