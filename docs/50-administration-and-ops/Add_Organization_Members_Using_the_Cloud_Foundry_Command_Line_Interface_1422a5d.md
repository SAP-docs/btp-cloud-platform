<!-- loio1422a5daa53d498f9270727135005884 -->

# Add Organization Members Using the Cloud Foundry Command Line Interface

You can use the Cloud Foundry Command Line Interface \(cf CLI\) to add organization members and assign roles to them.



<a name="loio1422a5daa53d498f9270727135005884__prereq_j4x_ytv_tz"/>

## Prerequisites

-   The Cloud Foundry environment is enabled. You can enable it in the Cloud Platform Cockpit. For more information, see [Create a Subaccount](Create_a_Subaccount_05280a1.md).

-   The Org Manager role for the org in question.

    > ### Note:  
    > You automatically have the Org Manager role in a subaccount that you created.

-   The e-mail addresses of the members that you want to add
-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md).




## Context

When you logged on with a platform user in a custom platform identity provider using the Cloud Foundry Command Line Interface, you can't use the ***--origin*** option. This isn't possible with the current version of the Cloud Foundry Command Line Interface \(cf CLI\). For more information, see [Supported Tools and Services When Using Custom Identity Providers for Platform Users\[Feature Set A\]](Supported_Tools_and_Services_When_Using_Custom_Identity_Providers_94ef515.md).



## Procedure

1.  Enter the following string, specifying the user name, the name of the organization, and the role:

    ```
    cf set-org-role USERNAME ORG ROLE 
    ```




<a name="loio1422a5daa53d498f9270727135005884__postreq_l4x_ytv_tz"/>

## Next Steps

To remove an org role from a user, enter the following string, specifying the user name, the name of the organization, and the role:

```
cf unset-org-role USERNAME ORG ROLE 
```

