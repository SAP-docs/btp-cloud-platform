<!-- loio9809fa4f02cb4696baea5c23d6eaac94 -->

# SAP BTP-Specific Configurations

Learn about technical configurations for Cloud Foundry that are specific to SAP BTP.



The following technical configurations are specific to SAP BTP and differ from the default configuration:

-   SAP BTP supports the Cloud Foundry command line interface \(CF CLI\) version 8 or newer. Older versions of the CF CLI are not supported.

-   By default, a newly pushed \(or started\) Cloud Foundry application needs to respond to a health check within the first 60 seconds, otherwise the application is considered to have failed. For more information, see [https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html\#health\_check\_timeout](https://docs.cloudfoundry.org/devguide/deploy-apps/healthchecks.html#health_check_timeout). On SAP BTP, however, you can override this timeout to up to 10 minutes. For instructions, see [https://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html](https://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html).

-   On SAP BTP, application SSH access is disabled by default. For more information on SSH, see [https://docs.cloudfoundry.org/devguide/deploy-apps/app-ssh-overview.html](https://docs.cloudfoundry.org/devguide/deploy-apps/app-ssh-overview.html).

-   SAP BTP supports the Cloud Foundry API version 3. The Cloud Foundry API v2 has been deprecated and is no longer supported. For more information, see [https://v3-apidocs.cloudfoundry.org/](https://v3-apidocs.cloudfoundry.org/).

-   On SAP BTP, the Cloud Foundry API is protected by a rate limit against misuse. The limit is in the range of a few 10k requests per hour per user on average. The rate limit for the deprecated Cloud Foundry API v2 is in the range of a few hundred requests per hour per user.

-   In addition to the general rate limit on the Cloud Foundry API, requests for certain API endpoints related to services face a separate limit on concurrent requests. The Cloud Foundry API responds with HTTP status code `429` if a rate limit is reached and provides a Retry-After Header suggesting when the client can attempt a retry. For more information, see [https://docs.cloudfoundry.org/running/rate-limit-cloud-controller-api.html\#Rate%20Limit%20Responses:%20Service%20Brokers](https://docs.cloudfoundry.org/running/rate-limit-cloud-controller-api.html#Rate%20Limit%20Responses:%20Service%20Brokers).

-   In the SAP BTP, Cloud Foundry environment, the total HTTP Request Header and HTTP Response Header size is limited to 64 KB to protect against misuse.

-   In the SAP BTP, Cloud Foundry environment, for both HTTP Request Headers and HTTP Response Headers the total amount of headers is limited to 101. Components that are handling the requests will add system-relevant headers such as `X-Vcap-Request-Id` or `X-Ssl-*` when mTLS is used. This addition reduces the amount of headers that can be set by the client \(for requests\) or the application \(for responses\).

-   In the SAP BTP, Cloud Foundry environment, the limit of concurrent HTTP connections between client and application is 3000 per application container.

-   In the SAP BTP, Cloud Foundry environment, the HTTP `keep-alive` timeout towards the client is set to 60s to protect against misuse. 60s is the maximum time span allowed to wait for a new HTTP request to appear if `keep-alive` is enabled.

-   In the SAP BTP, Cloud Foundry environment, an internal HTTP `keep-alive` is set to 90s. A higher value must be set on application-side to avoid intermittent disruptions. For more information, see step 4 of [3406978](https://me.sap.com/notes/3406978).

-   In the Cloud Foundry environment, there’s a logging rate limit to guard against malicious applications. By default, the limit is 4000 logs per second per application instance, but in exceptional high load scenarios it may be lowered by the platform. If this limit is exceeded, additional logs from the application instance are dropped and a warning message is injected into the application instance’s log stream every second. This message also contains the exact current log rate limit.

-   Applications requiring sent envelopes to be delivered to external Log Management Services should use the Cloud Foundry syslog drain capability. See [https://docs.cloudfoundry.org/devguide/services/log-management.html](https://docs.cloudfoundry.org/devguide/services/log-management.html).

-   In the SAP BTP, Cloud Foundry environment, the time between signaling a container to shut down gracefully and forcefully stopping it is set to 60 seconds. The default in Cloud Foundry is 10 seconds, see [https://docs.cloudfoundry.org/devguide/deploy-apps/app-lifecycle.html\#shutdown](https://docs.cloudfoundry.org/devguide/deploy-apps/app-lifecycle.html#shutdown). This time interval will not be taken into account if there are no explicit kernel signal handlers implemented in the application.

-   In the SAP BTP, Cloud Foundry environment, applications get a guaranteed CPU share of ¼ core per GB instance memory. As the maximum instance memory per application is 16 GB, this allows for vertical scaling up to 4 CPUs.

    If applications running on the same virtual machine don't use their guaranteed CPU, other applications might get more CPU. This isn’t guaranteed and might be subject to change in the future. If you encounter performance problems, scale up your application or increase the application start timeout.

    The number of running threads per application instance is limited to 10,420. Reaching this limit can cause performance issues.

-   When pushing or scaling your application, you can define a `disk_quota` that can be up to 10 GB. For more information, see [https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html\#disk-quota](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest-attributes.html#disk-quota).

-   When deploying applications on SAP BTP, the maximum application package size is 1.5 GB. If your application is larger than that, the deployment fails. For more information, see [https://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html](https://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html).

-   In the SAP BTP, Cloud Foundry environment, the hard limit for open file descriptors is 32,768 \(32K\) per container.

-   In global accounts that support the consumption-based commercial model you might see a quota limit for certain services. This is a technical limit only, not a business limit. If you need to increase this limit, report an incident to [SAP support](https://support.sap.com/en/index.html) for component BC-NEO-CIS.

-   In the SAP BTP, Cloud Foundry environment, the SAP HANA database supports up to 1000 simultaneous connections per database.

-   In the SAP BTP, Cloud Foundry environment, each application can be mapped to approximately 1000 routes \(128 KB\). The total length of the routing information must not exceed this limit.

-   Cloud Foundry Audit Events have a retention period of 14 days. For more information on Audit Events, see [https://docs.cloudfoundry.org/running/managing-cf/audit-events.html](https://docs.cloudfoundry.org/running/managing-cf/audit-events.html).


