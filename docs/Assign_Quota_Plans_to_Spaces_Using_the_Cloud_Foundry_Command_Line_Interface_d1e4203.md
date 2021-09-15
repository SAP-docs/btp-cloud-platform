<!-- loiod1e42039cf284190858bcb2d16b35986 -->

# Assign Quota Plans to Spaces Using the Cloud Foundry Command Line Interface

You use the Cloud Foundry Command Line Interface to assign the quotas available in your global account to your subaccounts.



<a name="loiod1e42039cf284190858bcb2d16b35986__prereq_dl2_smb_pbb"/>

## Prerequisites

-   The Org Manager role for the org that contains the spaces to which you want to assign quotas.
-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md).

-   A space quota plan. For more information, see [Create Space Quota Plans Using the Cloud Foundry Command Line Interface](Create_Space_Quota_Plans_Using_the_Cloud_Foundry_Command_Line_Interface_504fde9.md).



## Procedure

1.  Open a command line and enter the following string:

    ```
    cf set-space-quota SPACE_NAME SPACE_QUOTA_NAME
    ```


