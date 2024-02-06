<!-- loio8d2a68a263f64a8884ab19822227a325 -->

# Benefits of the Multitarget Application Model for the Cloud Foundry Environment

The benefits of the multitarget application \(MTA\) approach can be related to the three “A”s that the MTA offers - Abstraction, Automation, and Assembly.

-   Abstraction - Simply put, the MTA model uses abstraction to handle the diversity and complexity of different parts of an application, which may increase over time. This method offers a standardized way of modeling dependencies and environment-specific configurations. Without the MTA model you would have to individually handle all this heterogeneity, using custom scripts in a CI/CD tool to manage all underlying components, service dependencies and configurations. Achieving the needed automation through such custom scripts may be labor-intensive. It also demands higher effort as the technologies and services used by the application change over time. Modeling your application as an MTA highly simplifies the lifecycle of such heterogeneous applications.
-   Automation - By defining your application's structure and dependencies \(the “What”\), you can use the SAP Cloud Deployment Service to manage automated tasks like deployment, service creation, updates and binding \(the “How”\). This reduces the work required in CI/CD pipelines to oversee all these deployment-related tasks.
-   Assembly - By offering a standard packaging format for your applications, the MTA serves as a release artifact. This is known as an assembly. The assembly, constituting the application and all its metadata, can be useful in different contexts. One such context is audited environments, where a signed artifact is mandatory. Another use case is moving deployable artifacts through a firewall. The assembly can also be valuable in situations where different policies are applicable based on the deployment target. Furthermore, this artifact can be distributed to other consumers. For instance, a partner distributing a business application to several customers may find this useful. These customers can then deploy this application in their own accounts or tenants.



<a name="loio8d2a68a263f64a8884ab19822227a325__section_otj_hzc_mgb"/>

## Deciding on the Right Size for a Multitarget Application

Your business application may grow over time. When this happens, you should decide on the volume of data for your MTA or multiple MTAs by analyzing which pieces make sense to be managed together as a separate lifecycle management unit.

A popular example is the case for a “core” or “framework” application parts that could work on their own, offering the basic business capabilities. Then there might be “extension” or “plugin” applications that extend the basic business capabilities, but are not mandatory and could be released and updated separately.

Another possibility is to model just one single Cloud Foundry application in a separate MTA. This makes sense if the application can be considered a self-contained microservice. However, even one Cloud Foundry app in one MTA modeling bears the benefits of dependency management \(for example, backing service creation and external API lookup\), content management \(Fiori Launchpad configurations, workflow definitions, and so on\) and configuration management \(utilizing system placeholders, default and deployment specific configuration\).



<a name="loio8d2a68a263f64a8884ab19822227a325__section_wkm_rnn_5jb"/>

## Other Benefits

-   Parallel deployment - This feature enables asynchronous deployment of multiple applications, this way the deployment of the archive is faster.
-   Asynchronous service instance creation - The MTA deployer creates services asynchronously, this way decreasing the deployment time.
-   Parallel undeployment - This feature enables asynchronous undeployment of applications, this way decreasing the undeployment time.

