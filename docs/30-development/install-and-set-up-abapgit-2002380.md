<!-- loio2002380aeda84875a5fae4adc66b3fdb -->

# Install and Set Up abapGit

Learn how to install and set up abapGit.



-   You have signed up for a Git account of your choice, for example GitHub.
-   You have downloaded and installed the front-end components of [ABAP Development Tools \(ADT\)](https://tools.hana.ondemand.com/#abap). See [Video Tutorial: Configure Developer Tools](https://www.youtube.com/watch?v=iDcAPYjwTV0&list=PLkzo92owKnVxWqJSoFLGe1VRkzOs4Ucdr&index=3&t=0s).


> ### Restriction:  
> Please be aware that abapGit is an open-source project owned by the community. Therefore, we do not provide support for abapGit. We only support the Git integration in the ABAP environment.



Part 1: Create a Git repository

1.  Log on to your github.com account.

2.  Create an abapGit repository by clicking on *New repository*.
3.  Enter a repository name, tick the *Initialize this repository with a README* checkbox, and select *Create repository*.




Section 2: Install zabapGit for the on-premise use case

1.  Copy the content of the latest build from program `zabapgit` to your clipboard. You can find the content in the abapGit repository [https://github.com/abapGit/abapGit](https://github.com/abapGit/abapGit).

    > ### Caution:  
    > Check with your system administrator before installing `zabapgit`.

2.  Log on to an on-premise system of your choice, create a new program, and paste the content from your clipboard.

    > ### Note:  
    > Select `EN` as your logon language.

3.  Activate and execute the program.

    abapGit is installed and launched. See also [Video Tutorial: abapGit Installation](https://www.youtube.com/watch?time_continue=28&v=5TCBcJCafP4).




Part 3: Install an ADT plugin for abapGit

1.  Log on to ABAP Development Tools in Eclipse.

2.  Navigate to *Help* \> *Install New Software...*.

3.  To install the abapGit repositories ADT plug-in, add the following URL: `https://eclipse.abapgit.org/updatesite/` and provide a name for the repository.

4.  To display all the available features, press enter, and select *abapGit for ABAP Development Tools \(ADT\)*.

5.  Select *Next*to finish the installation.




[Create Content in an On-Premise System and Push it to abapGit Repository](create-content-in-an-on-premise-system-and-push-it-to-abapgit-repository-2af08ee.md)

