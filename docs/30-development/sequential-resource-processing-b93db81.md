<!-- loiob93db81b7df441d985896ac9eed65142 -->

# Sequential Resource Processing

In various cases, some resources depend on other resources to already exist in order to process. Whenever an order of resource processing is necessary, the `processed-after` attribute can be utilized.

This attribute contains a list of resource names. It creates a sequence of services, an order, in which the services should be processed. If a resource has this attribute, it will be processed after the other resources in a higher position are processed.

> ### Note:  
> If the parameter `processed-after` is not specified, the resources are processed in parallel.

> ### Note:  
> The `processed-after` parameter is supported from schema version 3 onwards. If you attempt to use `processed-after` with schema version lower than 3, the deployment will ignore the attribute.

**Example**: Service A requires service B and service C to be processed first. On the other hand, both service B and service C require service D to be processed first. Service D does not require any other service to be proccessed. So the sequence for processing is - D → B, C → A.

> ### Sample Code:  
> ```
> MTA Deployment Descriptor (mtad.yaml) 
> 
>  
> 
> _schema-version: 3 
> 
> ID: multiple-anatz 
> 
> version: 3.0.0 
> 
>  
> 
> modules: 
> 
>   - name: multiple-anatz 
> 
>     type: staticfile 
> 
> resources: 
> 
>   - name: serviceA 
> 
>     type: org.cloudfoundry.managed-service 
> 
>     parameters: 
> 
>       service: application-logs 
> 
>       service-plan: lite 
> 
>     processed-after: [ serviceB, serviceC ] 
> 
>  
> 
>   - name: serviceB 
> 
>     type: org.cloudfoundry.managed-service 
> 
>     parameters: 
> 
>       service: application-logs 
> 
>       service-plan: lite 
> 
>     processed-after: [ serviceD ] 
> 
>  
> 
>   - name: serviceC 
> 
>     type: org.cloudfoundry.managed-service 
> 
>     parameters: 
> 
>       service: application-logs 
> 
>       service-plan: lite 
> 
>     processed-after: [ serviceD ]         
> 
>  
> 
>   - name: serviceD 
> 
>     type: org.cloudfoundry.managed-service 
> 
>     parameters: 
> 
>       service: application-logs    
> 
>       service-plan: lite 
> ```

In the example, the `processed-after` attribute ensures that serviceD is processed first, then serviceC and serviceB are processed in parallel, and finally serviceA is processed.



<a name="loiob93db81b7df441d985896ac9eed65142__section_rfr_vb2_hsb"/>

## Circular Dependencies

Due to a modelling error, you can create direct or transitive circular deployment order dependencies between resources. In such cases, it is reported as a deployment error.

