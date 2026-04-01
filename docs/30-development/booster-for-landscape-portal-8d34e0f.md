<!-- loio8d34e0f80489468088a99202a7fb4a60 -->

# Booster for Landscape Portal

One of the main use cases of the Landscape Portal is the building of product \(add-on\) versions. While the Landscape Portal hides much of the complexity involved in the process, it is required that a partner set up a suitable account model before starting.

The “Landscape Portal for SAP BTP ABAP Environment” booster is an automated process that automates the setup required to use the *Build Product Version* app in the Landscape Portal. Upon execution, it creates three new subaccounts corresponding to 00 Landscape Portal, 03 Build/Assemble and 04 Build/Test as described in [Set Up a Global Account for Development](set-up-a-global-account-for-development-9f2150f.md).

The three subaccounts fulfil the following roles:

-   **00 Landscape Portal**: This subaccount will host your Landscape Portal subscription, which can be used for a wide range of lifecycle management tasks.

-   **03 Build/Assemble**: This subaccount will host ABAP environment instances that are used to build new add-on product versions.

-   **04 Build/Test**: This subaccount will host ABAP environment instances that are used to test the installation of new add-on product versions.


It is recommended to use a transient build system during the add-on build process. This means that with every build that is triggered, a new ABAP environment instance is provisioned and, after the process is finished, it is deleted again. The booster also offers the possibility to provision such an instance during the booster execution, which can be later used during the build process.

You can start the booster from your global account for development. A wizard queries the user for the necessary data for the configuration of the subaccounts.



## Prerequisites

-   Your global account for development should be assigned the necessary entitlements:

    -   Landscape Portal \(1x standard\)
    -   Continuous Integration & Delivery \(1x standard\)
    -   abap \(2x standard, 2x abap\_compute\_unit, 4x hana\_compute\_unit\)
    -   Web Access for ABAP \(1x default\)




## Procedure

1.  Navigate to your global account for development in the BTP Cockpit.
2.  Navigate to the *Boosters* tab.
3.  Select the “Landscape Portal for SAP BTP ABAP Environment” booster and click *Start*.
4.  Configure the *00 Landscape Portal*subaccount.
    1.  Choose a subaccount name and subdomain.

5.  Configure the 03 Build/Assemble subaccount.
    1.  Choose a subaccount name and subdomain.
    2.  Choose a Cloud Foundry organization and space name.
    3.  Specify a technical user from your identity provider that shall be used for the provisioning of build systems.
    4.  Specify whether to provision a build system.
    5.  If a system shall be provisioned, choose a system ID.

6.  Configure the*04 Build/Test* subaccount.
    1.  Choose a subaccount name and subdomain.
    2.  Choose a Cloud Foundry organization and space name.
    3.  Specify a technical user from your identity provider that shall be used for the provisioning of installation test systems.

7.  Configure the user groups.
    1.  Specify a list of administrator users. These users will be assigned authorizations as described in *Results* down below.
    2.  Specify a list of viewer users. These users will be assigned authorizations as described in *Results* down below.


SAP ID Service is configured as the identity provider in all three subaccounts. If you wish to use different trust settings for different subaccounts, you can adjust the configuration as necessary after the booster execution.

> ### Note:  
> Currently, the Landscape Portal can only be used with SAP ID service as the application identity provider.



<a name="loio8d34e0f80489468088a99202a7fb4a60__section_xrb_pzg_fcc"/>

## Results

After successful execution, your global account for development should contain three new subaccounts with the following properties:

**00 Landscape Portal** 

-   Entitlements: Landscape Portal \(1x standard\), Continuous Integration and Delivery \(1x default\)

-   Subscriptions: Landscape Portal, Continuous Integration and Delivery

-   Administrator users have role collections *Subaccount Administrator*and *LandscapePortalAdminRoleCollection*.

-   Viewer users have role collections *Subaccount Viewer*.


**03 Build/Assemble**

-   Entitlements: abap \(1x standard, 2x abap\_compute\_unit, 2x hana\_compute\_unit\)

-   Subscriptions: -

-   Cloud Foundry is enabled

-   1 Cloud Foundry space is created

-   If configured, an ABAP environment instance is provisioned

-   Administrator users have role collection *Subaccount Administrator*, are *CF Org Managers* and *Space Managers* 

-   Viewer users have role collection *Subaccount Viewer*, are*CF Org Members* and *Space Developers* 

-   The specified technical user is granted the same authorizations as the viewer user group.


**04 Build/Test**

-   Entitlements: abap \(1x standard, 2x abap\_compute\_unit, 2x hana\_compute\_unit\), Web Access for ABAP \(1x default\)
-   Subscriptions: Web Access for ABAP
-   Cloud Foundry is enabled
-   1 Cloud Foundry space is created
-   Administrator users have role collection *Subaccount Administrator,* are *CF Org Managers* and *Space Managers*
-   Viewer users have role collection*Subaccount Viewer*, are *CF Org Members* and *Space Developers*
-   The specified technical user is granted the same authorizations as the viewer user group.

After executing the booster, you maintain the same technical user\(s\) in the *Credentials* section of the *Build Product Version* app.

You are then ready to configure one or more pipeline templates, see [Configure a Pipeline Template](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/5919ca97b3d54c758cf56dfb0887c306.html).

When configuring a template, reuse the resources created by the booster as follows:

For the "Prepare System" stage, reuse the subaccount/CF space from the **03 Build/Assemble** subaccount. If you provisioned a system during the booster execution, specify its instance name in the template so that it will be used.

For the "Integration Tests" stage, reuse the subaccount/CF space from the**04 Build/Test** subaccount. If you provisioned a system during the booster execution, specify its instance name in the template so that it will be used.

