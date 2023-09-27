<!-- loio6b2f0bfc14cb47ef888f01784c92e1bf -->

# How to Work with Branches



<a name="loio6b2f0bfc14cb47ef888f01784c92e1bf__section_cp5_dlg_lkb"/>

## Context:

To allow you to easily work on and switch between different versions of code, you can create branches, a copy of your existing code at a certain point in time, that you can check out and work on without changing your original code.

Find out how to create, check out and switch between different branches:



<a name="loio6b2f0bfc14cb47ef888f01784c92e1bf__section_k2l_glg_lkb"/>

## Procedure:

1.  Upon opening the **Manage Software Components** app, you’ll see a list of all available software components. Select the one you would like to work on.

2.  Scroll down to *Branching* to see a list of all available branches for your component. The table shows you which branch the different branches originally derived from and which branch is currently checked out. The first branch is always named 'main'. The main branch will be created directly with the creation of the software component. If a branch was successfully created, it should directly be visible on all other system instances.

    The column *Delta* shows information about the currently active/checked-out branch. It displays how many commits the branch is behind the remote repository \(1 commit behind remote\) or just informs, that the branch is up to date \(No new commits\). This information is only valid for the currently active branch.

    If the branch is not active, the column value will be set to "Please checkout first". If the branch is multiple commits behind, the column value will be set to "X commits behind remote", where X is the number of new commits on the remote branch.

3.  Note that you need to clone the repository once before you can check out a branch. Clone the repository by clicking *Clone*.

4.  To create a new branch, click on *Create*. Choose a name for your new branch and select the parent branch from the drop down menu. Confirm with *Create*.

    You can also create a branch based on a specific commit state. This referenced commit must be available in the current system, i.e. included in the currently selected branch. To do this, simply fill in the *Commit ID* in the *Create New Branch* popup. The commit ID can be provided in short or long format. Note that short commit IDs should only be used if the software component has already been pulled. Otherwise, the long ID needs to be used.

    > ### Note:  
    > When you delete a branch and recreate it with the same name, the creation will be denied with an error popup saying "Branch cannot be recreated". As a consequence, a branch name has to be unique once it has been used. Please choose another name in that case.

5.  Refresh the page. Your new branch has now been created and added to the table.

6.  If you want to work on the new branch, you can check it out by selecting it and clicking *Checkout*. All objects in the target branch will overwrite existing objects in the system without further notice. It is therefore important to ensure that all open transport requests in the current branch are released before switching to a new branch.

    A new checkout is not possible while a checkout or pull is already in progress.

7.  The branch selected for checkout is now available in the system.

8.  You can easily switch between all your different branches by using the *Checkout* button.


> ### Note:  
> **Branch Deletion**:
> 
> While it is possible to delete branches, please consider the possible negative effects of branch deletion, like losing the commit history.
> 
> Please make sure that the branch you are deleting is no longer in use on other systems. If you delete the branch while it's in use in other systems, this code can no longer be released there, even if there are open transport requests.
> 
> The branch will be deleted locally and also on the remote repository. After the branch deletion, a pull of this branch is no longer possible on all system instances.

> ### Note:  
> The merging of branches is currently not supported.

> ### Note:  
> Note that a maximum of 25 branches can be created per software component.

