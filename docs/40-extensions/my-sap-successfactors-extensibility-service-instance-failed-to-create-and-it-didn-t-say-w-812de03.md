<!-- loio812de0399a36405ea13476285363b70c -->

# My SAP SuccessFactors Extensibility Service Instance Failed to Create and It Didn't Say Why

My SAP SAP SuccessFactors extensibility service instance failed to create and it didn't say why.



<a name="loio812de0399a36405ea13476285363b70c__section_wrc_bjy_dcc"/>

## Issue/Symptom

You are trying to create an SAP SuccessFactors Extensibility service instance but the creation fails without an error message.



<a name="loio812de0399a36405ea13476285363b70c__section_l1b_kjy_dcc"/>

## Solution

This is what you can do:

-   You can use the Cloud Foundry command line interface to get the error message by executing the command:

```
cf service <service_instance_name>
```

Check for any error messages there. See [Managing Service Instances](https://docs.cloudfoundry.org/devguide/services/managing-services.html#get-details-for-a-particular-service-instance).

-   Can you reach the SAP SuccessFactors company? Check that the tenant is not in maintenance or being updated.
-   Check that there is not an already existing destination with the same name as the SAP SuccessFactors Extensibility service instance you are creating. When creating this service instance, a destination with the same name will be automatically created. See [Create an SAP SuccessFactors Extensibility Service Instance in the Cloud Foundry Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/8b774e4ca8be46a4830a021f727667ed.html?version=Cloud).

