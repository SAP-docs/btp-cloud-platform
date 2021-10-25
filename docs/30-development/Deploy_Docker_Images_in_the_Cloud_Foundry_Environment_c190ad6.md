<!-- loioc190ad6eeb78428c91a2b66e5557f962 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Deploy Docker Images in the Cloud Foundry Environment

The high-level steps to application deployment using Docker images.



<a name="loioc190ad6eeb78428c91a2b66e5557f962__prereq_lll_cdy_dgb"/>

## Prerequisites

-   You are aware how `cf push` works when you deploy a regular Cloud Foundry application.

-   You need a higher degree of freedom and know that this freedom comes with higher responsibility for application operation.

-   Your Docker image resides in a highly available container registry.




## Context

A Docker image deployed to the Cloud Foundry environment has to adhere to the same boundary conditions as regular Cloud Foundry applications. Cloud Foundry applications deployed as Docker images are running in Linux containers with user namespaces enabled, which prevents certain functionality like mounting FuseFS devices. Another difference is the usage of buildpacks. Docker images can't be used in combination with buildpacks. If you want to use certain functionality provided by the buildpack, you have to build it into your Docker image.

Compared to regular Cloud Foundry applications, using a Docker image means more effort for you. If the following factors are fulfilled, using Docker on Cloud Foundry might be a viable option.

1.  Managing a whole cluster on Kubernetes is too much overhead for your scenario.

2.  The usual approach doesn't let you realize what you want to achieve.


Here are some features of the Cloud Foundry environment you have to implement yourself in your Docker image. The comparison is made with the SAP Java buildpack.


<table>
<tr>
<th valign="top">

Supported with SAP Java buildpack



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Dynatrace



</td>
<td valign="top">

Enable applications for Dynatrace based monitoring.



</td>
</tr>
<tr>
<td valign="top">

XSUAA



</td>
<td valign="top">

Automatic validation of OAuth token and mapping of OAuth scopes to JEE roles, if `auth-method` is set to XSUAA in `web.xml`.



</td>
</tr>
<tr>
<td valign="top">

Dynamic Logging



</td>
<td valign="top">

Set of log level via CLI without restart.



</td>
</tr>
<tr>
<td valign="top">

Switch to debug via CLI



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

OS & JVM management



</td>
<td valign="top">

Consume newer versions \(especially patches\) of the underlying OS and JVM regularly..



</td>
</tr>
</table>



## Procedure

1.  Your Docker image adheres to the 12 factor principles.

    [https://12factor.net/](https://12factor.net/)

2.  You only use supported features in the SAP BTP, Cloud Foundry environment, see [Cloud Foundry Environment](../10-concepts/Cloud_Foundry_Environment_9c7092c.md#loio9c7092c7b7ae4d49bc8ae35fdd0e0b18)

3.  Read what the open source documentation says about deploying an application with Docker.

    Pay special attention to the mentioned requirements. [Deploy an App with Docker](https://docs.cloudfoundry.org/devguide/deploy-apps/push-docker.html)

    Requires traffic routing to the lowest numbered port. [How Diego Runs and Monitors Processes](https://docs.cloudfoundry.org/adminguide/docker.html#run-monitor)

4.  Use `cf push` with the `--docker-image` parameter.

    This is an example if you want to push from Docker Hub:

    ```
    cf push *<APP-NAME\>* --docker-image *<REPO\>*/*<IMAGE\>*:*<TAG\>*
    ```

    Also pay attention to the section on private registries and Google Container Registry. [Push a Docker Image From Docker Hub](https://docs.cloudfoundry.org/devguide/deploy-apps/push-docker.html#public)

5.  Operate and patch your Docker images.

    Docker images contain everything that is necessary to run a process, including the operating system and libraries into one binary blob. Consequently, staging a Docker image in Cloud Foundry does not provide the same separation of droplet and stack that is available for a Cloud Foundry application staged using a buildpack.

    If there is an operating system and library security vulnerability, the developer is responsible to `cf push` a new version of the Docker images . The developer using the platform has the responsibility for watching these security vulnerabilities and for reacting accordingly.

    For scale or restart operations, the image is pulled again from the container registry. The container registry has to be highly available and reachable from network side for proper operations.




<a name="loioc190ad6eeb78428c91a2b66e5557f962__result_xph_hyt_ngb"/>

## Results

Was this topic helpful? Did you miss something? Let us know and use the feedback function <span class="SAP-icons"></span> \(feedback\).

