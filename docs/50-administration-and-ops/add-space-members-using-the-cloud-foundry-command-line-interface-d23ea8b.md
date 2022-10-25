<!-- loiod23ea8bf91b14634a294ee93b8485479 -->

# Add Space Members Using the Cloud Foundry Command Line Interface

You can use the Cloud Foundry Command Line Interface \(cf CLI\) to add space members and assign roles to them.



<a name="loiod23ea8bf91b14634a294ee93b8485479__prereq_j4x_ytv_tz"/>

## Prerequisites

-   The Space Manager role for the space.
-   The users exist in a trusted platform identity provider.

    All users of Cloud Foundry UAA are stored in identity providers, either in the default or in a custom identity provider. UAA needs a copy of the user, sometimes called a shadow user. You assign the shadow user authorizations to access resources in UAA. When a user authenticates, UAA forwards the request to the identity provider.

    To specify which identity provider hosts the user, use the `--origin` option. For more information about finding the origin key, see the trust configuration documentation.

    For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).

-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).




<a name="loiod23ea8bf91b14634a294ee93b8485479__context_rqw_csz_kjb"/>

## Context

Space members are organization members who have specific roles in a space.

Org members can only be added by an Org Manager. This means that if you only have the Space Manager role, you can’t add space members that aren’t known to the org. To do that, you must first ask your Org Manager to add the users as org members with no roles. Once this is done, you can add them as space members following the steps below.

If you’re the Org Manager, you don’t need to first add the users as org members with no roles. Since you have the permissions necessary to add users to the org, when you add a new user as a space member, that user automatically becomes part of the org as well.



<a name="loiod23ea8bf91b14634a294ee93b8485479__steps_jrg_wt4_zl"/>

## Procedure

Enter the following string, specifying the user name, the name of the organization, the name of the space, and the role:

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


[Supported Tools and Services When Using Custom Identity Providers for Platform Users](supported-tools-and-services-when-using-custom-identity-providers-for-platform-users-94ef515.md "Not all tools and services of SAP BTP support the use of custom identity providers with platform users. We provide a list of tools and services, which support this feature and any restrictions that apply.")

