<!-- loioa2e5e29eca0b40da8d3a25e806329377 -->

# Create Spaces Using the Cloud Foundry Command Line Interface

Use the `cf create-space` command to create spaces in your Cloud Foundry organization using the Cloud Foundry Command Line Interface \(cf CLI\).



<a name="loioa2e5e29eca0b40da8d3a25e806329377__prereq_zt3_mzc_wbb"/>

## Prerequisites

-   \(Enterprise accounts only\) Create at least one subaccount and enable the Cloud Foundry environment in this subaccount. For more information, see [Create a Subaccount](create-a-subaccount-05280a1.md) and [Create Orgs](create-orgs-a9b1f54.md).

    > ### Note:  
    > In a trial account, the Cloud Foundry environment is automatically activated, and a first space named *dev* is created.

-   You have the Org Manager role in the organization in which you want to create a space. For more information about roles and permissions, see [https://docs.cloudfoundry.org/concepts/roles.html](https://docs.cloudfoundry.org/concepts/roles.html).
-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).




<a name="loioa2e5e29eca0b40da8d3a25e806329377__steps_mv3_csm_qz"/>

## Procedure

1.  Make sure that you are in the Cloud Foundry organization you want to add a space to.

    ```
    cf target -o ORG
    ```

    To get a list of your organizations, call `cf orgs`.

2.  Enter the following string, specifying a name for the new space, the name of the organization, and the quota you'd like to assign to it:

    ```
    cf create-space SPACE [-o ORG] [-q SPACE_QUOTA]
    ```

3.  \(Optional\) Set this space as target by executing: `***cf target -o ORG -s SPACE***`

    > ### Note:  
    > If you are assigned to only one Cloud Foundry organization and space, the system automatically targets you to the relevant Cloud Foundry organization and space when you log on.


**Related Information**  


[Delete Spaces Using the Cloud Foundry Command Line Interface](delete-spaces-using-the-cloud-foundry-command-line-interface-13359c4.md "Use the cf delete-space command to delete spaces in your Cloud Foundry organization using the Cloud Foundry Command Line Interface (cf CLI).")

