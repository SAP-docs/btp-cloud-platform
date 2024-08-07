<!-- loio1eb6a099af3942fb99979f255218893b -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Delete Spaces

Delete spaces in your Cloud Foundry org using the SAP BTP cockpit.



<a name="loio1eb6a099af3942fb99979f255218893b__prereq_om2_ftm_qz"/>

## Prerequisites

-   You have the Org Manager role in the org from which you want to delete a space. For more information about roles and permissions, see [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).

-   You’ve ensured that the data in the space you’re going to delete is no longer needed.

    > ### Caution:  
    > Please be aware that you won’t be able to access your SAP HANA database system if you delete a space in an organization to which an SAP HANA database system is assigned.




<a name="loio1eb6a099af3942fb99979f255218893b__steps_jgs_mxw_z5"/>

## Procedure

1.  Navigate to *Cloud Foundry* \> *Spaces* in your Cloud Foundry subaccount and choose :wastebasket: on the tile of the space you want to delete.

2.  Confirm your change.


**Related Information**  


[Create Spaces Using the Cockpit](create-spaces-2f6ed22.md "Create spaces in your Cloud Foundry organization using the SAP BTP cockpit. In a space, you can deploy and maintain applications, and connect them to services.")

[Delete Spaces Using the Cloud Foundry Command Line Interface](delete-spaces-using-the-cloud-foundry-command-line-interface-13359c4.md "Use the cf delete-space command to delete spaces in your Cloud Foundry organization using the Cloud Foundry Command Line Interface (cf CLI).")

