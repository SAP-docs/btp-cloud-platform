<!-- loiof9e18605e01a485098fe5478649bd474 -->

# Troubleshoot Custom Apps

After developing or releasing an application to a test or productive system, you might need to troubleshoot your application, for example to debug your business logic, display data of your application, and to analyze short dumps as well as logs and traces.



<a name="loiof9e18605e01a485098fe5478649bd474__section_ihz_1z4_zqb"/>

## Prerequisites

As an administrator, assign business role `Application Support Engineer - Development Support` to a business user. With this role, you enable business users to troubleshoot applications. In addition to this business role, you might need to assign the business role of the application to be analyzed to the business user.



<a name="loiof9e18605e01a485098fe5478649bd474__section_uny_gz4_zqb"/>

## Business Role Template Application Support Engineer - Development Support

Business role template `Application Support Engineer - Development Support` \(`BR_APPL_SUP_ENG_DEV_SUP`\) contains all the business catalogs that are required for troubleshooting activities, such as:

-   Debugging capability
-   Running the data preview
-   Executing classrun
-   Accessing Feed Reader
-   SQL Trace Analysis & SQL Explain Analysis capability



### Business Catalogs

Business role template `Application Support Engineer - Development Support` includes the following business catalogs:


<table>
<tr>
<th valign="top">

Business Catalog

</th>
<th valign="top">

Authorization

</th>
</tr>
<tr>
<td valign="top">

Development Support - Data Preview - Business Data \(`SAP_A4C_BC_DAT_PRV_DFT_PC`\)

</td>
<td valign="top">

This business catalog enables you to use the data preview in ABAP Development Tools for objects that are considered to contain business data, such as:

-   CDS views in language version 5
-   Client-dependent tables in language version 5 with delivery class A and L
-   Data of CDS views that can be viewed with or without application of the DCL



</td>
</tr>
<tr>
<td valign="top">

Development Support - Data Preview - Cross-Client and Customizing Data \(`SAP_A4C_BC_DAT_PRV_RDO_PC`\)

</td>
<td valign="top">

This business catalog enables you to use the data preview in ABAP Development Tools for objects that are considered to contain customizing and cross-client data, such as:

-   Client-independent tables in language version 5 with delivery class A and L
-   Tables in language version 5 with delivery class S, E, and W \(metadata\)
-   Tables in language version 5 with delivery class C and G \(customizing\)



</td>
</tr>
<tr>
<td valign="top">

Development - Class Runner Execution \(`SAP_A4C_BC_DEV_CLA_RUN_PC`\)

</td>
<td valign="top">

This business catalog enables you to execute class runners in ABAP Development Tools.

</td>
</tr>
<tr>
<td valign="top">

Development - Data Preview - Released Objects \(`SAP_A4C_BC_DEV_DAT_PRV_PC`\)

</td>
<td valign="top">

This business catalog enables you to use the data preview in ABAP Development Tools for objects that are released for language version 5:

-   SAP-delivered CDS views
-   CDS Views that are released for usage outside of their own software component
-   Data of CDS views that can be viewed with or without application of the DCL



</td>
</tr>
<tr>
<td valign="top">

Development - Development Objects Display \(`SAP_A4C_BC_DEV_OBJ_DIS_PC`\)

</td>
<td valign="top">

This business catalog enables you to sign in to ABAP Development Tools and view development objects with read-only authorization.

</td>
</tr>
<tr>
<td valign="top">

Development - Analysis and Support \(`SAP_A4C_BC_DEV_SUP_PC`\)

</td>
<td valign="top">

This business catalog gives you access to troubleshooting tools such as logs, traces, and the debugger.

Business user assigned to the business role `Development` or any kind of source code changes are not permitted. Nevertheless, business users can execute the class runner in a test or productive system, unless this is not restricted by the administrator.

</td>
</tr>
</table>



<a name="loiof9e18605e01a485098fe5478649bd474__section_ul2_g3q_zqb"/>

## Connect to the System

As the Application Support Engineer, you have to connect to the ABAP system using ABAP Development Tools. This allows you to use the troubleshooting functionality and tools.

> ### Note:  
> Certain analysis tools, such as the SQL Trace Analysis and SQL Explain SAP Fiori app are only accessible in SAP Fiori launchpad.

See [Connect to the ABAP System](../30-development/connect-to-the-abap-system-7379dbd.md).



<a name="loiof9e18605e01a485098fe5478649bd474__section_zgx_s3q_zqb"/>

## Troubleshoot Using Debugging

The most common use case for troubleshooting to analyze the implemented business logic is debugging. The following debugging scenarios exist:

-   Debug your own user
-   Debug another business user
-   Debug a communication user

See [ABAP Debugger](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/4ec365a66e391014adc9fffe4e204223.html).

> ### Note:  
> To find the business user and communication user ID for debugging, navigate to the *Debug Properties View* in ABAP Development Tools and search for business users \(`CB*`\) and communication users \(`CC*`\).



### Debug Your Own User

To debug the application with your own Application Support Engineer user, make sure that you have the business application role assigned.



### Debug Another Business User

To debug the application of another business user, you need to change the breakpoint settings in the debug properties view in ABAP Development Tools to the business user \(`CB*`\).



### Debug a Communication User

To debug the application of the communication user, you need to change the breakpoint settings in the debug properties view in ABAP Development Tools to the communication user \(`CC*`\).

**Related Information**  


[Troubleshooting Tools](troubleshooting-tools-911438b.md "Apart from debugging, you can also use other troubleshooting tools, such as the Feed Reader view in ABAP Development Tools, ABAP Profiler as well as the SQL Explain and SQL Trace Analysis SAP Fiori apps.")

