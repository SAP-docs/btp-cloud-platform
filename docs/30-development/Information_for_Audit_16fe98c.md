<!-- loio16fe98cb8bae461ea70d57e9c44b7458 -->

# Information for Audit

The following information is relevant for audit:

-   Git repository: The creation of a Git repository branch creates a clone of the parent branch \(including all development objects in the branch\)
    -   During a pull or checkout, all objects that differ from the previously checked out commit and the pulled commit are imported into the ABAP system. Transport requests cannot be imported selectively into subsequent ABAP systems. Together with the information which branch and commit ID was pulled into an ABAP system, you can reproduce which version of an object was in an ABAP system at which point in time.
    -   The content of the Git repository with all its commits and objects is not directly accessible to users of an ABAP system. Only SAP employees have access to it for support purposes because the information is typically not required for an audit. In exceptional cases, the content of the Git repository can be requested via a service request.
-   In the Manage Software Components SAP Fiori app and in ABAP Development Tools \(ADT\), the following information is available for a regular audit.
    -   Manage Software Components app:
        -   Action history of imports \(pulls and branch checkouts\), which also contains an execution log and a transport log per import. As these two logs are only saved temporarily in the ABAP system, we recommend to save them to an excel if they are needed for error analysis or audit.
        -   Information on the last commit \(commit ID, commit message consisting of the transport request number and description, commit author and last commit timestamp\) for each branch
    -   ADT
        -   In the *Transport Organizer*, you can find the transport requests together with the piece list
        -   In the *Revision History*, you can find the history of an object

