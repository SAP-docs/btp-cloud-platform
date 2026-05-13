<!-- loiob7272906d6484c03b246365bac1e3866 -->

# How to Manage Deprecated Business Catalogs

Deprecated business catalogs are deleted from the systems around 12 months after the deprecation announcement. Review upcoming changes and define the resulting IAM requirements together with authorization coordinators \(key users or domain experts\) from the line of businesses.



<a name="loiob7272906d6484c03b246365bac1e3866__HowToReviseBusinessCatalogs_context"/>

## Context

Due to ongoing development of new features and new apps, we need to periodically revise existing business catalogs. This means that some business catalogs are deprecated and replaced by one or more successors, and you need to assign business roles and business users to these new catalogs. Use the *Business Catalogs* app to identify and replace deprecated business catalogs in business roles **four weeks before the test system is upgraded**.

> ### Caution:  
> To prevent authorization issues, it’s important to replace deprecated business catalogs as soon as possible. SAP usually provides around 12 months between a deprecation announcement and the actual deletion, but this period can vary. It's best to replace deprecated business catalogs soon after the announcement. However, if you missed this or intentionally deferred it, you can still prepare before the release upgrade. Four weeks before an upgrade, review the preliminary information to identify which deprecated business catalogs are still in use and scheduled for removal. Make the necessary last-minute business catalog adjustments to mitigate authorization issues during the upgrade cycle and maintain uninterrupted access.



<a name="loiob7272906d6484c03b246365bac1e3866__HowToReviseBusinessCatalogs_steps"/>

## Procedure

1.  In the *Business Catalogs* app, adapt the filter settings to search for deprecated business catalogs that are used in a business role. In the *Status* search filter, select *Deprecated*. In the *Used in Business Roles* search filter, enter `>=1`.

2.  Focus on the business catalogs first that have been announced to be deprecated in the last release and that will now finally be removed. Select a business catalog to see its description, its deprecation release, the list of business roles it affects, and any successor\(s\). If more than one successor is assigned, confirm whether all successors are required. If any successors are not required, you need to manually delete them in the updated business roles **after the upgrade**. Identify the business roles that require the deprecated business catalog to be replaced and apply the update.

3.  Ensure that also the assignments of custom catalog extensions are changed.


