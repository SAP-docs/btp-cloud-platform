<!-- loio1e2615eb3d984861ae401ecba33db138 -->

# How to Delete an Employee



<a name="loio1e2615eb3d984861ae401ecba33db138__HowToDeleteEmployee_context"/>

## Context

If you delete an employee in *Maintain Employees*, it is not physically deleted from the database but is marked for archiving. This is contrary to the Fiori app *Maintain Business Users*, where the user is physically deleted.

An employee cannot be deleted immediately for business process reasons. It is also not possible to delete an employee in the Fiori app *Maintain Employees*, if the employee has a user assigned to it. In this case, you have to delete the user in the Fiori app *Maintain Business Users* first.

By default, all employees that are marked for archiving \(deleted\) are hidden. You can unhide them and also undo the mark \(deletion\) to reuse the employee. To do so, follow these steps:



<a name="loio1e2615eb3d984861ae401ecba33db138__HowToDeleteEmployee_steps"/>

## Procedure

1.  In the Fiori app *Maintain Employees*, choose *Filters*.

2.  Choose *More Filters*, select *Deleted* and choose *OK*.

3.  In the dropdown menu for *Deleted*, select *YES* or leave it blank, and choose *OK*.

4.  Search for a deleted employee.

    You may have to change the settings of the table to add the optional column *Deleted*.

5.  Choose a deleted employee to get to the *Display Employee* view.

6.  Choose *Undo Deletion*.

    The archiving flag will be removed from the employee.

    You can now use the employee again, for example, to create a new user for it.


