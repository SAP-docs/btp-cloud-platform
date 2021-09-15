<!-- loio13673461af2f4d739ec9b8784f25943e -->

# ABAP Environment Specifics

gCTS and the SAP Fiori app Manage Software Components provide a simplified git UI adapted to the possibilities of ABAP. This means:

-   There is a remote Git repository for each software component managed by SAP in the cloud. Using the SAP Fiori app Manage Software Components, a software component can be created from any ABAP system in the same global account. Alongside with the software component creation, the corresponding remote repository is created. Afterwards, the software component needs to be cloned and pulled into the ABAP system. With this step, a corresponding structure package is created in the ABAP system that acts as a local repository so that you can start developing \(software component = repository in gCTS\).
-   The creation of a Git repository branch is also performed in the Git repository. It does not matter in which ABAP system you create the branch. However, you have to check it out in each ABAP system where you want to use it, be it for development, testing or productive use.
-   In an ABAP system
    -   there is only one branch of a software component at a time
    -   all developers work on the same object versions
    -   an object can be edited by one developer at once
-   Pulling a software component does not simply copy object files, but, depending on the object type, also activates the objects, for example a data element, or even generates additional invisible objects in Eclipse, for example authorization artifacts for business catalogs used in business roles.
-   You have no merge functionality. If you pull the current branch while changes have been added from another ABAP system, all the changes in the ABAP system the branch is pulled into are discarded. Consequently, you should not work on the same branch in two different ABAP systems.
-   Before being able to pull a software component again or before checking out a different branch, you have to release all open transport requests. There is no way of saving them without releasing, like a git stash.
-   Releasing a transport request combines the git actions of committing and pushing. The Transport Request Id and description are displayed in the commit message.
-   A new branch is created remotely in the Git repository. This means that if the new branch shall be derived from the one currently checked out, changes in the ABAP system that are not yet committed and pushed by releasing the transport that contains these changes are not part of the new branch. The ***Last Commit Message*** text consists of the Transport Request ID and description, and helps you to ensure that the expected changes are part of the new branch. If you don’t want to hold back any new changes, you must release all open transports before creating a new branch.
-   If you need to discard changes, you have to do this manually. This can be done with the help of the *History* view in Eclipse, which offers a compare editor to revert to the last transported version. Afterwards, you have to remove all the discarded objects from their modifiable transport request in the *Transport Organizer* view.
-   Branches cannot be deleted or set to *obsolete*, therefore consumers have to be informed about a branch that they shall not use, for example, if you skipped a release branch that could not be finished in time.
-   Basic change logging using the “traditional” ABAP server capabilities is available in the development ABAP system: e.g. the *Revision History* for ABAP objects and the *Responsible* and *Last Changed By* contacts. However, if you de-provision the development ABAP system, this information is lost. The Git repository still stores the version \(see [Information for Audit](Information_for_Audit_16fe98c.md)\) and the person who released the transport request\(s\) but the information on the *Last Changed By* contact per object is only available in the development ABAP system.
-   You cannot work offline because you need access to the ABAP system.

