<!-- loiodc25fff149b34301b1d5bbfb04796ff2 -->

# Serverless Buildless Mode

Learn how to accelerate your development with Serverless buildless mode.

From the beginning, Kyma Serverless has aimed to accelerate the development of fast prototypes by allowing users to focus on business logic rather than containerization and Kubernetes deployment. Our goal is to remove operational barriers so developers can iterate quickly and efficiently.

With the introduction of buildless mode, we significantly shortened the feedback loop during prototype development by eliminating the image build step in Kyma runtime. In buildless mode, instead of building and pushing custom Function images into the in-cluster registry, your code and dependencies are mounted into Kyma-provided runtime images. This approach positions Kyma Serverless as a more efficient development tool, enabling even faster iteration. Additionally, it eliminates the architectural complexities and limitations of deploying Serverless Functions on Kubernetes.



<a name="loiodc25fff149b34301b1d5bbfb04796ff2__section_v4b_v31_hgc"/>

## Features

-   **Simplified architecture**: By separating the Docker Registry into its own module, the Serverless module is now more lightweight and easier to manage.
-   **Faster deployment**: The removal of the build job reduces the time required to deploy Functions.
-   **Dynamic dependency resolution**: Dependencies are resolved at runtime, allowing for more flexibility in managing library versions.
-   **Improved flexibility**: Injecting Function code into the runtime Pod simplifies the deployment process and reduces image management overhead.
-   **Reduced resource consumption**: Eliminating build jobs means Serverless no longer requires computational resources from worker nodes for image building.
-   **Enhanced security**: By removing build jobs, Functions can run in namespaces with more restrictive Pod security levels enabled.



<a name="loiodc25fff149b34301b1d5bbfb04796ff2__section_vtn_3j1_hgc"/>

## Outcomes of Switching to Buildless Mode

-   Your Serverless module no longer includes an internal Docker Registry.
-   Function builds are eliminated. Your Functions use a base image that mounts dependencies dynamically at runtime.
-   Function dependencies are downloaded each time a Function Pod starts. This means different replicas of the same Function may use different dependency versions if you don't pin exact versions.
-   Your Function code is injected directly into runtime Pods without requiring pre-built container images.



<a name="loiodc25fff149b34301b1d5bbfb04796ff2__section_zjg_xj1_hgc"/>

## **Using Fixed Dependency Versions**

-   **Avoid using `latest` versions of Function dependencies**: Since dependencies are resolved at the Function's Pod start time in buildless mode, using `latest` versions can lead to inconsistencies between replicas of the same Function. This may be the case when the dependency provider releases a new version after one replica is already running and before another replica is created due to auto-scaling. Always specify exact versions of dependencies to ensure stability and predictability.
-   **Dependency resolution behavior**: Be aware that each replica of a Function may resolve and use a different dependency version if the version is not explicitly pinned.

<a name="task_vsg_bk1_hgc"/>

<!-- task\_vsg\_bk1\_hgc -->

## **Disabling Buildless Mode**

To learn how to disable Serverless buildless mode, see [Configuring Serverless](configuring-serverless-b40a119.md).

