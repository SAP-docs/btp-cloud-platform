<!-- loio9c7092c7b7ae4d49bc8ae35fdd0e0b18 -->

# Cloud Foundry Environment

The Cloud Foundry environment allows you to create polyglot cloud applications in Cloud Foundry. It contains the SAP BTP, Cloud Foundry runtime service, which is based on the open-source application platform managed by the Cloud Foundry Foundation.

The Cloud Foundry environment enables you to develop new business applications and business services, supporting multiple runtimes, programming languages, libraries, and services. You can leverage a multitude of buildpacks, including community innovations and self-developed buildpacks. It also integrates with SAP HANA extended application services, advanced model.



For more information about Cloud Foundry, see the official Cloud Foundry documentation at [https://docs.cloudfoundry.org/](https://docs.cloudfoundry.org/).

**Related Information**  


[Getting Started in the Cloud Foundry Environment](../20-getting-started/getting-started-in-the-cloud-foundry-environment-b328cc8.md "Get onboarded in the Cloud Foundry environment of SAP BTP. Follow the workflows for trial or customer accounts or subscribe to business applications.")

[Development in the Cloud Foundry Environment](../30-development/development-in-the-cloud-foundry-environment-40a8f8f.md "Learn more about developing applications on the SAP BTP, Cloud Foundry environment.")

[Administration and Operations in the Cloud Foundry Environment](../50-administration-and-ops/administration-and-operations-in-the-cloud-foundry-environment-a6b3b81.md "Learn about the different account administration and application operation tasks which you can perform in the Cloud Foundry environment.")

<a name="loiof8a351c8d81544a2942c911dccaba3c7"/>

<!-- loiof8a351c8d81544a2942c911dccaba3c7 -->

## Supported and Unsupported Cloud Foundry Features

Find out which Cloud Foundry features the Cloud Foundry environment on SAP BTP supports and doesn't support.




<table>
<tr>
<th valign="top">

Supported Features

</th>
<th valign="top">

Unsupported Features

</th>
</tr>
<tr>
<td valign="top">

-   Diego runtime. See [https://docs.cloudfoundry.org/concepts/diego/diego-architecture.html](https://docs.cloudfoundry.org/concepts/diego/diego-architecture.html).

-   SSH. See [https://docs.cloudfoundry.org/devguide/deploy-apps/app-ssh-overview.html](https://docs.cloudfoundry.org/devguide/deploy-apps/app-ssh-overview.html).
-   Custom Domains. See [https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html\#domains](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#domains).
-   Docker. See [https://docs.cloudfoundry.org/adminguide/docker.html](https://docs.cloudfoundry.org/adminguide/docker.html).
-   Running Tasks. See [https://docs.cloudfoundry.org/devguide/using-tasks.html](https://docs.cloudfoundry.org/devguide/using-tasks.html).
-   Request Tracing

    -   Zipkin Tracing. See [https://docs.cloudfoundry.org/adminguide/zipkin\_tracing.html](https://docs.cloudfoundry.org/adminguide/zipkin_tracing.html).


-   Websockets. See [https://docs.cloudfoundry.org/adminguide/supporting-websockets.html](https://docs.cloudfoundry.org/adminguide/supporting-websockets.html).
-   Space-Scoped Service Brokers. See [https://docs.cloudfoundry.org/services/managing-service-brokers.html](https://docs.cloudfoundry.org/services/managing-service-brokers.html).
-   Route Services \(only user-provided and fully-brokered services\). See [https://docs.cloudfoundry.org/services/route-services.html](https://docs.cloudfoundry.org/services/route-services.html).
-   Sharing Service Instances \(not all services support instance sharing\). See [https://docs.cloudfoundry.org/devguide/services/sharing-instances.html](https://docs.cloudfoundry.org/devguide/services/sharing-instances.html).
-   HTTP/2. See [https://docs.cloudfoundry.org/adminguide/supporting-http2.html\#application](https://docs.cloudfoundry.org/adminguide/supporting-http2.html#application).
-   Streaming Logs to Log Management Services. See [https://docs.cloudfoundry.org/devguide/services/log-management.html](https://docs.cloudfoundry.org/devguide/services/log-management.html).



</td>
<td valign="top">

-   Container-to-Container Networking. See [https://docs.cloudfoundry.org/concepts/understand-cf-networking.html](https://docs.cloudfoundry.org/concepts/understand-cf-networking.html) .

-   Isolation Segments. See [https://docs.cloudfoundry.org/adminguide/isolation-segments.html](https://docs.cloudfoundry.org/adminguide/isolation-segments.html).
-   TCP Routing. See [https://docs.cloudfoundry.org/adminguide/enabling-tcp-routing.html](https://docs.cloudfoundry.org/adminguide/enabling-tcp-routing.html).
-   Secure Service Credential Delivery \(with Credhub\). See [https://docs.cloudfoundry.org/credhub/index.html](https://docs.cloudfoundry.org/credhub/index.html) or [https://github.com/cloudfoundry/credhub/blob/main/docs/secure-service-credentials.md](https://github.com/cloudfoundry/credhub/blob/main/docs/secure-service-credentials.md)




</td>
</tr>
</table>

<a name="loio9809fa4f02cb4696baea5c23d6eaac94"/>

<!-- loio9809fa4f02cb4696baea5c23d6eaac94 -->

## SAP BTP-Specific Configurations



The following technical configurations are specific to SAP BTP and differ from the default configuration:

-   SAP BTP supports the Cloud Foundry command line interface \(CF CLI\) version 8 or newer. Older versions of the CF CLI are not supported.

-   By default, a newly pushed \(or started\) Cloud Foundry application needs to respond to a health check within the first 60 seconds, otherwise the application is considered to have failed. For more information, see [https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html\#health\_check\_timeout](https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html#health_check_timeout). On SAP BTP, however, you can override this timeout to up to 10 minutes. For instructions, see [https://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html](https://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html).

-   On SAP BTP, application SSH access is disabled by default. For more information on SSH, see [https://docs.cloudfoundry.org/devguide/deploy-apps/app-ssh-overview.html](https://docs.cloudfoundry.org/devguide/deploy-apps/app-ssh-overview.html).

-   SAP BTP supports the Cloud Foundry API version 3. The Cloud Foundry API v2 has been deprecated and is no longer supported. For more information, see [https://v3-apidocs.cloudfoundry.org/](https://v3-apidocs.cloudfoundry.org/).

-   On SAP BTP, the Cloud Foundry API is protected by a rate limit against misuse. The limit is in the range of a few 10k requests per hour per user. Starting in April 2023, the rate limit for the deprecated Cloud Foundry API v2 will be decreased and eventually reach the range of a few hundred requests per hour per user.

-   In addition to the general rate limit on the Cloud Foundry API, requests for certain API endpoints related to services face a separate limit on concurrent requests. The Cloud Foundry API responds with HTTP status code `429` if a rate limit is reached and provides a Retry-After Header suggesting when the client can attempt a retry. For more information, see [https://docs.cloudfoundry.org/running/rate-limit-cloud-controller-api.html\#Rate%20Limit%20Responses:%20Service%20Brokers](https://docs.cloudfoundry.org/running/rate-limit-cloud-controller-api.html#Rate%20Limit%20Responses:%20Service%20Brokers).

-   In the SAP BTP, Cloud Foundry environment, the total HTTP Request Header and HTTP Response Header size is limited to 64 KB to protect against misuse.

-   In the SAP BTP, Cloud Foundry environment, for both HTTP Request Headers and HTTP Response Headers the total amount of Headers is limited to 101 to protect against misuse.

-   In the Cloud Foundry environment, there’s a logging rate limit to guard against malicious applications. The limit is in the range of up to a few thousand logs per second per application instance. If this limit is exceeded, additional logs from the application instance are dropped and a warning message is injected into the application instance’s log stream every second. This message also contains the exact log rate limit.

-   Applications requiring sent envelopes to be delivered to external Log Management Services should use the Cloud Foundry syslog drain capability. See [https://docs.cloudfoundry.org/devguide/services/log-management.html](https://docs.cloudfoundry.org/devguide/services/log-management.html).

-   In the SAP BTP, Cloud Foundry environment, the time between signaling a container to shut down gracefully and forcefully stopping it is set to 60 seconds. The default in Cloud Foundry is 10 seconds, see [https://docs.cloudfoundry.org/devguide/deploy-apps/app-lifecycle.html\#shutdown](https://docs.cloudfoundry.org/devguide/deploy-apps/app-lifecycle.html#shutdown). This time interval will not be taken into account if there are no explicit kernel signal handlers implemented in the application.

-   In the SAP BTP, Cloud Foundry environment, applications get a guaranteed CPU share of ¼ core per GB instance memory. As the maximum instance memory per application is 8 GB, this allows for vertical scaling up to 2 CPUs.

    If applications running on the same virtual machine don't use their guaranteed CPU, other applications might get more CPU. This isn’t guaranteed and might be subject to change in the future. If you encounter performance problems, scale up your application or increase the application start timeout.

    The number of running threads per application instance is limited to 10 420. Reaching this limit can cause performance issues.

-   When pushing or scaling your application, you can define a `disk_quota` that can be up to 10 GB. For more information, see [https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html\#disk-quota](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html#disk-quota).

-   When deploying applications on SAP BTP, the maximum application package size is 1.5 GB. If your application is larger than that, the deployment fails. For more information, see [https://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html](https://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html)

-   In global accounts that support the consumption-based commercial model you might see a quota limit for certain services. This is a technical limit only, not a business limit. If you need to increase this limit, report an incident to [SAP support](https://support.sap.com/en/index.html) for component BC-NEO-CIS.

-   In the SAP BTP, Cloud Foundry environment, the SAP HANA database supports up to 1,000 simultaneous connections per database.

-   Cloud Foundry Audit Events have a retention period of 14 days. For more information on Audit Events, see [https://docs.cloudfoundry.org/running/managing-cf/audit-events.html](https://docs.cloudfoundry.org/running/managing-cf/audit-events.html).


<a name="loiob6a7e11c3a58416a9ab1175bba17193a"/>

<!-- loiob6a7e11c3a58416a9ab1175bba17193a -->

## Availability Zones in the Cloud Foundry Environment

The Cloud Foundry environment follows the recommendations of our partner IaaS providers by leveraging the availability zones \(AZ\) concept.



<a name="loiob6a7e11c3a58416a9ab1175bba17193a__section_nty_twt_wjb"/>

## About Availability Zones

**Availability zones** \(AZ\) are single failure domains within a single geographical region and are separate physical locations with independent power, network, and cooling. Multiple AZs exist in one region and are connected with each other through a low-latency network.

  
  
**2-AZ and 3-AZ Deployments**

![](images/Availability_Zone_af5d046.png "2-AZ and 3-AZ Deployments")

To achieve better fault-tolerance, our partners recommend deploying services across multiple AZs, which improves the availability of a service if there are issues with the region infrastructure of one AZ.



<a name="loiob6a7e11c3a58416a9ab1175bba17193a__section_av2_yvs_mmb"/>

## High Availability at Platform and Application Level

The SAP BTP Cloud Foundry environment follows these recommendations to support high availability at the platform and application level:

-   **High availability of the platform components:**

    -   The building blocks of Cloud Foundry and the virtual machines on which the Cloud Foundry application instances are scheduled run in a high availability setup. Their instances are distributed across different AZs.

    -   The technology that manages the deployment of the Cloud Foundry environment monitors the health of the platform. If there are infrastructure failures, it re-creates the faulty components.


-   **High availability on the application level:**

    -   We recommend running multiple application instances to increase availability. For more information, see [Run Multiple Instances to Increase Availability](https://docs.cloudfoundry.org/devguide/deploy-apps/prepare-to-deploy.html#increase-availability). On SAP BTP, there are three ways to increase application instances:

        -   Scaling your application using the application manifest. The `manifest.yml` allows you to make and save configurations for your application. To scale, you can configure the instance count in the manifest and push the application again with the new configuration. See [App Manifest Attribute Reference](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html#instances). To avoid downtimes when updating your application configuration, you can also consider using rolling application deployments. See [Rolling App Deployments](https://docs.cloudfoundry.org/devguide/deploy-apps/rolling-deploy.html).
        -   Scaling your application using the `cf scale` command in the Cloud Foundry command line interface \(CF CLI\). See [Scaling an App Using cf scale](https://docs.cloudfoundry.org/devguide/deploy-apps/cf-scale.html).
        -   Scaling your application using the SAP BTP cockpit. See [Add or Remove Application Instances](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/75836f1b68ce439e9c169b05597f97e4.html?q=high%20available).

    -   The Cloud Foundry container scheduler takes care of distributing the different instances of one application on virtual machines in different AZs. For more information, see [How Diego Balances App Processes](https://docs.cloudfoundry.org/concepts/diego/diego-auction.html).

    -   Cloud Foundry is constantly monitoring the health state of application instances and restarts instances that are considered unhealthy. See [Using App Health Checks](https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html).

    -   When the number of desired instances doesn't match the number of actually running instances, Cloud Foundry reschedules the missing instances, for example, when the virtual machines that an application instance was initially scheduled on become unresponsive.


    For more information on high availability configuration, see [High Availability in Cloud Foundry](https://docs.cloudfoundry.org/concepts/high-availability.html#overview).

    For more information on application stability and resilience, see [Develop Resilient Applications](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/b1b929a5aea64571b2f74e810b622568.html "Our best practices about resilient application design help you to make your applications running on SAP BTP stable and highly available.") :arrow_upper_right:.


<a name="loio1c6cba872ce24f2ba24f53feb6dbce6d"/>

<!-- loio1c6cba872ce24f2ba24f53feb6dbce6d -->

## Additional Information About Cloud Foundry

Links to additional information about Cloud Foundry that is useful to know but not necessarily directly connected to the SAP BTP, Cloud Foundry environment.




<table>
<tr>
<th valign="top">

Content

</th>
<th valign="top">

Location

</th>
</tr>
<tr>
<td valign="top">

BOSH

</td>
<td valign="top">

[http://bosh.cloudfoundry.org](http://bosh.cloudfoundry.org) 

</td>
</tr>
<tr>
<td valign="top">

BOSH documentation

</td>
<td valign="top">

[http://bosh.io/docs](http://bosh.io/docs) 

</td>
</tr>
<tr>
<td valign="top">

Buildpacks

</td>
<td valign="top">

[http://docs.cloudfoundry.org/buildpacks](http://docs.cloudfoundry.org/buildpacks) 

</td>
</tr>
<tr>
<td valign="top">

Components of Cloud Foundry 

</td>
<td valign="top">

[http://docs.cloudfoundry.org/concepts/architecture/](http://docs.cloudfoundry.org/concepts/architecture/) 

</td>
</tr>
<tr>
<td valign="top">

Cloud Foundry Concepts

</td>
<td valign="top">

[http://docs.cloudfoundry.org/concepts/](http://docs.cloudfoundry.org/concepts/) 

</td>
</tr>
<tr>
<td valign="top">

Deployment of Cloud Foundry 

</td>
<td valign="top">

[http://docs.cloudfoundry.org/deploying](http://docs.cloudfoundry.org/deploying) 

</td>
</tr>
<tr>
<td valign="top">

Developer Guide for Cloud Foundry 

</td>
<td valign="top">

[http://docs.cloudfoundry.org/devguide](http://docs.cloudfoundry.org/devguide) 

</td>
</tr>
<tr>
<td valign="top">

Diego Application Process Balancing

</td>
<td valign="top">

[https://docs.cloudfoundry.org/concepts/diego/diego-auction.html](https://docs.cloudfoundry.org/concepts/diego/diego-auction.html) 

</td>
</tr>
<tr>
<td valign="top">

Glossary for Cloud Foundry 

</td>
<td valign="top">

[http://docs.cloudfoundry.org/concepts/glossary.html](http://docs.cloudfoundry.org/concepts/glossary.html) 

</td>
</tr>
<tr>
<td valign="top">

Overview of Cloud Foundry 

</td>
<td valign="top">

[http://docs.cloudfoundry.org/concepts/overview.html](http://docs.cloudfoundry.org/concepts/overview.html) 

</td>
</tr>
<tr>
<td valign="top">

Sample applications for Cloud Foundry 

</td>
<td valign="top">

[https://github.com/cloudfoundry-samples](https://github.com/cloudfoundry-samples) 

</td>
</tr>
<tr>
<td valign="top">

Security settings for Cloud Foundry 

</td>
<td valign="top">

[http://docs.cloudfoundry.org/concepts/security.html](http://docs.cloudfoundry.org/concepts/security.html) 

</td>
</tr>
<tr>
<td valign="top">

Cloud Foundry Services

</td>
<td valign="top">

[http://docs.cloudfoundry.org/services](http://docs.cloudfoundry.org/services)

[http://docs.cloudfoundry.org/devguide/services/user-provided.html](http://docs.cloudfoundry.org/devguide/services/user-provided.html)

</td>
</tr>
<tr>
<td valign="top">

Considerations for designing and running an application in the cloud

</td>
<td valign="top">

[http://docs.cloudfoundry.org/devguide/deploy-apps/prepare-to-deploy.html](http://docs.cloudfoundry.org/devguide/deploy-apps/prepare-to-deploy.html) 

</td>
</tr>
<tr>
<td valign="top">

Installing the Cloud Foundry command line interface

</td>
<td valign="top">

[http://docs.cloudfoundry.org/devguide/installcf/install-go-cli.html](http://docs.cloudfoundry.org/devguide/installcf/install-go-cli.html) 

</td>
</tr>
<tr>
<td valign="top">

Blog about Cloud Foundry 

</td>
<td valign="top">

[http://blog.cloudfoundry.org/](http://blog.cloudfoundry.org/) 

</td>
</tr>
</table>

