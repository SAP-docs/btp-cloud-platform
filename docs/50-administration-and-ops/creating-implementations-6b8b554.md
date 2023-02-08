<!-- loio6b8b5545cd91489ca42aea0ec611f01c -->

# Creating Implementations

Get an overview of how to create and publish your implementations.



<a name="loio6b8b5545cd91489ca42aea0ec611f01c__section_g4d_rbf_4vb"/>

## Process Steps

This is a generic description about how to create implementations. For specific documentation, refer to the individual extension point documentation in the *Custom Logic* app.

1.  To create a new implementation, open the *Custom Logic* app and click *Create*.
2.  Select the extension point \(BAdI\) that you want to implement. Perform a free text search by using the search field. The extension point descriptions, IDs and documentation will be searched. To view the documentation of an extension point, click *View Documentation*. When you have selected an extension point, click *Step 2*.

3.  Depending on the extension point you've selected, you can enter the implementation attributes next. Open the *Edit Filter Condition* dialog by clicking *Add*.

4.  All BAdI filter conditions added in the dialog are connected with `AND`. Click *Save* to add the filter condition to the list of filters. You can add more rows to the filter list by opening the dialog again. The filter list rows are connected with `OR`. Click *Step 3* once you've maintained the filters.

5.  Enter the implementation description and the ID. The description must start with a non-whitespace character. The ID starts with a fixed prefix and its total length must not exceed 30 characters. Click *Review* once you've maintained valid values.

6.  Review the data you entered. If you want to make changes, click *Edit* in the respective section. Once you're finished, click *Create*. The creation process starts in the background and you're taken to the implementation detail page.

7.  Once the implementation is created, the status will change from *Creating* to *Created*. You can now edit the implementation attributes if your implementation has any, or publish your implementation to start writing code. After publishing, click *Open Code Editor* to write custom code.


