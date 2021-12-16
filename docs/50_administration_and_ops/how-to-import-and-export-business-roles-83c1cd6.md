<!-- loio83c1cd62666f48c68d93f2fdeae1ae95 -->

# How to Import and Export Business Roles



<a name="loio83c1cd62666f48c68d93f2fdeae1ae95__HowToImportExportBusinessRoles_context"/>

## Context

You can use the *Export Software Collection* app and the *Import Collection* app to transport business roles from your quality system to your productive system.

We recommend that you do not change the business role after it has been transported. It should not be changed locally but only updated with a new transport.

Local changes should only be carried out in urgent cases. Please note that local changes are not possible at all if Adaptation Transport Organizer \(ATO\) is configured, and you're working in a productive system. In this case, the *Manage Launchpad Space* pushbutton in the *Maintain Business Roles* app is disabled.

> ### Note:  
> -   Once you have transported a business role, no change documents will be written for this business role in the productive system. Change documents for transported business roles are only available in the quality system.
> 
> -   If you transport a derived business role, the leading business role and all other derived business roles need to be added as dependencies to the transport request as well.
> 
>     If you transport a leading business role, all derived business roles need to be added as dependencies to the transport request as well.



<a name="loio83c1cd62666f48c68d93f2fdeae1ae95__HowToImportExportBusinessRoles_steps"/>

## Procedure

1.  In your quality system, open the*Export Software Collection* app.

2.  Create a software collection and give it a unique name.

3.  Click *Add Items* and select the business roles you want to export.

4.  Click *Export*to export the required business roles to your productive system. You can view in the log if the export has been finished.

5.  In your productive system, open the *Import Collection* app.

6.  Select the previously exported software collection and click *Import* to import the required business roles to your productive system. You can view in the log if the import has been finished.


**Related Information**  






[How to Create Leading and Derived Business Roles](how-to-create-leading-and-derived-business-roles-9b09af6.md "")



