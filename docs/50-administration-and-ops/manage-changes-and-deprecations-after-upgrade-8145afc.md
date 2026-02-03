<!-- loio8145afce5dca4b83adf24ef6d8db5ebb -->

# Manage Changes and Deprecations After Upgrade



Your system is upgraded regularly to deliver new features and improvements.

These changes may include changes or deprecation of apps, business catalogs, and business role templates.



<a name="loio8145afce5dca4b83adf24ef6d8db5ebb__section_App_Deprecation"/>

## Deprecation Process for Apps

If an app is outdated or its functionality is covered by a successor app, it is deprecated. This means that even though you can still use the app, SAP no longer recommends its use, and it will be deleted from the SAP Fiori launchpad in an upcoming release. There's a period of at least six months between the initial announcement of an app's deprecation and its deletion. The deprecated app may no longer be available by default on the SAP Fiori launchpad. In this case, you can find it in the app finder until it is deleted.

The deprecation of an app may require you to recheck the business catalogs that are assigned to your business roles. For more details about this and changes to restriction types, see *Manage Business Role Changes After Upgrade* in the *Related Information* section.



<a name="loio8145afce5dca4b83adf24ef6d8db5ebb__section_BC_Deprecation"/>

## Deprecation of Business Catalogs

Due to ongoing development of new features and new apps, you need to revise existing business catalogs with every system upgrade. This means that some business catalogs are deprecated and replaced by new ones, and you need to assign business roles and business users to these new business catalogs.

Rather than disappearing, deprecated business catalogs are identified as being obsolete, which allows you to identify them at a glance. For more information, see *How to Handle Deprecated Business Catalogs* in the *Related Information* section.



<a name="loio8145afce5dca4b83adf24ef6d8db5ebb__section_BR_ChangesAfterUpgrades"/>

## Business Role Changes after Upgrades

It is important for you to know how the release changes impact your productive business roles.

Business role changes often have the technical reason that new developments may require changes to existing applications, business catalogs, restriction types, and/or restriction fields. The affected business roles need to be adapted accordingly to ensure that existing apps behave consistently before and after the upgrade.

The following typical changes might occur:

-   Business catalogs were deprecated, or split, or have new dependencies so new business catalogs need to be assigned.

-   New apps were added to existing business catalogs.

-   New restriction types were added, removed, or access categories were changed.


For more information about change activation, see *Phase-In/Phase Out Status* in the *Related Information* section.

**Related Information**  


 <?sap-ot O2O class="- topic/link " href="e86e87fc7ac243ee8de3916dc12e9ee7.xml" text="" desc="" xtrc="link:1" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/8145afce5dca4b83adf24ef6d8db5ebb.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[Manage Business Role Changes After Upgrade](manage-business-role-changes-after-upgrade-2e2f201.md)

[How to Manage Deprecated Business Catalogs](how-to-manage-deprecated-business-catalogs-b727290.md "Deprecated business catalogs are deleted from the systems around 12 months after the deprecation announcement. Review upcoming changes and define the resulting IAM requirements together with authorization coordinators (key users or domain experts) from the line of businesses.")

