<!-- loio504fde98e8bb4bff889e49d0b2f6c28b -->

# Create Space Quota Plans Using the Cloud Foundry Command Line Interface

You can use the Cloud Foundry Command Line Interface to create space quota plans.



<a name="loio504fde98e8bb4bff889e49d0b2f6c28b__prereq_qht_cmb_pbb"/>

## Prerequisites

-   The Org Manager role for the org that contains the spaces to which you want to assign quotas.
-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).




## Procedure

Open a command line and enter the following string, replacing `QUOTA` with the name for your space quota plan:

```
cf create-space-quota QUOTA [-i INSTANCE_MEMORY] [-m MEMORY] [-r ROUTES] [-s SERVICE_INSTANCES] [--allow-paid-service-plan | --disallow-paid-service-plans]
```

Specify the following parameters:

-   `-i`: Maximum amount of memory an application instance can have \(`-1` represents an unlimited amount\)

-   `-m`: Total amount of memory a space can have
-   `-r`: Total number of routes
-   `-s`: Total number of service instances
-   `--allow-paid-service-plans`: Can provision instances of paid service plans
-    `--disallow-paid-service-plans`: Can not provision instances of paid service plans

