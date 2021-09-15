<!-- loio1610eac123c04d07babaf89c47d82c91 -->

# Dynatrace Integration



<a name="loio1610eac123c04d07babaf89c47d82c91__context_p1l_rrd_p2b"/>

## Context

Dynatrace OneAgent is a Java agent that sends all captured monitoring data to your monitoring environment for analysis. The monitoring environment for Cloud Foundry environment resides in the Dynatrace cloud monitoring environment, see [How Do I Monitor Cloud Foundry Applications](https://www.dynatrace.com/support/help/cloud-platforms/cloud-foundry/how-do-i-monitor-cloud-foundry-applications/).



<a name="loio1610eac123c04d07babaf89c47d82c91__steps_w3f_srd_p2b"/>

## Procedure

1.  Obtain an environment ID and Token.

    Follow the steps described in the Generate PaaS Token section in [How Do I Monitor Cloud Foundry Applications](https://www.dynatrace.com/support/help/cloud-platforms/cloud-foundry/how-do-i-monitor-cloud-foundry-applications/).

2.  Create a user provided service.

    The service name contains the string dynatrace \(for example - *dynatrace-service*\) where *environmentid* and *apitoken* are the ones generated in the previous step. The *apiurl* should be set to *https://<YourDynatraceServerURL\>/e/<environmentid\>/api*.

    ```
    cf cups dynatrace-service -p "environmentid, apitoken, apiurl"
    ```

    For more details on how to create the user provided service refer to Option 1: Create a user-provided service in the Create a Dynatrace service in your Cloud Foundry Environment section in [How Do I Monitor Cloud Foundry Applications](https://www.dynatrace.com/support/help/cloud-platforms/cloud-foundry/how-do-i-monitor-cloud-foundry-applications/).

3.  Bind the application to the service instance created in the previous step, using the `manifest.yml` file.

    > ### Sample Code:  
    > manifest.yml
    > 
    > ```
    > ---
    > applications:
    > - name: myapp
    >   memory: 1G
    >   instances: 1
    >   services:
    >   - dynatrace-service
    > ```


