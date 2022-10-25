<!-- loiod1e42039cf284190858bcb2d16b35986 -->

# Assign Quota Plans to Spaces Using the Cloud Foundry Command Line Interface

You use the Cloud Foundry Command Line Interface to assign the quotas available in your global account to your subaccounts.



<a name="loiod1e42039cf284190858bcb2d16b35986__prereq_dl2_smb_pbb"/>

## Prerequisites

-   The Org Manager role for the org that contains the spaces to which you want to assign quotas.
-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).

-   A space quota plan. For more information, see [Create Space Quota Plans Using the Cloud Foundry Command Line Interface](create-space-quota-plans-using-the-cloud-foundry-command-line-interface-504fde9.md).



## Procedure

Open a command line and enter the following string:

```
cf set-space-quota SPACE_NAME SPACE_QUOTA_NAME
```

