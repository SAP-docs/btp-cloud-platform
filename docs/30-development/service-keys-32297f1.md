<!-- loio32297f15898f47329df76b706447fc3e -->

# Service Keys



The consumption of existing service keys from applications is an alternative of service bindings. The application can use the service key credentials and consume the service.



<a name="loio32297f15898f47329df76b706447fc3e__section_q25_3ng_1fb"/>

## Creation and Update of Service Keys

A `service-keys` parameter can be created or updated when a service instance is being created or updated. It has to be defined under the resources that represent services which support service keys.

> ### Sample Code:  
> ```
> resources:
> - name: my-service-instance
>   type: org.cloudfoundry.managed-service
>   parameters:
>     service-keys: # Specifies the service keys that should be created for the respective service instance. Optional parameter.
>     - name: tool-access-key # Specified the service key name. Mandatory element.
>       config: # Specified the service key configuration. All entries under this map element are used for the service key creation request. Optional element.
>         permissions: read-write
>     - name: reader-endpoint
>       config:
>         permissions: read-only
> ```

As shown in the example above, every service key entry under the `service-keys` parameter supports optional configuration parameters that can be defined under the `config` parameter.



<a name="loio32297f15898f47329df76b706447fc3e__consumption-of-service-keys"/>

## Consumption of Service Keys

To be consumed, the existing service keys are modeled as a resource of type `org.cloudfoundry.existing-service-key`. MTA modules might be set to depend on these resources by using a configuration in the `requires` section, which results in an injection of the service key credentials in the application environment.

> ### Sample Code:  
> ```
> modules:
>   - name: app123
>     type: javascript.nodejs
>     requires:
>       - name: service-key-1
>         parameters:
>           env-var-name: keycredentials
> ...
> resources:
>   - name: service-key-1
>     type: org.cloudfoundry.existing-service-key
>     parameters:
>       service-name: service-a
>       service-key-name: test-key-1
> ```

As a result, the application `app123` has the environment variable `keycredentials`, with value the credentials of the existing service key `test-key-1` of service `service-a`.

> ### Note:  
> Note that only the parameter `service-name` is mandatory. It defines which service is used by the application.
> 
> The following parameters are optional:
> 
> -   `service-key-name`- resource parameter, which defines which service key of the defined service is used. The default value is the name of the resource.
> 
> -   `env-var-name` - required dependency parameter, which defines what is the name of the new environment variable of the application. The default value is the service key name.



<a name="loio32297f15898f47329df76b706447fc3e__section_cvh_3hj_wxb"/>

## Automatic Service Key Renewal

It’s a common use case to want an automatic service key renewal \(e.g. if you want to rotate generated service credentials or certificates\).

Service key renewal on MTA redeployment is supported by using changed key names. You can do this either by manually changing the service key name in the descriptor or by using a dynamic parameter as part of it - `${timestamp}`. This parameter will always resolve to the current timestamp at the time of deployment. This means that the key will have a different name on each subsequent deployment. This ensures that it will be considered as new and created. Afterwards the old key will be deleted. This functionality applies to service keys modelled under a resource using the `service-keys:` parameter. Example descriptor for automated key renewal/rotation:

> ### Sample Code:  
> ```
> ...
> resources:
>   - name: my-service
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service-plan: plan
>       service: offering
>       service-keys:
>         - name: my-rotating-key-${timestamp}
> ...
> ```

To consume a service key with a changing name in an application environment, make sure to use the parameter `env-var-name` when defining the service key `requires` section in the consuming module. This will ensure that the service key details are persisted under a static alias in the application environment. e.g.

> ### Sample Code:  
> ```
> modules:
> - name: my-app
> ...
>   requires:
>     - name: rotating-key
>       parameters:
>         env-var-name: *keycredentials*
> ...
> resources:
>   - name: my-service
>     type: org.cloudfoundry.managed-service
>     parameters:
>       service-keys:
>         - name: rotating-key-${timestamp}
>   - name: rotating-key
>     type: org.cloudfoundry.existing-service-key
>     parameters:
>       service-name: my-service
>       service-key-name: rotating-key-${timestamp}
> ```

