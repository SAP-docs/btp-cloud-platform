<!-- loio6b2f0bfc14cb47ef888f01784c92e1bf -->

# Work with Branches





### Context

To allow you to easily work on and switch between different versions of code, you can create branches, a copy of your existing code at a certain point in time, that you can check out and work on without changing your original code.

Find out how to work on branches below. To find out how to create, check out and switch between different branches, please refer to the following documentation pages.



### Procedure

1.  Upon opening the **Manage Software Components** app, you’ll see a list of all available software components. Select the one you would like to work on.

2.  Scroll down to *Branching* to see a list of all available branches for your component. The table shows you which branch the different branches originally derived from and which branch is currently checked out. The first branch is always named 'main'. The main branch will be created directly with the creation of the software component. If a branch was successfully created, it should directly be visible on all other system instances.

    The column *Delta* shows information about the currently active/checked-out branch. It displays how many commits the branch is behind the remote repository \(1 commit behind remote\) or just informs, that the branch is up to date \(No new commits\). This information is only valid for the currently active branch.

    If the branch is not active, the column value will be set to "Please checkout first". If the branch is multiple commits behind, the column value will be set to "X commits behind remote", where X is the number of new commits on the remote branch.

3.  Note that you need to clone the repository once before you can check out a branch. Clone the repository by clicking *Clone*.






### Merging of Branches - SAP Managed Software Components

> ### Note:  
> The merging of branches of SAP-managed software components is currently not supported.



### Merging of Branches - Customer-managed Software Components

It is possible to merge branches of a software component with Bring Your Own Git. However, this will have implications on the usability of your software component and is not officially supported using the Manage Software Components Fiori app. If you choose to merge branches of a customer-managed software component, please refer to the two options below:

**Option 1: Merging of Branches Using the Git Provider UI** 

You need to do a double maintenance for all the changes made to a branch that should be merged. This double maintenance needs to be performed on an SAP BTP ABAP environment, so that the changes exist in both the source branch and the target branch.

If the double maintenance has not been done correctly, and changes to the same object are present in both branches, Git might detect a merge conflict.

In case there are merge conflicts produced during the merge attempt of the two branches, please maintain your changes in both branches respectively. Once all changes are available in both branches, they can be merged on the remote repository.

It is essential not to resolve merge conflicts using a merge conflict resolver by your Git provider. If the individual line content was altered during the merge conflict resolution, this commit might not be able to get pulled into an ABAP environment.

**Option 2: Merging of Branches Using the Git Command Line Interface \(CLI\)** 

With this approach, it is mandatory to clone the remote Git repository to your local machine.

After the repository is cloned to your local machine, you need to perform the merge of the branches using either the `ours` or `theirs` strategy option. This approach ensures that the merging of branches does not alter individual line contents, butcontents but takes full objects from one side to the other instead. This way, the resulting commit from the merge is importable into an SAP BTP ABAP environment. As a reference, please take a look at the example below on how to perform a merge using the `theirs` strategy.

> ### Sample Code:  
> ```
> git clone <Repository_URL>
> cd <Repository_Name>
> git checkout <baseBranch>
> git merge -X theirs <mergeBranch>
> git push origin <baseBranch>
> 
> ```

> ### Note:  
> Currently, the merging of branches is not officially supported in the Manage Software Components Fiori app using customer-managed software components.

