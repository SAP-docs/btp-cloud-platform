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

