<!-- loio6b2f0bfc14cb47ef888f01784c92e1bf -->

# How to Work with Branches



<a name="loio6b2f0bfc14cb47ef888f01784c92e1bf__section_cp5_dlg_lkb"/>

## Context:

To allow you to easily work on and switch between different versions of code, you can create branches, a copy of your existing code at a certain point in time, that you can check out and work on without changing your original code.

Find out how to create, check out and switch between different branches:



<a name="loio6b2f0bfc14cb47ef888f01784c92e1bf__section_k2l_glg_lkb"/>

## Procedure:

1.  Upon opening the **Manage Software Components** app, you’ll see a list of all available software components. Select the one you would like to work on.

2.  Scroll down to *Branching* to see a list of all available branches for your component. The table shows you which branch the different branches originally derived from and which branch is currently checked out. The first branch is always named 'main'. It is created when releasing a transport request for this software component using ABAP Development Tools. In the initial \(development\) system, the 'main' branch will not be visible until you've released a transport request. If you pull the software component on your test or production system afterwards, you'll see all branches even before you've released an ABAP transport request.

3.  Note that you need to pull the repository once before you can check out a branch. Pull the repository by clicking *Pull*.

4.  To create a new branch, select the branch that you want to create it from and click *+*. Choose a name for your new branch and confirm with *Create*.

    > ### Note:  
    > A new branch initially has the same state as the branch it was created from.

    You can also create a branch based on a specific commit state. This referenced commit must be available in the current system, i.e. included in the currently active branch. To do this, simply fill in the *Commit ID* in the *Create New Branch* popup. The commit ID can be provided in short or long format. Note that short commit IDs should only be used if the software component has already been cloned. Otherwise, the long ID needs to be used.

5.  Refresh the page. Your new branch has now been created and added to the table.

6.  If you want to work on the new branch, you can check it out by selecting it and clicking *Checkout*. All objects in the target branch will overwrite existing objects in the system without further notice. It is therefore important to ensure that all open transport requests in the current branch are released before switching to a new branch.

    A new checkout is not possible while a checkout or pull is already in progress.

7.  The branch selected for checkout is now available in the system.

8.  You can easily switch between all your different branches by using the *Checkout* button.


> ### Note:  
> **Branch Deletion**:
> 
> While it is possible to delete branches, please consider the possible negative effects of branch deletion, like losing the commit history.

> ### Note:  
> The merging of branches is currently not supported.

> ### Note:  
> Note that a maximum of 25 branches can be created per software component.

-   **[How to Tag Commits](How_to_Tag_Commits_10139f4.md "")**  


