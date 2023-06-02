<!-- loio1610eac123c04d07babaf89c47d82c91 -->

# Dynatrace Integration



<a name="loio1610eac123c04d07babaf89c47d82c91__context_p1l_rrd_p2b"/>

## Context

Dynatrace OneAgent is a Java agent that sends all captured monitoring data to your Dynatrace monitoring environment for analysis.



<a name="loio1610eac123c04d07babaf89c47d82c91__steps_w3f_srd_p2b"/>

## Procedure

1.  Obtain an environment ID and an API token. To do that, follow the steps described on page: [Deploy OneAgent on SAP BTP Cloud Foundry Runtime](https://www.dynatrace.com/support/help/setup-and-configuration/setup-on-container-platforms/cloud-foundry/deploy-oneagent-on-sap-cloud-platform-for-application-only-monitoring#deploy-oneagent-on-sap-btp-cloud-foundry-runtime)

2.  Create a user-provided service.

    The service name should contain the string "dynatrace" \(for example, **dynatraceservice**\). The `environmentid` and `apitoken` parameters have been generated in the previous step. You also need to set up the API URL, which depends on the Dynatrace type you want to integrate:

    -   **SaaS Dynatrace**

        ```
        "apiurl": "https://<environmentid>.live.dynatrace.com/api"
        ```

    -   **Managed Dynatrace**

        ```
        "apiurl": "https://<your_domain>/e/<environmentid>/api"
        ```


    Then, in cf CLI execute:

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


4. Push the application to Cloud Foundry with the updated manifest. Once the application receives web traffic, monitoring data will show up in Dynatrace.
