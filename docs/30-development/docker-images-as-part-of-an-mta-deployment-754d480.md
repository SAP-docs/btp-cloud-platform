<!-- loio754d4800b69b478eaa2427338c5d47e5 -->

# Docker Images as Part of an MTA Deployment

Deploy Docker images as part of a Multitarget application.

You can depoy your own or 3rd party Docker images in the Cloud Foundry environment by referencing them in an application module.

This type of application deployment is faster, as images are already built. Thus, staging is not required, and also all dependencies are statically included in the image.

> ### Note:  
> When you reference docker images, MTA packages are not self-sustained - they depend on external repositories hosting images for the deployment.

You can deploy Docker images as MTA modules using the Cloud Foundry command line interface.

To deploy a Docker image as a Cloud Foundry application, your deployment descriptor should reference the image in a module as described in the following example:

> ### Sample Code:  
> ```
> …
> modules:
>   name: foo
>   type: application
>     parameters:
>       docker:
>         image: cloudfoundry/test-app 
>         username: <username>
>         password: <password>
>     build-parameters: #only required for mta.yaml
>         no-source: true
> 
> … 
> 
> ```

Using the parameters above:

-   `image` - you reference the location of the image so that it can be scheduled for download by the patform. You have to provide the location of the image using the format `<registry.domain><:port>/repo/image:<tag>`. If you do not do so, images are referenced from Docker Hub. See more about deploying an application with Docker in the provided link at the end of the section.
-   \(Optional\) `username` and `password` - you provide credentials in the descriptor only when the image repository requires them.
-   Only when you create an MTA development descriptor \(`mta.yaml`\) to build with the Cloud MTA Build Tool, you have to enter the parameter `no-source: true` in the `build-parameters` section.

**Related Information**  


[Cloud Foundry Documentation: Deploying an App with Docker](https://docs.cloudfoundry.org/devguide/deploy-apps/push-docker.html)

[CF MTA Examples in GitHub: Deploying Docker Images as CF Apps with an MTA](https://github.com/SAP-samples/cf-mta-examples/tree/master/cf-app-docker)

[https://hub.docker.com/](https://hub.docker.com/)

[Cloud MTA Build Tool: Configuring a module that does not have source code to build and package](https://sap.github.io/cloud-mta-build-tool/configuration/#configuring-a-module-that-does-not-have-source-code-to-build-and-package)

