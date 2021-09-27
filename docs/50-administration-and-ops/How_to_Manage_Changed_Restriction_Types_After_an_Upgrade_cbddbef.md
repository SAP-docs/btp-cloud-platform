<!-- loiocbddbef3c0eb430aaac634e0a2ba9a71 -->

# How to Manage Changed Restriction Types After an Upgrade



<a name="loiocbddbef3c0eb430aaac634e0a2ba9a71__HowToManageBusinessRoleChanges_context"/>

## Context

If you want to have transparency over all of the changes to restriction types after an upgrade, and you want to maintain the corresponding restrictions in your business roles, proceed as follows:



<a name="loiocbddbef3c0eb430aaac634e0a2ba9a71__HowToManageBusinessRoleChanges_steps"/>

## Procedure

1.  Select the *Manage Business Role Changes After Upgrade* tile on the SAP Fiori Launchpad to open the app. On the initial screen, view the*Restriction Types* area to get an overview of what has changed with the last upgrade. Filter for certain change types if required, for example if you only want to see the removed or the added restriction types.

2.  Download a csv file containing all recently changed restriction types if required.

3.  Click on the required restriction type to check how the changed restriction types affect your business roles. The business roles affected by the changes to this restriction type are displayed in a list. By clicking on the restriction type *Name* above the list, you can view a description of the restriction and a list of business catalogs in which this restriction type has been changed \(for example added or removed\). Please note that any derived roles will be filtered out from the list of the affected business roles to allow for synchronization with the master role.

4.  To find more information about the affected business roles or to make further changes, you can cross-navigate to the *Maintain Business Roles* app by clicking on the link listed in the *Business Role ID* column. When you click on the*Information* pushbutton next to the link, a list of all other changes that have affected the business role after the upgrade and that might be relevant for you as well is displayed.

5.  To make the necessary changes in your business roles, select the required business role and click *Maintain \(Write, Read, Value Help\) Restrictions*. Restrictions can be mass-maintained for multiple business roles if the roles have the same access categories. If they have different access categories, the pushbutton is disabled. On the *Maintain Restrictions* screen, you can also view the related business catalogs and the business roles selected on the previous screen. You see the restriction fields of the restriction you are currently maintaining. To see other restrictions these business roles might include, click the glasses icon \(*Display Restrictions*\) to cross-navigate to the *Maintain Business Roles* app.

6.  Click the *Edit* icon and assign the required values or ranges. Click *Not maintained*if you want to make clear that you have not maintained a field on purpose and not by accident.

7.  Click *Apply*.




<a name="loiocbddbef3c0eb430aaac634e0a2ba9a71__result_sbz_gvj_vlb"/>

## Results

The system displays the results of the update in a pop-up. If the update has been successful, a green icon is visible. If issues occurred, a warning message is displayed.

When you close the pop-up, you will be directed to the main view again.

