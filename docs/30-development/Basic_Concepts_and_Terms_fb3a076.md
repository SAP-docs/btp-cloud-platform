<!-- loiofb3a0763ea6b495dbc32517042d3ea62 -->

# Basic Concepts and Terms

To better understand how software lifecycle management with gCTS in the ABAP environment can be implemented, let’s start off with some basic concepts and terms.



<a name="loiofb3a0763ea6b495dbc32517042d3ea62__section_n35_g3c_xlb"/>

## Classical Git



### Git

Git is a distributed version-control system.

Distributed version control is a form in which development objects and all their versions and metadata are mirrored from a central place to every developer's computer. The developer can switch locally and offline between different versions and change all of them before updating the central originals later.



### Repository

A repository is a collection of objects, their directory structure, and metadata, for example, a historical record of changes in the repository, a set of commit objects, and a set of references to commit objects.

The central place that all objects are mirrored from and saved to, after having finished changes on a developer’s computer, is the so-called remote repository. Every developer’s computer holds a so-called local repository to work on.



### Branch

Git repository branches can be used to control the flow of changes through the test and production landscape. They are used to separate changes from each other, which shall or might not be delivered together \(i.e. development vs. correction, feature A vs. feature B\). A branch is created on the current state of another branch, the parent branch, and reflected by a new copy of all included objects, that is, the commit history of the parent branch. Depending on which branch is supposed to be changed, the corresponding copy is worked on.



### Pull

Pulling means getting the code that is currently in the remote repository into the local repository.



### Push

Pushing means getting the code that is currently in the local repository into the remote repository.



### Commit

A commit records the state and content changes of a file. It bundles multiple changes and saves it to the local repository. When you perform a git push, all commits are transferred to the remote git.



### Check Out

Checking out means that, if several branches are available, the one that is selected is added to the working tree. The working tree consists of the objects of the branch you are currently working on. It contains the state of these objects since they were last pulled and the changes that were made locally but are not yet pushed to the central remote repository. This checked out branch/working tree is what is displayed in the application to edit the objects.



<a name="loiofb3a0763ea6b495dbc32517042d3ea62__section_kwk_53c_xlb"/>

## ABAP and ABAP with gCTS



### ABAP System/Instance

SAP Business Technology Platform offers a service called ABAP System \(abap\). If you want to develop with ABAP in the cloud, you have to create an instance of that service, see [Create an ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f0163565eb554f009f990652ca41d1c6.html). This service instance provides the ABAP system that you are developing in. The terms ABAP system and ABAP instance can and are often used synonymously, however, we refer to the term ABAP system.



### Transport Request

A transport request records all the changes in your ABAP development system. Once a transport request is released, the changes are pushed into your central Git repository, to be more precise a branch of it, which is by default the main branch, in the cloud as a commit represented by a commit ID. During the import \(pull or checkout\), the delta of the Git repository branch content between the ABAP system and central Git repository is imported.

> ### Note:  
> Transport requests cannot be imported selectively into subsequent ABAP systems but as part of software component branches their changes were added to.



### Release

A release, for example with the format YYYY-<nn\>, is a set of changes that are tested successfully in your quality ABAP system\(s\) and imported into your production ABAP systems after a release decision. It is represented by a release branch in the Git repository. Once the release decision has been made, you have to create and pull \(import\) the new release branch into the production ABAP system.

