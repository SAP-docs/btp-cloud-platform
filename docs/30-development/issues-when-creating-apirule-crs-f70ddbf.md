<!-- loiof70ddbf2bbf34e719bd2f0203310223f -->

# Issues when Creating APIRule CRs



<a name="loiof70ddbf2bbf34e719bd2f0203310223f__section_gbh_sy5_52c"/>

## Symptom

When you create an APIRule custom resource \(CR\), an instant validation error appears, or the APIRule CR has the `ERROR` status, for example:

```
kubectl get apirules httpbin

NAME      STATUS   HOST
httpbin   ERROR    httpbin.xxx.shoot.canary.k8s-hana.ondemand.com

```

The error may signify that your APIRule CR is in an inconsistent state and the service cannot be properly exposed. To check the error message of the APIRule CR, run:

```
kubectl get apirules -n {NAMESPACE} {APIRULE_NAME} -o=jsonpath='{.status.description}'

```

See what might be causing the issue and how to resolve it.



<a name="loiof70ddbf2bbf34e719bd2f0203310223f__section_et3_sy5_52c"/>

## The `issuer` Configuration of the jwt Access Strategy is Missing



### Cause

The following APIRule is missing the **issuer** configuration for the **jwt** access strategy:

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

If your APIRule is missing the **issuer** configuration for the **jwt** access strategy, the following error appears:

```
{"code":"ERROR","description":"Validation error: Attribute \".spec.rules[0].jwt\": supplied config cannot be empty"}

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



### Cause

If the `issuer` contains`:`, it must be a valid URI. Otherwise, you get the following error, and the APIRule CR is not created:

```
The APIRule "httpbin" is invalid: .spec.rules[0].jwt.authentications[0].issuer: value is empty or not a valid URI

```

Here’s an example of the APIRule CR with an invalid **issuer** URL configuration:

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

