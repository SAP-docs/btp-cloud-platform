<!-- loio994c961dd666413e801df6c62cb727fc -->

# How to Configure Your Git Repository

Up until this point, the ABAP repositories in SAP BTP, ABAP environment were managed by the Manage Software Components Fiori app, which was the only interface where users could see the status of their remote repository. Bring Your Own Git \(BYOG\) allows users to connect their own Git repositories with the Manage Software Components app. In doing so, the user has a better overview of their own code, branches, and commits. However, the user is not allowed to make code changes in their remote Git repository and import these changes into the local SAP BTP, ABAP environment system instance, as this might violate any guidelines for ABAP cloud development. See [Supported ABAP Object Types](https://help.sap.com/docs/btp/sap-business-technology-platform/supported-abap-object-types?version=Cloud)



<a name="loio994c961dd666413e801df6c62cb727fc__section_zhh_vkt_c1c"/>

## Prerequisites

-   You have created a new repository with the preferred Git provider. The repository does not have any objects except for a readme file.

-   You have created a branch in your repository before cloning it.

-   Your repository is publicly accessible on the internet. Repositories hosted on a private company network are currently not supported.

-   You have administrative authorizations to push, pull and clone from the repository. Credentials must include a username and a password or token.

-   The developer users have administrative authorizations to the Manage Software Components app.

-   Production, development and/or test system instances are in the same global account.

-   The Git provider must trust a \(root\) certificate that is available in the SAP standard certificate trust list. Please check the current trust list [here](https://me.sap.com/notes/2801396) and compare it with your Git provider certificate.




<a name="loio994c961dd666413e801df6c62cb727fc__section_s24_hlt_c1c"/>

## Restrictions

-   Moving a BYOG software component from one global account to another is not supported.

-   Changing the URL of the remote repository after it has been linked to a software component is not allowed. After changing the URL, the repository can no longer be used.

-   It is important to distinguish between the user \(pusher\), whose credentials are entered during the clone process, and any other ABAP users \(committers\) that develop and release objects to be pushed to the remote repository. Although the committer will be noted in the commit history, the release and later the push will technically be performed using the credentials of the pusher. Therefore, it is recommended thtat the pusher does have push, pull and clone authorizations.




<a name="loio994c961dd666413e801df6c62cb727fc__section_cjt_44t_c1c"/>

## Procedure

Follow the steps below to create and manage a BYOG \(Bring Your Own Git\) repository in the Manage Software Components \(MSC\) app.



### Creating a remote repository

To create a BYOG repository, first create a new repository in your preferred Git provider.

Make sure to create a branch as well, as a default branch is necessary for the clone later on.

Next, copy the HTTPS link \(must end with `.git`\) to clone the repository in the Manage Software Components app.



### Create a Software Component and link the remote repository

In the Manage Software Components app, create a new software component and enter the URL from the previous step in the *Repository URL* field. Select the correct Git provider for your repository. The currently supported providers are GitHub, GitLab, Azure and Bitbucket. Choose *'Git \(others\)'* if none of the other options apply.

> ### Note:  
> When specifying the repository URL, please note that it must be case-insensitive and unique. This prevents multiple software components from being linked to a single or identical Git repository.

Add a name for your software component and choose the component type as development. Afterwards, click on *Create*. The software component is linked to the remote repository and is now ready to be cloned into the system.



### Cloning the Software Component

To clone the software component, click on the *Clone* button on the top right corner. A dialog will pop up:

Enter your user credentials that you would normally use to clone the repository, respectively a username and a password or token.

> ### Note:  
> Remember to enter the credentials of a user that has administrative rights to the repository and has authorizations to push and pull changes directly into the repository.

Select the radio button which describes your method of authentication, either a password or an OAuth token. Then click on *Next*. If the credentials are correct, the next step *Branch Selection*, will be displayed. Otherwise, re-enter the correct credentials before you move forward.

From the dropdown select the name of the branch you want to clone. Click on *Next*.

Select the repository role and import options. Choose *Latest* to import the latest commit.

Click on *Clone*. When the clone is finished, the status should be green.

After the clone is finished, notice that there will be a new commit *Modify repository layout* generated in the remote repository by commit author `noreply@example.com` and a newly added file. This file is necessary for pushing and pulling changes into the SAP system.

> ### Caution:  
> Do not edit or delete this file at any given time.



### Creating Branches

To create a branch, you should do so using the native interface \(e.g., Git interface\) of your git provider linked to your repository.

In the MSC app simply refresh the branch table to see the new branch. You can proceed as usual with the checkout.

> ### Note:  
> To be able to work with an alternative branch, you should create the branch after the initial clone. It is important that any new branches are created based on the *Modify repository layout* commit, as mentioned above. The file generated from this commit will allow import into the local system instance.



### Deleting a Software Component

Deleting a software component in the *Manage Software Components* app with the default settings will only delete the local representation of the software component in the ABAP system instance. Releasing transport requests will no longer be possible.

Selecting the *Unregister Repository* option will additionally unlink the remote repository from the software component and delete the software component completely from your global account.

Deleting the software component is an irreversible action. To delete the component, simply proceed by clicking *Delete* in the dialog. The remote Git repository will not be deleted, but it cannot be used again and be linked to new software components. This action is irreversible, therefore ensure to first delete the software component on all system instances where it is cloned.



### Creating and deleting tags

Tagging functionality is the same as in classic non-BYOG software components. To create a tag, go to the commit view of your selected branch. The created tag will also be visible on your remote repository. Deleting a tag will also delete the tag in the remote repository.

**Related Information**  


[Development in the ABAP Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/development-in-abap-environment?version=Cloud)

