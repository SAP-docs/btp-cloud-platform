<!-- loioff7cc1eb1d2f438b84877ab4ceeacfe1 -->

# Create a Branch





### Context

You want to create a new branch for your software component.



### Procedure

1.  Open the **Manage Software Components** Fiori app.
2.  Choose the software component you want to work on.
3.  Navigate to the section **Branching** and click on **Create**.
4.  Choose a name for your new branch and select the parent branch from the drop down menu.
5.  Confirm with **Create**.

    You can also create a branch based on a specific commit state. This referenced commit must be available in the current system, i.e. included in the currently selected branch. To do this, simply fill in the Commit ID in the Create New Branch popup. The commit ID can be provided in short or long format. Note that short commit IDs should only be used if the software component has already been pulled. Otherwise, the long ID needs to be used.

    > ### Note:  
    > When you delete a branch and recreate it with the same name, the creation will be denied with an error popup saying "Branch cannot be recreated". As a consequence, a branch name has to be unique once it has been used. Please choose another name in that case.

6.  Refresh the page. Your new branch has now been created and added to the table.

