<!-- loio2002380aeda84875a5fae4adc66b3fdb -->

# Install and Set Up abapGit

Learn how to install and set up abapGit.



<a name="loio2002380aeda84875a5fae4adc66b3fdb__prereq_xkx_yb2_dhb"/>

## Prerequisites

-   You have signed up for a Git account of your choice, for example GitHub.
-   You have access to an on-premise system with the required root CA of the Git server \(`STRUST`\).
-   You have downloaded and installed the front-end components of [ABAP Development Tools \(ADT\)](https://tools.hana.ondemand.com/#abap). See [Video Tutorial: Configure Developer Tools](https://www.youtube.com/watch?v=iDcAPYjwTV0&list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr&index=3&t=0s).


> ### Restriction:  
> Please be aware that abapGIT is an open-source project owned by the community. Therefore, we do not provide support for abapGIT. We only support the GIT integration in the ABAP environment.



## Procedure

1.  Log on to your github.com account.

2.  Create an abapGit repository by clicking on *New repository*.

3.  Enter a repository name, tick the *Initialize this repository with a README* checkbox, and select *Create repository*.

    Your repository is set up.

4.  Copy the content of the latest build from program `zabapgit` to your clipboard. You can find the content in the abapGit repository [https://github.com/abapGit/abapGit](https://github.com/abapGit/abapGit).

    > ### Caution:  
    > Check with your system administrator before installing `zabapgit`.

5.  Log on to an on-premise system of your choice, create a new program, and paste the content from your clipboard.

    > ### Note:  
    > Select `EN` as your logon language.

6.  Activate and execute the program.

    abapGit is installed and launched. See also [Video Tutorial: abapGit Installation](https://www.youtube.com/watch?time_continue=28&v=5TCBcJCafP4).

7.  Log on to ABAP Development Tools in Eclipse.

8.  Navigate to *Help* \> *Install New Software...*.

9.  To install the abapGit repositories ADT plug-in, add the following URL: ***https://eclipse.abapgit.org/updatesite/*** and provide a name for the repository.

10. To display all the available features, press enter, and select *abapGit for ABAP Development Tools \(ADT\)*.

11. Select *Next* to finish the installation.




<a name="loio2002380aeda84875a5fae4adc66b3fdb__postreq_tqq_qzb_fhb"/>

## Next Steps

[Create Content in an On-Premise System and Push it to abapGit Repository](create-content-in-an-on-premise-system-and-push-it-to-abapgit-repository-2af08ee.md)
