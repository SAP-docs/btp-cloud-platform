<!-- loio1610eac123c04d07babaf89c47d82c91 -->

# Dynatrace Integration

Dynatrace OneAgent is a Java agent that sends all captured monitoring data to your Dynatrace monitoring environment for analysis.



<a name="loio1610eac123c04d07babaf89c47d82c91__context_p1l_rrd_p2b"/>

## Context

Dynatrace supports full-stack monitoring for Cloud Foundry – from the application to the infrastructure layer. To integrate it with your Java application, follow the steps below.



<a name="loio1610eac123c04d07babaf89c47d82c91__steps_w3f_srd_p2b"/>

## Procedure

1.  Obtain an [environment ID](https://docs.dynatrace.com/docs/get-started/monitoring-environment#environment-id) and an [API access token](https://docs.dynatrace.com/docs/manage/access-control/access-tokens#create-api-token).

2.  Create a user-provided service.

    The service name should contain the string "dynatrace" \(for example, **dynatraceservice**\). The `environmentid` and `apitoken` parameters have been generated in the previous step. You also need to set up the `apiurl`, which depends on the Dynatrace type you want to integrate.

    -   **SaaS Dynatrace**

        ```
        "apiurl": "https://<environmentid>.live.dynatrace.com/api"
        ```

    -   **Managed Dynatrace**

        ```
        "apiurl": "https://<your_domain>/e/<environmentid>/api"
        ```


    Then, in cf CLI, run the following command:

    ```
    cf cups dynatraceservice -p "environmentid, apitoken, apiurl"
    ```

    For more information, see:

    -   Dynatrace Docs: [Create a user-provided service in your SAP BTP, Cloud Foundry Environment](https://www.dynatrace.com/support/help/setup-and-configuration/setup-on-container-platforms/cloud-foundry/deploy-oneagent-on-sap-cloud-platform-for-application-only-monitoring#create-a-user-provided-service-in-your-sap-btp-cloud-foundry-environment)

    -   Cloud Foundry Docs: [User-Provided Service Instances](https://docs.cloudfoundry.org/devguide/services/user-provided.html)


3.  Bind the application to the service instance created in the previous step, by using the *manifest.yml* file.

    > ### Sample Code:  
    > ```
    > ---
    > applications:
    > - name: myapp
    >   memory: 1G
    >   instances: 1
    >   buildpack: sap_java_buildpack
    >   services:
    >   - dynatraceservice
    > ```

    **NOTE:** If there are more than one Dynatrace services bound to the application, the service that's going to be used is the one that was chronologically bound first.

4.  Deploy the application to Cloud Foundry with the updated *manifest.yml* file. Run:

    ```
    cf push myapp
    ```

    Once the application receives web traffic, monitoring data will show up in Dynatrace.


**Related Information**  


[Dynatrace Docs: Access tokens API](https://docs.dynatrace.com/docs/dynatrace-api/environment-api/tokens-v2/api-tokens/get-all)

[Dynatrace Docs: Cloud Foundry Monitoring](https://docs.dynatrace.com/docs/platform-modules/infrastructure-monitoring/container-platform-monitoring/cloud-foundry-monitoring)

