<!-- loio8d2a68a263f64a8884ab19822227a325 -->

# Benefits of the Multitarget Application Model for the Cloud Foundry Environment

The benefits of the multitarget application \(MTA\) approach can be related to the three “A”s that the MTA offers - Abstraction, Automation, and Assembly.

-   Abstraction - The MTA model abstracts the underlying heterogeneity of application parts, which can grow over time, and offers a standardized way to model dependencies and environment specific configurations. In the absence of such a common model, you would have to individually handle all this heterogeneity, using custom scripts in a CI/CD tool to manage all underlying components, the service dependencies, and the configurations – achieving the needed automation through such custom scripts is not a trivial task. And maintaining such scripts – as the technologies and services used by the application changes – demands higher effort. Modeling your application as an MTA highly simplifies the lifecycle of such heterogeneous applications.
-   Automation - By specifying your application structure and its dependencies \(the “What”\), you set the Multitarget Application Deployment Service to handle the automated deployment or undeployment, service instance creation and binding, “Blue-Green” updates, configuration injection, and so on \(the “How”\). This automation significantly reduces the overhead needed in CI/CD pipelines to orchestrate all the steps needed for such deployment related processes.
-   Assembly - By offering a standard packaging format for your applications, the MTA serves as a release artifact. Such an assembly \(of the application and all its metadata\) can be useful in different contexts: in audited environments where a signed artifact is mandatory, to move deployable artifacts through a firewall, to apply different policies based on the deployment target, or to distribute the application to other consumers \(for example a partner distributing a business application to several customers, who deploy it in their accounts or tenants\).



<a name="loio8d2a68a263f64a8884ab19822227a325__section_otj_hzc_mgb"/>

## Deciding on the Right Size for a Multitarget Application

Your business application may grow over time. When this happens, you should decide on the volume of data for your MTA or multiple MTAs by analyzing which pieces make sense to be managed together as separate lifecycle management unit.

A popular example is the case for a “core” or “framework” application parts that could work on their own, offering the basic business capabilities. Then there might be an “extension” or “plugin” applications that extend the basic business capabilities, but are not mandatory and could be released and updated separately.

Another possibility is to model just one single Cloud Foundry application in a separate MTA. This makes sense if the application can be considered a self-contained microservice. However, even such one Cloud Foundry app in one MTA modeling still bears the benefits of dependency management \(for example, backing service creation and external API lookup\), content management \(Fiori Launchpad configurations, workflow definitions, and so on\) and configuration management \(utilizing system placeholders, default and deployment specific configuration\).



<a name="loio8d2a68a263f64a8884ab19822227a325__section_wkm_rnn_5jb"/>

## Other Benefits

-   Parallel deployment - This feature enables asynchronous deployment of multiple applications, this way the deployment of the archive is faster.
-   Asynchronous service instance creation - The MTA deployer creates services asynchronously, this way decreasing the deployment time.
-   Parallel undeployment - This feature enables asynchronous undeployment of applications, this way decreasing the undeployment time.

