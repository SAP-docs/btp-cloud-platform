<!-- loio100be99ac7064dfca43f0a0750d90d5b -->

# Register Systems for Pre-Upgrade

You have an upgrade planned for your systems. The *Register Systems for Pre-Upgrade* app allows you to select specific test- or development systems for an early upgrade: These systems will be upgraded two weeks before the official roll-out, giving you ample time to test your solution prior to the actual upgrade.



<a name="loio100be99ac7064dfca43f0a0750d90d5b__section_umt_xqz_1tb"/>

## Prerequisites

You need to have the “LandscapePortalAdmin” user role assigned to your user account to access this app.



<a name="loio100be99ac7064dfca43f0a0750d90d5b__section_vzk_yqz_1tb"/>

## Working in the Register Systems for Pre-Upgrade app

1.  Log into the Landscape Portal.

2.  Under *Systems*, click on the *Register Systems for Pre-Upgrade* tile to open the app.

3.  Select the system that you want to register for a pre-upgrade.

4.  Click the *Register System* button.

    > ### Note:  
    > The button is only active if the current date is within the registration period.

5.  Refresh the page by clicking on the *Refresh* button. The status of your system has changed from “Not registered for pre-upgrade” to “Registered for pre-upgrade”.

6.  If you change your mind and want to undo the registration of a system for pre-upgrade, simply select the system and click the *Un-Register System* button.


> ### Caution:  
> Make sure not to register your Add-on Build systems for pre-upgrade because product versions assembled on them cannot be installed into other systems until the target systems were updated as well. For production systems, this would be the regular update weeks later.

For more information, see [Pre-Upgrade Option for Release 2402](https://community.sap.com/t5/technology-blogs-by-sap/sap-btp-abap-environment-pre-upgrade-option-for-release-2402/ba-p/13573197).

