<!-- loio038415880116407d89765d26b36653e3 -->

# Parallel Module Deployment



In some cases, it is crucial that modules and therefore applications are deployed in a predictable and consistent order. To ensure this, the module-level attribute `deployed-after` has been introduced. It contains a list of module names. If a module has this attribute, it will be deployed only after the modules specified in the attribute have already been deployed.

The relations described through this attribute are transitive, so if module A should be deployed after module B, and module B should be deployed after module C, then it means that module A should be deployed after module C.

> ### Sample Code:  
> MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> ID: com.sap.sample
> version: 0.1.0
> _schema-version: "3.2.0"
> parameters:
>   enable-parallel-deployments: true
>  
> modules:
>   - name: ui
>     type: javascript
>     deployed-after: [ backend, metrics ]
>  
>   - name: backend
>     type: java
>     deployed-after: [ hdi-content ]
>     requires:
>       - name: metrics
>         properties:
>           METRICS_URL: ~{url}
>     
>   - name: metrics
>     type: javascript
>     deployed-after: [ hdi-content ]
>     provides:
>       - name: metrics
>         properties:
>           METRICS_URL: ~{url}
>  
>   - name: hdi-content
>     type: hdi
> ```

In the example above, the `deployed-after` attributes guarantee that the `ui` module is deployed after the `backend` and the `metrics` modules, and they in turn are deployed after the `hdi-content` module. Note that the deployent order of the `backend` and the `metrics` modules is not specified in the attributes. This means that they can be deployed in any order.



<a name="loio038415880116407d89765d26b36653e3__parallel_deployment"/>

## Parallel Deployment

> ### Note:  
> The `deployed-after` parameter is supported from major schema version 3 onwards.

In the example above, we have also specified the top-level MTA parameter `enable-parallel-deployments` with value `true`. It activates the parallel deployment of MTA modules that do not have any deployment order dependencies between each other. If the parameter is missing or its value is `false`, the module deployment will be sequential.

> ### Note:  
> The `enable-parallel-deployments` parameter has influence only on modules deployment, see section [Sequential Resource Processing](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/b93db81b7df441d985896ac9eed65142.html) for the resources process.

> ### Note:  
> The `enable-parallel-deployments` parameter is supported from major schema version 3 onwards.



<a name="loio038415880116407d89765d26b36653e3__section_xc2_4ks_x5b"/>

## Circular Dependencies

Due to a modelling error, the user can introduce direct or transitive circular deployment order dependencies between modules. In such cases, this will be reported as a deployment error.



<a name="loio038415880116407d89765d26b36653e3__section_v55_qks_x5b"/>

## Compatibility with Previous Deployment Order

The previous deployment order algorithm was based on the `requires` module-level attribute, which contains a list of module names or provided dependencies from other modules. Since it is also the way to model configuration dependencies, this mechanism was not explicit enough to model a deployment order .

There are many applications that are still depending on the old deployment order algorithm. To support them until they adapt to the new modeling, the new deployment order is introduced in a backward compatible manner. This means that if there are no `deployed-after` module-level elements in the MTA descriptor and the top-level MTA parameter `enable-parallel-deployments` is set to `false` or is missing, the old ordering algorithm is enabled by default.

