<!-- loioe366d0d425584950ac8bc51b13083c25 -->

# Application Versions and Deployment Consistency

The SAP Cloud Deployment service follows the rules specified in the Semantic Versioning Specification \(Semver\) when comparing the versions of a deployed multitarget application \(MTA\) with the version that is to be deployed. If an MTA that is submitted for deployment has a version that is lower than or equal to an already deployed version of the same MTA, the deployment might fail if their is a conflict with the version rule specified in the deployment operation. The version rule is a parameter of the deployment process, which specifies which relationships to consider between the existing and the new version of an MTA before proceeding with the operation. The version rules supported by the deploy service are as follows:

-   *HIGHER* - Only MTAs with versions that are bigger than the version of the currently deployed MTA, are accepted for deployment.
-   *SAME\_HIGHER* - Only MTAs with versions that are higher than \(or the same as\) the version of the currently deployed MTA are accepted for deployment. This is the **default** setting for the version rule.
-   *ALL* - All versions are accepted for deployment.

