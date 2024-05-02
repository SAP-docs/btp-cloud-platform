<!-- loio28f133ffbc7d472cbbd11d8780eb2943 -->

# Maintain Restrictions UI



<a name="loio28f133ffbc7d472cbbd11d8780eb2943__MaintainRestrictions"/>

## Maintain Restrictions

The *Maintain Restrictions UI* combines all restrictions of a restriction type of all access categories per business role in one place. It includes a main view showing all access categories and assigned restriction types and a detail view where you can change the assigned restrictions and values if required.

**Main View**

At the top of the main view, name and ID of the business role and the defined settings of the access categories are displayed. You can change these if required in the dropdown lists shown directly below. Underneath, the assigned restriction types are listed.

The *More Actions* area in the header includes the following options:

-   *Maintain Empty Restrictions* 

    When you are in the edit mode you can apply the selected field settings to all empty restrictions of a selected access category.

-   *Display Restrictions Overview*

    You can navigate to the *Restrictions Overview* from here and from the object view in both edit and display mode


The following colour scheme of the assigned restriction types helps you to organize your work:

-   Green: all restrictions of this type have been processed \(either maintained with values or set to *Not Maintained* intentionally\)

-   Orange: at least one field is still empty

    Please note that there is one exception to this colour scheme. If a restriction is not directly maintained for a specific access category but filled via inheritance from a higher access category it is shown as green even if it was not processed manually.


The restriction type you're currently working on is displayed under focus.

**Detail Area**

The detail area consists of the following three tabs:

-   Values

-   Description \(if available\)
-   Business Catalogs

You can carry out the following activities in the detail view:

-   Display all restrictions and values of the restriction type that is currently under focus.

-   Edit restrictions and values by clicking the pencil icon when you are in edit mode.

    -   Maintain the field settings *Restricted*, *Unrestricted Access* or *Not maintained* by selecting the radio buttons. The option *Maintained in Derived Role* is only availabe if the business role you're currently editing is a leading business role.

    -   Select and deselect values from the value help list

    -   Add number ranges if number ranges are supported

        Edit or paste multiple values in a comma-separated form in the text area

        > ### Note:  
        > Please note that any change in the text area will be processed once you leave the text area.

    -   Display an overview of all assigned values


    > ### Note:  
    > Mass maintenance is supported as well. You do this by selecting multiple restrictions and then clicking on one of the following buttons in the header of the restrictions list:
    > 
    > *Unrestricted Access*
    > 
    > *Not maintained*
    > 
    > *Maintained in derived role* \(this option is only available for leading business roles\)

-   Easily change the access category of a restriction by selecting the following radio buttons: *Write, Read, Value Help*, *Read, Value Help*, or*Value Help*.

-   Add other instances of this restriction type of the highest access category \(which is automatically selected\) by pressing the the *Add* button in the header of the restrictions list.

-   Define a restriction of the *General type* as leading by selecting the *Leading Restriction* checkbox.

    If required, you can define several general restrictions as leading. You can do this by selecting the required restrictions and then clicking *Leading*.

-   Remove restrictions if required by selecting the restrictions and clicking the the*Remove button* in the header of the restrictions list.

-   Hide fields you have set as *Unrestricted*. This makes it easier for you to gain an overview of all restrictions. You can do this clicking *Hide Unrestricted* in the very top right corner of the screen.


