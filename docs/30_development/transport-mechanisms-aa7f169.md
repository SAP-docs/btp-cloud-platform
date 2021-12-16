<!-- loioaa7f169886154ebebb5ce4eb90091773 -->

# Transport Mechanisms

There are two git-based transport mechanisms in the ABAP environment.

**Git-based CTS \(gCTS**\) is the evolution of the classical Change and Transport Management System \(CTS\). It is the recommended approach for transporting objects between ABAP systems in your global account. It offers built-in and easy to use functionalities provided by the Manage Software Components app in your SAP Fiori launchpad.

**abapGit** is an open-source Git client that allows you to import existing code into your ABAP system. You should use it for the following use cases:

-   Migrate on-premise code to the cloud. See [Use abapGit to Transform ABAP Source Code to the Cloud](https://developers.sap.com/tutorials/abap-environment-abapgit.html).
-   Transfer your code from the cloud to on premise. See [Transfer Your ABAP Source Code With SAP BTP ABAP Environment via abapGit](https://developers.sap.com/tutorials/abap-environment-abapgit-transfer.html).
-   Export your code when the development ABAP system is decommissioned.
-   Transfer your code from one cloud to another to share it with others, for example as open source, or from a partner to a customer account.
-   Implement mechanisms for distributed development and testing in dedicated development/test ABAP systems. This can be useful for special projects, such as proof of concepts or features that are dependent on regular development of a solution but shall run independent from its lifecycle.
-   To learn more about abapGit, see [Working with abapGit](working-with-abapgit-d62ed9d.md).

For a quick start on transportation, see [Transport a Software Component Between Two ABAP Systems](https://developers.sap.com/tutorials/abap-environment-gcts.html).

