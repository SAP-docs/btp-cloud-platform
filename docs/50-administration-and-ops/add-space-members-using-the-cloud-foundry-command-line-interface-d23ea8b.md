<!-- loiod23ea8bf91b14634a294ee93b8485479 -->

# Add Space Members Using the Cloud Foundry Command Line Interface

You can use the Cloud Foundry Command Line Interface \(cf CLI\) to add space members and assign roles to them.



<a name="loiod23ea8bf91b14634a294ee93b8485479__prereq_j4x_ytv_tz"/>

## Prerequisites

-   The Space Manager role for the space.
-   The e-mail addresses of the users that you want to add. The user must already exist in the connected identity provider. For more information, see [Managing Users and Assigning Role Collections](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md#loio94bb5935d4b64cff945c181fffa85282__section_l1j_mgj_rhb)
-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).




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

**Related Information**  


[Supported Tools and Services When Using Custom Identity Providers for Platform Users\[Feature Set A\]](supported-tools-and-services-when-using-custom-identity-providers-for-platform-users-feat-94ef515.md "Not all tools and services of SAP BTP support the use of custom identity providers with platform users. We provide a list of tools and services, which support this feature and any restrictions that apply.")

