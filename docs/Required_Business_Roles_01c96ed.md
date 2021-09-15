<!-- loio01c96eda913b4550afc04ea3aa3087a7 -->

# Required Business Roles

Different actions require different roles as well. In the process description, the following role proposals are used:

-   System Administrator
    -   Creates ABAP systems in the SAP BTP Cockpit
    -   Needs authorization for space/organization management in the Cloud Foundry environment subaccount
-   User Administrator
    -   Maintains business roles and assigns users to them
    -   Needs authorization for business catalogs


        <table>
        <tr>
        <th>

        Catalog ID


        
        </th>
        <th>

        Catalog Description


        
        </th>
        <th>

        Needed For


        
        </th>
        </tr>
        <tr>
        <td>

        `SAP_CORE_BC_IAM_UM`


        
        </td>
        <td>

        Identity and Access Management – User Management


        
        </td>
        <td>

        Creating and maintaining business users with Manage Business Users app


        
        </td>
        </tr>
        <tr>
        <td>

        `SAP_CORE_BC_IAM_RM`


        
        </td>
        <td>

        Identity and Access Management –Role Management


        
        </td>
        <td>

        Maintaining business roles with Manage Business Roles app


        
        </td>
        </tr>
        </table>
        
-   Release Manager

    -   Performs tasks that are executed centrally for a release, such as software component creation and import, making the release decision, approving corrections, creating and releasing transports etc.
    -   Needs authorization for business catalogs

    <table>
    <tr>
    <th>

    Catalog ID


    
    </th>
    <th>

    Catalog Description


    
    </th>
    <th>

    Needed For


    
    </th>
    </tr>
    <tr>
    <td>

    `SAP_A4C_BC_MSCL_PC`


    
    </td>
    <td>

    Lifecycle Management - Software Components


    
    </td>
    <td>

    Creating and importing software components with Manage Software Components app


    
    </td>
    </tr>
    <tr>
    <td>

    `SAP_A4C_BC_TRN_REL_PC`


    
    </td>
    <td>

    Development - Transport Release Management


    
    </td>
    <td>

    Releasing transport requests in Eclipse with ADT


    
    </td>
    </tr>
    <tr>
    <td>

    `SAP_CORE_BC_IAM_UM`


    
    </td>
    <td>

    Identity and Access Management - User Management


    
    </td>
    <td>

    Un-/locking developers for corrections in correction ABAP systems with Manage Business Users app


    
    </td>
    </tr>
    <tr>
    <td>

    `SAP_CORE_BC_IAM_RA`


    
    </td>
    <td>

    Identity and Access Management – Role Assignment


    
    </td>
    <td>

    En-/disabling developers for corrections in correction ABAP Systems by role assignment with Manage Business Users app


    
    </td>
    </tr>
    </table>
    
-   Developer
    -   Develops the code and performs tests
    -   Needs authorization for business catalogs


        <table>
        <tr>
        <th>

        Catalog ID


        
        </th>
        <th>

        Catalog Description


        
        </th>
        <th>

        Needed For


        
        </th>
        </tr>
        <tr>
        <td>

        `SAP_A4C_BC_DEV_PC`


        
        </td>
        <td>

        Development – ABAP Development Tools


        
        </td>
        <td>

        Developing in ADT for Eclipse


        
        </td>
        </tr>
        <tr>
        <td>

        `SAP_A4C_BC_TRN_MNG_PC`


        
        </td>
        <td>

        Development – Transport Management


        
        </td>
        <td>

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


