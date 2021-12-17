<!-- loiod23ea8bf91b14634a294ee93b8485479 -->

# Add Space Members Using the Cloud Foundry Command Line Interface

You can use the Cloud Foundry Command Line Interface \(cf CLI\) to add space members and assign roles to them.



<a name="loiod23ea8bf91b14634a294ee93b8485479__prereq_j4x_ytv_tz"/>

## Prerequisites

-   The Space Manager role for the space
-   The e-mail addresses of the users that you want to add
-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).




## Context

When you logged on with a platform user in a custom platform identity provider using the Cloud Foundry Command Line Interface, you can't use the ***--origin*** option. This isn't possible with the current version of the Cloud Foundry Command Line Interface \(cf CLI\). For more information, see [Supported Tools and Services When Using Custom Identity Providers for Platform Users\[Feature Set A\]](Supported_Tools_and_Services_When_Using_Custom_Identity_Providers_94ef515.md).



<a name="loiod23ea8bf91b14634a294ee93b8485479__steps_jrg_wt4_zl"/>

## Procedure

1.  Enter the following string, specifying the user name, the name of the organization, the name of the space, and the role:

    ```
    cf set-space-role USERNAME ORG SPACE ROLE 
    ```




<a name="loiod23ea8bf91b14634a294ee93b8485479__postreq_l4x_ytv_tz"/>

## Next Steps

To remove a space role from a user, enter the following string, specifying the user name, the name of the organization, the name of the space, and the role:

```
cf unset-space-role USERNAME ORG SPACE ROLE 
```

