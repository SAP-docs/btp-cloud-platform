<!-- loioea47e09911c24f658e5f111d21729ffd -->

# Branching



> ### Note:  
> Keep in mind that there are some restrictions for using branches in your development processes, for example the merging of branches is not supported and has to be done manually. See [ABAP Environment Specifics](abap-environment-specifics-1367346.md).

Development in the ABAP environment is done in software components. For each software component, different branches can be created that include a different list of commits. For each system, only one branch can be active at a time. Branches are used to separate changes from each other that shall or might not be delivered together \(development vs. correction\).

To separate development of new features from the development of bug fixes for the active version of a software component, you can use branches for different purposes:

-   **Main Branch**: Implementation of new planned features that are to be delivered in the future \(development codeline\)
-   **Maintenance Branch**: Implementation of unplanned bug fixes for the active version of a software component that is deployed to customer systems \(maintenance codeline\)


The main branch is the default branch of each software component and therefore already exists when the software component is created. This branch is not deleted throughout delivery of different software component versions.

A maintenance branch should be created for each support package level of a software component and is named accordingly, for example v1.1.0 for support package level 1 in release 1. Maintenance branches can be deleted once the successor support package level is the currently deployed support package level in customer systems.

> ### Recommendation:  
> Create a new maintenance branch with each new support package level, and thus with each new AOI and CSP package delivered for a software component.

For the first release, the main branch of software components is used to create a maintenance branch for the add-on build process. In subsequent versions, the development and correction code line are separated by using the main branch and the maintenance branch. See [Use Case 2: One Development and Correction Codeline in a 5-System Landscape](use-case-2-one-development-and-correction-codeline-in-a-5-system-landscape-4e53874.md).

All corrections to a software component based on a certain support package level are released in the corresponding maintenance branch and need to be maintained as new commits in the main branch \(double maintenance\). See [Double Maintenance of Corrections into Development](double-maintenance-of-corrections-into-development-1241b14.md).

For each ABAP system, only one branch can be active at a time. Therefore, in development system DEV and test system TST, the main branch of a software component is checked out. Whereas in correction system COR and quality assurance system QAS, the currently relevant maintenance branch is checked out.

