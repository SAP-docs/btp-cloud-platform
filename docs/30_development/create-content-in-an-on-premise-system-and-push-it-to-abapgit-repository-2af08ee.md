<!-- loio2af08eedf488445d89690f581034dbaa -->

# Create Content in an On-Premise System and Push it to abapGit Repository



<a name="loio2af08eedf488445d89690f581034dbaa__prereq_jwg_15c_fhb"/>

## Prerequisites

You have installed and set up abapGit. See [Install and Set Up abapGit](install-and-set-up-abapgit-2002380.md).

> ### Restriction:  
> Please be aware that abapGit is an open-source project owned by the community. Therefore, we do not provide support for abapGIT. We only support the Git integration in the ABAP environment.



## Procedure

1.  After installing and launching abapGit, select *Clone or download*, and copy the URL of your repository.

2.  Call up transaction `ZABAPGIT`, and select *+ Online*.

3.  Paste the URL of your repository.

4.  Select *Create package*.

    > ### Note:  
    > If you have already created a software component with gCTS, you can skip steps 4 to 6 and use this software component in step 7.

5.  Add a package name and short description, and select *Continue*.

6.  Confirm with *OK*.

    The cloned abapGit repository is displayed in abapGit.

7.  Log on to ABAP Development Tools in Eclipse, and navigate to your newly created package.

8.  Add ABAP development objects to your package. See [Released ABAP Object Types](released-abap-object-types-b31aa03.md).

9.  Navigate back to the abapGit UI, and select *Refresh* to display the development objects that you have created in Eclipse.

10. Choose *Stage*.

11. Select single objects or choose *Add all and commit*.

    > ### Note:  
    > You can also select structure packages to be exported.

12. Enter a *committer name*, *committer e-mail*, and *comment*.

13. Select *Commit*.

14. In the Login popup, enter your abapGit repository server credentials, and select *Execute*.

    The pushed ABAP objects are displayed in your abapGit repository.




<a name="loio2af08eedf488445d89690f581034dbaa__postreq_arz_4xc_fhb"/>

## Next Steps

[Import Content from abapGit Repository into the ABAP Environment](import-content-from-abapgit-repository-into-the-abap-environment-0b0d894.md)

