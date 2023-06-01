<!-- loio01c96eda913b4550afc04ea3aa3087a7 -->

# Required Business Roles

Different actions require different roles as well. In the process description, the following role proposals are used:

-   System Administrator
    -   Creates ABAP systems in the SAP BTP cockpit 
    -   Needs authorization for space/organization management in the Cloud Foundry environment subaccount

-   User Administrator
    -   Maintains business roles and assigns users to them
    -   Needs authorization for business catalogs


        <table>
        <tr>
        <th valign="top">

        Catalog ID


        
        </th>
        <th valign="top">

        Catalog Description


        
        </th>
        <th valign="top">

        Needed For


        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
                `SAP_CORE_BC_IAM_UM`


        
        </td>
        <td valign="top">
        
                Identity and Access Management – User Management


        
        </td>
        <td valign="top">
        
                Creating and maintaining business users with *Maintain Business Users* app


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `SAP_CORE_BC_IAM_RM`


        
        </td>
        <td valign="top">
        
                Identity and Access Management –Role Management


        
        </td>
        <td valign="top">
        
                Maintaining business roles with *Maintain Business Roles* app


        
        </td>
        </tr>
        </table>
        

-   Release Manager

    -   Performs tasks that are executed centrally for a release, such as software component creation and import, making the release decision, approving corrections, creating and releasing transports etc.
    -   Needs authorization for business catalogs


    <table>
    <tr>
    <th valign="top">

    Catalog ID


    
    </th>
    <th valign="top">

    Catalog Description


    
    </th>
    <th valign="top">

    Needed For


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        `SAP_A4C_BC_MSCL_PC`


    
    </td>
    <td valign="top">
    
        Lifecycle Management - Software Components


    
    </td>
    <td valign="top">
    
        Creating and importing software components with *Manage Software Components* app


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        `SAP_A4C_BC_TRN_REL_PC`


    
    </td>
    <td valign="top">
    
        Development - Transport Release Management


    
    </td>
    <td valign="top">
    
        Releasing transport requests in ABAP Development Tools for Eclipse


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        SAP\_A4C\_BC\_DEV\_OBJ\_DIS\_PC


    
    </td>
    <td valign="top">
    
        Development – Development Objects Display


    
    </td>
    <td valign="top">
    
        Show development objects in transport organizer in ABAP Development Tool


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        `SAP_CORE_BC_IAM_UM`


    
    </td>
    <td valign="top">
    
        Identity and Access Management - User Management


    
    </td>
    <td valign="top">
    
        Un-/locking developers for corrections in correction ABAP systems with *Maintain Business Users* app


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        `SAP_CORE_BC_IAM_RA`


    
    </td>
    <td valign="top">
    
        Identity and Access Management – Role Assignment


    
    </td>
    <td valign="top">
    
        En-/disabling developers for corrections in correction ABAP systems by role assignment with *Maintain Business Users* app


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        `SAP_CORE_BC_BCT_TRN_REL_PC`


    
    </td>
    <td valign="top">
    
        Business Configuration - Transport Release Management


    
    </td>
    <td valign="top">
    
        Creating, editing, and releasing customizing transports with *Export Customizing Transports* app


    
    </td>
    </tr>
    </table>
    
-   Developer
    -   Develops the code and performs tests
    -   Needs authorization for business catalogs


        <table>
        <tr>
        <th valign="top">

        Catalog ID


        
        </th>
        <th valign="top">

        Catalog Description


        
        </th>
        <th valign="top">

        Needed For


        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
                `SAP_A4C_BC_DEV_PC`


        
        </td>
        <td valign="top">
        
                Development – ABAP Development Tools


        
        </td>
        <td valign="top">
        
                Developing in ADT for Eclipse


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `SAP_A4C_BC_TRN_MNG_PC`


        
        </td>
        <td valign="top">
        
                Development – Transport Management


        
        </td>
        <td valign="top">
        
                Creating transport requests in ADT for Eclipse


        
        </td>
        </tr>
        </table>
        

-   Tester
    -   Tests the software

        > ### Note:  
        > Depending on your organization, the tasks of this role can be performed by automatic test tools, developers, or dedicated persons that are responsible for executing manual tests.

    -   Needs authorizations for custom business catalogs created via IAM business catalogs for custom apps.

        > ### Caution:  
        > Do not assign catalog `SAP_CORE_BC_EXT_TST` \(Extensibility - Custom Apps and Services\) to a tester.
        > 
        > As this catalog is used to provide an easy test of custom apps or their underlying services in a development ABAP system only by adding them automatically to it during activation, real service tests with own catalogs might not be tested securely. In non-development systems, automatic authorization via business catalog`SAP_CORE_BC_EXT_TST` is not enabled, instead custom authorization is required.


-   Business Configuration Expert
    -   Maintains and tests business configuration


        <table>
        <tr>
        <th valign="top">

        Catalog ID


        
        </th>
        <th valign="top">

        Catalog Description


        
        </th>
        <th valign="top">

        Needed For


        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
                `SAP_CA_BC_IC_LND_PC`


        
        </td>
        <td valign="top">
        
                Customizing - Business Configuration


        
        </td>
        <td valign="top">
        
                General business configuration tasks, such as uploading business configuration or viewing the change log for business configuration


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `SAP_CORE_BC_BCT_TRN_MNG_PC`


        
        </td>
        <td valign="top">
        
                Business Configuration - Transport Management


        
        </td>
        <td valign="top">
        
                Creating and editing customizing transports


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                Application-specific catalog with configuration apps, for example `SAP_CA_BC_IC_LND_NUM_PC`


        
        </td>
        <td valign="top">
        
                Example: Number Range Management - Configuration


        
        </td>
        <td valign="top">
        
                Configuring number ranges


        
        </td>
        </tr>
        </table>
        


