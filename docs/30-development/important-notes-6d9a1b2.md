<!-- loio6d9a1b21b0714ddb8273161a496607b6 -->

# Important Notes

-   The creation of a Git repository branch creates a clone of the parent branch. If you create a branch immediately after the release decision, you have a codeline for further changes in parallel to the parent branch. Branches can be compared to a block chain which means you can only add new commits on top but not skip or overtake some.
-   In the different system setups, the production systems can either be provisioned once development starts or later on, when needed for the first time for the Go Live, which is the point in time, when the first release is used productively in the production system.
-   A classical 3-system setup comprising a development, quality assurance, and production system can be enhanced by pre-production systems, multiple test systems, etc. Test systems can be provisioned on demand \(temporary\) or permanently. In addition, any systems that are not permanently needed can be temporarily stopped and started later using [Manage System Hibernation](https://help.sap.com/docs/btp/sap-business-technology-platform/manage-system-hibernation?version=Cloud) in the Landscape Portal. This reduces the operating costs especially in larger system landscapes.
-   Keep your transports open in the development system until you are sure they will not jeopardize the validation of other features in testing systems.

-   New developments too large for a single transport should be released in disable state by toggling them in code or using a "branch-by-abstraction" pattern so that their delivery can be decoupled from their enablement. That means, you can enable them explicitly in test systems without fearing any damage by delivery to subsequent systems. Finally, they can be enabled in production by changing the default after successful testing. This approach can also serve as "circuit breaker" to easily turn off problematic features in emergency cases by transporting just the reverted default toggling.

-   If a released transport turns out to cause issues in testing, release a subsequent transport in development to remedy the issue.

-   If one or more released transports from development turnout to be a dead end, they can be reverted by pulling the last known good commit in the development system using Manage Software Components app and continue from there. Note however that this will revert all transports that were released after this last known good commit.


