<!-- loio1422a5daa53d498f9270727135005884 -->

# Add Organization Members Using the Cloud Foundry Command Line Interface

You can use the Cloud Foundry Command Line Interface \(cf CLI\) to add organization members and assign roles to them.



<a name="loio1422a5daa53d498f9270727135005884__prereq_j4x_ytv_tz"/>

## Prerequisites

-   The Cloud Foundry environment is enabled.

    Enable it in the SAP BTP cockpit. For more information, see [Create a Subaccount](create-a-subaccount-05280a1.md).

-   The Org Manager role for the org in question.

    > ### Note:  
    > You automatically have the Org Manager role in an org that you created.

-   The user exists in the UAA.

    All users are stored in identity providers, either in the default or in a custom identity provider. Cloud Foundry needs a copy of the user, sometimes called a shadow user. To create the shadow user, choose one of the following options:

    -   The user has been added from the cockpit.

        For more information, see [Add Org Members](add-org-members-a4eeaf1.md).

    -   The user has already logged on to the Cloud Foundry environment.

        For example: `cf login -a https://api.cf.eu20.hana.ondemand.com`

        > ### Note:  
        > The landscape the user logs on to must be the same as the landscape where the subaccount is located. See the overview page of your subaccount for the API endpoint.


-   You have the e-mail addresses of the members that you want to add.

    The user must already exist in the connected identity provider. For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).

-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).




<a name="loio1422a5daa53d498f9270727135005884__context_oyv_xpy_3sb"/>

## Context

This task is meant for the `OrgManager` and `OrgAuditor` roles. To add members with the `OrgUser` role, follow the procedure described in [Add Space Members Using the Cloud Foundry Command Line Interface](add-space-members-using-the-cloud-foundry-command-line-interface-d23ea8b.md).



## Procedure

Enter the following command, specifying the user name, the name of the organization, and the role:

```
cf set-org-role <USERNAME> <ORG> <ROLE>
```

```
cf set-org-role julie.armstrong@example.com account_subaccount-47v2w8dj OrgAuditor
```



<a name="loio1422a5daa53d498f9270727135005884__postreq_l4x_ytv_tz"/>

## Next Steps

To remove an org role from a user, enter the following string, specifying the user name, the name of the organization, and the role:

```
cf unset-org-role <USERNAME> <ORG> <ROLE> 
```

**Related Information**  


[Supported Tools and Services When Using Custom Identity Providers for Platform Users](supported-tools-and-services-when-using-custom-identity-providers-for-platform-users-94ef515.md "Not all tools and services of SAP BTP support the use of custom identity providers with platform users. We provide a list of tools and services, which support this feature and any restrictions that apply.")

[About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md "Roles determine which features users can view and access, and which actions they can initiate.")

[Managing Org Members Using the Cockpit](managing-org-members-b792066.md "Learn how to add, edit, and delete org members in the SAP BTP cockpit.")

