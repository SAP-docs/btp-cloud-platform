<!-- loiob6a7e11c3a58416a9ab1175bba17193a -->

# Availability Zones in the Cloud Foundry Environment

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

    For more information on application stability and resilience, see [Developing Resilient Applications](https://help.sap.com/docs/BTP/0c8c1db388f645159e134a005aaabbcf/b1b929a5aea64571b2f74e810b622568.html?locale=en-US&state=PRODUCTION&version=Cloud).


