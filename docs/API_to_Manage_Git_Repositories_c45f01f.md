<!-- loioc45f01f6589f4eefafc34d3ad71e6eb5 -->

# API to Manage Git Repositories

You can use the `MANAGE_GIT_REPOSITORY` API to pull or clone Git repositories to ABAP environment systems and to create and checkout branches. The `MANAGE_GIT_REPOSITORY` API belongs to the Communication Scenario SAP\_COM\_0510.

> ### Note:  
> In ABAP environment, Git repositories are wrapped in software components. These are currently managed in the **Manage Software Components** app. The technical parameter `sc_name` used in this API needs to be the name of the Git repository on the ABAP environment system – the name of the software component.

> ### Note:  
> It is currently not possible to execute/trigger multiple actions \(clones/pulls/deletes\) in parallel on one system, regardless of the fact that the calls run asynchronously.

-   **[Cloning Git Repositories to an ABAP Environment System](Cloning_Git_Repositories_to_an_ABAP_Environment_System_0552763.md "")**  

-   **[Pulling Git Repositories to an ABAP Environment System](Pulling_Git_Repositories_to_an_ABAP_Environment_System_80a8d52.md "")**  

-   **[Working with Branches on a Git Repository](Working_with_Branches_on_a_Git_Repository_f571353.md "")**  


**Related Information**  


[Cloning Git Repositories to an ABAP Environment System](Cloning_Git_Repositories_to_an_ABAP_Environment_System_0552763.md "")

[Pulling Git Repositories to an ABAP Environment System](Pulling_Git_Repositories_to_an_ABAP_Environment_System_80a8d52.md "")

[Working with Branches on a Git Repository](Working_with_Branches_on_a_Git_Repository_f571353.md "")

