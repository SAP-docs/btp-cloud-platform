<!-- loio8f62c414203546faa96542ad723f932e -->

# Creating Custom Code

With the *ABAP Cloud Editor*, you can write your own code using ABAP for key users.

The editor is divided into three tabs that focus on different aspects of dealing with code: *Develop*, *Test*, and *Compare*.



<a name="loio8f62c414203546faa96542ad723f932e__section_pwx_ls2_4vb"/>

## Develop

On the *Develop* tab, you can write, save, and publish ABAP code. Saving means writing a draft version of the code that only you can see. Once you publish your code, it'll be available in the system and visible for all users. Depending on the method you're implementing, there is a button *Show Sample Code*. Click this button to open a dialog that shows the sample code provided by SAP. Click *Expand* to increase the vertical space for the code.

The method signature on the right provides information about the method's parameters.

Put the cursor on a class, interface, or parameter to view the documentation displayed in the element information at the bottom of the page.

In edit mode, you can add prebuilt code blocks by selecting *Insert Code Snippet*.

> ### Note:  
> Do not use the `return` statement in your code because it can affect the framework logic. It can result in missing custom logic trace entries or unexpected code behavior.



<a name="loio8f62c414203546faa96542ad723f932e__section_orr_1t2_4vb"/>

## Test

On the *Test* tab, you can test your code with different parameter values. Use the parameter kind dropdown to navigate to **importing**, **exporting**, **changing**, and **returning** parameters, depending on what the method offers. Use the input fields in the table rows to enter parameter values. For table parameters, click *Add* to add a new table row or *Delete* to delete a table row.

On the right, you can choose what code version will be tested: either *Draft* or *Latest Published*. Click *Test* to run the test. If the test was successful, a toast will appear. You can then view the outcome in the different parameter tables.

If you want to save the test data you entered, click *Save As*, enter a test variant name, and click *Save*. If you have already selected an existing test variant, just click *Save*. Use *Manage* to delete saved test variants.



<a name="loio8f62c414203546faa96542ad723f932e__section_jbr_yt2_4vb"/>

## Compare

On the *Compare* tab, you can compare different code versions. If you have a draft, it can be selected on the left. This is useful if you want to copy parts from older code versions to a new draft, for example. On the *Compare* tab, you can only save code but not publish it. Use the *Develop* tab for all code editing features.

> ### Note:  
> Please make sure that your draft logic is syntactically correct and tested. Otherwise, the draft logic might be lost when your system is upgraded to another release.



<a name="loio8f62c414203546faa96542ad723f932e__section_qr5_p3t_cwb"/>

## Keyboard Shortcuts

You can use keyboard shortcuts while working with the ABAP Cloud editor. The following key combinations are provided:


<table>
<tr>
<th valign="top">

Key Combination



</th>
<th valign="top">

What Is It Used For?



</th>
</tr>
<tr>
<td valign="top">

[Ctrl\] + [Space\]  



</td>
<td valign="top">

To turn on code completion



</td>
</tr>
<tr>
<td valign="top">

[Shift\] + [F1\]  



</td>
<td valign="top">

To use the pretty printer



</td>
</tr>
<tr>
<td valign="top">

[Ctrl\] + [/\] \(Slash\)

[Ctrl\] + [\#\] \(Hash\)



</td>
<td valign="top">

To uncomment or comment out a code block



</td>
</tr>
</table>

