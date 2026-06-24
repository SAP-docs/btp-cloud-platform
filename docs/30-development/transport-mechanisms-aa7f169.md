<!-- loioaa7f169886154ebebb5ce4eb90091773 -->

# Transport Mechanisms

There are two git-based transport mechanisms in the ABAP environment.

**Git-based CTS \(gCTS**\) is the evolution of the classical Change and Transport Management System \(CTS\). It is the recommended approach for transporting objects between ABAP systems in your global account. It offers built-in and easy to use functionalities provided by the [Manage Software Components](https://help.sap.com/docs/btp/sap-business-technology-platform/software-component-lifecycle-management?version=Cloud) app in your SAP Fiori launchpad.

**abapGit** is an open-source Git client that allows you to import existing code into your ABAP system. You should use it for the following use cases:

-   Migrate on-premise code to the cloud. See [Use abapGit to Transform ABAP Source Code to the Cloud](https://developers.sap.com/tutorials/abap-environment-abapgit.html).
-   Transfer your code from the cloud to on premise. See [Transfer Your ABAP Source Code With SAP BTP ABAP Environment via abapGit](https://developers.sap.com/tutorials/abap-environment-abapgit-transfer.html).
-   Export your code when the development ABAP system is decommissioned.
-   Transfer your code from one cloud to another to share it with others, for example as open source, or from a partner to a customer account.
-   Implement mechanisms for distributed development and testing in dedicated development/test ABAP systems. This can be useful for special projects, such as proof of concepts or features that are dependent on regular development of a solution but shall run independent from its lifecycle.
-   To learn more about abapGit, see [Working with abapGit](working-with-abapgit-d62ed9d.md).

For a quick start on transportation, see [Transport a Software Component Between Two ABAP Systems](https://developers.sap.com/tutorials/abap-environment-gcts.html). For more information about the according delivery process, see [Delivery via Add-On or gCTS](https://help.sap.com/docs/btp/sap-business-technology-platform/delivery-via-add-on-or-gcts?version=Cloud).



## Transports within one or several global accounts

Transports in the ABAP environment are limited to a single global account. Use gCTS \(Manage Software Components app\) to transport ABAP development objects between systems within the same global account, following the standard ABAP transport lifecycle. For example, you can transport objects from DEV to TEST to PROD. You can't use gCTS \(Manage Software Components app\) to transport objects across global accounts. To move ABAP code between systems that belong to different global accounts, use abapGit to import and export the source code.

**gCTS vs. abapGit**


<table>
<tr>
<th valign="top">

Issue

</th>
<th valign="top">

gCTS \(transport\)

</th>
<th valign="top">

abapGit \(code import/export\)

</th>
</tr>
<tr>
<td valign="top">

purpose

</td>
<td valign="top">

regularly scheduled transport in system landscape

</td>
<td valign="top">

distribution of source code in development systems

</td>
</tr>
<tr>
<td valign="top">

scope

</td>
<td valign="top">

within a global account

</td>
<td valign="top">

extending beyond global accounts as well

</td>
</tr>
<tr>
<td valign="top">

target lifecycle

</td>
<td valign="top">

3 system landscape: DEV → TEST → PROD or 5 system landscape

</td>
<td valign="top">

only DEV to DEV is possible

</td>
</tr>
</table>

