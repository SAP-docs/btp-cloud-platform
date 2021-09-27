<!-- loio3d734bec294441f498880e93ed3222dd -->

# Transfer your ABAP Source Code via abapGit

Use abapGit to transfer your ABAP source code from an ABAP environment instance back to your repository.

1.  Create or adapt your source code in the ABAP environment instance:

    1.  Open **ABAP Development Tools** and logon to your ABAP system.
    2.  Add an ABAP development object, e.g. an ABAP class, to your already existing *TESTABAPGIT* package. To do this, click on *Classes* and select *New ABAP Class*.

        ![](images/image1_c06082b.png)

    3.  Enter a name and description for your new ABAP class and click *Next*.

        ![](images/image2_2635c93.png)

    4.  Click *Finish*.

        ![](images/image3_a0c6b51.png)

    5.  Now you can implement your newly created class.

        ![](images/image4_002c889.png)

    6.  Save and activate.
2.  Open abapGit repositories:

    1.  Select your **ABAP system** in the Project Explorer and select *Windows* \> *Show View* \> *Other...* to open the *abapGit* repositories.

        ![](images/img5_b00fdff.png)

    2.  Search for *abapGit repositories*, select it and click *Open*.

        ![](images/img6_ab280cf.png)

3.  Stage and commit your ABAP development objects.
    1.  Right-click your *TESTABAPGIT* package and click *Stage and Push*.
    2.  Enter your repository credentials in the popup and click *OK*.

        ![](images/image7_c0ccbf7.png)

    3.  In the staging view you will see a list of changed, created or deleted ABAP development objects which can be transferred to your repository. The icon of the respective file indicates whether a file was created, modified, or deleted.

        ![](images/img8_4ddb086.png)

    4.  ABAP development objects which should become staged can be selected by drag and drop from the *unstaged* box to the *staged* box or by clicking on the *+* button. Enter your commit message and click**Commit and Push**.

        ![](images/img9_97b74b8.png)

    5.  You'll see a notification telling you that your push has started. Click *OK*.
    6.  The staged objects have now been transferred to your repository.

        ![](images/img100_17a4575.png)


