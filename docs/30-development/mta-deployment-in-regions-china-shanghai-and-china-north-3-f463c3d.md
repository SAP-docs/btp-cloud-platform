<!-- loiof463c3d1edfa4dd8bd525c43bd0f1a6b -->

# MTA Deployment in Regions China \(Shanghai\) and China \(North 3\)

Find information on region-specific deployment configurations for regions China \(Shanghai\) and China \(North 3\).



<a name="loiof463c3d1edfa4dd8bd525c43bd0f1a6b__section_xtl_ls2_bgc"/>

## Configuring Domains for Cloud Foundry Applications

Most of the Cloud Foundry applications deployed as part of an MTA have assigned routes at the end of the MTA deployment. You can specify the route by using various module-level parameters as described in [Routes](routes-53daaaf.md).

If you do not specify the route by using one of these parameters, a placeholder `default-uri` is automatically applied. This placeholder is resolved to `${default-host}.${default-domain}`, where `${default-domain}` is resolved to the default domain for the current Cloud Foundry organization. This value is coming from the Cloud Foundry API and it cannot be configured by the end user. Usually, the default domain is resolved to `cfapps.<region>.hana.ondemand.com`. However, due to missing shared domains in regions China \(Shanghai\) and China \(North 3\), the default domain value is not resolved properly, and so the MTA parameter `${default-domain}` is not resolved properly as well.

You may encounter this problem in one of the following cases:

-   You rely on the default implicit logic during MTA deployment and the parameters `domain` or `routes` are not configured at all.
-   You explicitly use `${default-domain}` somewhere in the routes configuration:

    > ### Example:  
    > > ### Sample Code:  
    > > ```
    > > modules:
    > > - name: my-app
    > >   type: application
    > >   parameters:
    > >     routes:
    > >       - route: "my-route.${default-domain}"
    > > ```


To avoid problems when deploying MTAs in regions China \(Shanghai\) and China \(North 3\), please avoid using the `${default-domain}` parameter. Instead, configure the domains for your Cloud Foundry applications by following these steps:

1.  Configure a custom domain for your applications. When a custom domain is used, both the domain name and the TLS/SSL certificate of the server are owned by the customer. You can configure custom domains using the Cloud Foundry command-line interface with the plugin for custom domains. For more information, see [What Is Custom Domain](https://help.sap.com/docs/CUSTOM_DOMAINS/74af813c7ee2457cb5eddca0cc70a0c1/4414cc43db2d4229b27b232a5590e253.html?locale=en-US) and [Custom Domain Plugin for the Cloud Foundry Environment](../50-administration-and-ops/custom-domain-plugin-for-the-cloud-foundry-environment-1832fcd.md).

2.  Configure your MTA descriptor to use the custom domain. You can do this in one of the following ways:



### Using the `routes` parameter \(recommended\)

```
modules:
- name: my-app
  type: application
  parameters:
    routes:
      - route: "my-route.my.custom.domain"
```

When you update your MTA by using [Blue-Green Deployment of Multitarget Applications](blue-green-deployment-of-multitarget-applications-772ab72.md), you also need to configure `idle-routes` respectively. Otherwise, in the first phase of blue-green deployment, newly created applications will use `${default-domain}`, which might lead to problems.

```
modules:
- name: my-app
  type: application
  parameters:
    routes:
      - route: "my-route.my.custom.domain"
    idle-routes:
      - idle-route: "my-route-idle.my.custom.domain"
```



### Using the `domain` or `domains` parameter

```
modules:
- name: my-app
  type: application
  parameters:
    domain: my.custom.domain
```

When you update your MTA by using [Blue-Green Deployment of Multitarget Applications](blue-green-deployment-of-multitarget-applications-772ab72.md), you also need to configure `idle-domain` or `idle-domains` respectively. Otherwise, in the first phase of blue-green deployment, newly created applications will use `${default-domain}`, which might lead to problems.

```
modules:
- name: my-app
  type: application
  parameters:
    domain: my.custom.domain
    idle-domain: my.custom.domain
```

> ### Note:  
> The `domain` and `domains` parameters are deprecated, so their usage is not recommended. Use the `routes` parameter instead.



<a name="loiof463c3d1edfa4dd8bd525c43bd0f1a6b__section_vth_1hf_bgc"/>

## Specifying the SAP Cloud Deployment Service URL

> ### Note:  
> This section is relevant only for multitarget application developers who are using a version of the MultiApps CF CLI plugin that is older than 3.0.0. If you are using a version of the MultiApps CF CLI plugin that is newer than 3.0.0, you do not need to do the additional settings described below. It is recommended to update the MultiApps CF CLI plugin regularly to the latest release - see [Releases](https://github.com/cloudfoundry/multiapps-cli-plugin/releases).

Due to the missing shared domains in regions China \(Shanghai\) and China \(North 3\), you need to specify the URL of the Cloud Deployment service in one of the following ways:

-   by setting the MULTIAPPS\_CONTROLLER\_URL environment variable. For more information, see [Configuration](https://github.com/cloudfoundry/multiapps-cli-plugin?tab=readme-ov-file#configuration).
-   by using the <code><i>-u</i> <i class="varname">&lt;URL&gt;</i></code> command option of the [Multitarget Application Commands for the Cloud Foundry Environment](../50-administration-and-ops/multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md).

    > ### Note:  
    > If you are using this option, make sure you have the MultiApps CLI plugin version 2.1.3 or higher.


The deploy-service URL needs to be in the following format: `deploy-service.cf.<domain>`. You can derive the domain from the Cloud Foundry API endpoint which is visible in the *Overview* of your subaccount in the SAP BTP cockpit. See also [Regions and API Endpoints Available for the Cloud Foundry Environment](../10-concepts/regions-and-api-endpoints-available-for-the-cloud-foundry-environment-f344a57.md).

> ### Note:  
> For region China \(Shanghai\) with API endpoint `api.cf.cn40.platform.sapcloud.cn`, you need to specify the URL as follows: `export MULTIAPPS_CONTROLLER_URL=deploy-service.cf.cn40.platform.sapcloud.cn`.



<a name="loiof463c3d1edfa4dd8bd525c43bd0f1a6b__section_z2g_znf_bgc"/>

## Optimizing MTA Deployment Time

In most cases, MTA deployment is done from one single CI/CD towards different target regions, including European, American and China regions. In the beginning of one MTA deployment, an MTA archive is uploaded from the CI/CD or from a local machine towards the Cloud Deployment service located in the specific region. Sometimes, connection problems \(connection drops or is lost completely\) might occur between other regions and regions China \(Shanghai\) and China \(North 3\). For example, if the CI/CD is in a European region and the MTA deployment is towards China \(Shanghai\) or China \(North 3\), it is very likely to observe problems while uploading the MTA archive to Cloud Deployment service.

To avoid such connection problems, you can try following these approaches:

-   If you are using the MultiApps CF CLI plugin, which provides the `cf deploy` command, you can decrease the chunk size of the MTA archive – in this way, the whole MTA archive will be split in parts, where each part has smaller size. It is expected that the smaller parts will be uploaded more easily. For more information, see [Configuration](https://github.com/cloudfoundry/multiapps-cli-plugin?tab=readme-ov-file#configuration).
-   Instead of deploying a local MTA archive, pass the URL of the archive and Cloud Deployment service will download it. For more information, see **Deployment using a URL to the MTA archive** in [Multitarget Application Commands for the Cloud Foundry Environment](../50-administration-and-ops/multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md).

    This approach is suitable for adoption for other regions as well. It brings optimization in MTA archive upload and overall MTA deployment time, especially for MTA archives with larger size.


**Related Information**  


[MultiApps CF CLI Plugin](https://github.com/cloudfoundry/multiapps-cli-plugin?tab=readme-ov-file#multiapps-cf-cli-plugin-)

[Multitarget Application Commands for the Cloud Foundry Environment](../50-administration-and-ops/multitarget-application-commands-for-the-cloud-foundry-environment-65ddb1b.md "A list of additional commands to deploy multitarget applications (MTA) to the Cloud Foundry environment.")

