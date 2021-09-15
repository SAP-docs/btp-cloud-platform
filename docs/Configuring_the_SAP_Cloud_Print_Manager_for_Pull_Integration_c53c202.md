<!-- loioc53c2020e51448ca8152e8a8c9c9bfff -->

# Configuring the SAP Cloud Print Manager for Pull Integration

You want to configure the *SAP Cloud Print Manager for Pull Integration* to be able to use the *Maintain Print Queues* app.



<a name="loioc53c2020e51448ca8152e8a8c9c9bfff__ConfiguringTheSAPCloudPrintManager_prerequisites"/>

## Prerequisites

You have enabled the *Maintain Print Queues* app and created a print queue.



<a name="loioc53c2020e51448ca8152e8a8c9c9bfff__ConfiguringTheSAPCloudPrintManager_context"/>

## Context

*SAP Cloud Print Manager for Pull Integration* receives print jobs from the print queues you created in the *Maintain Print Queues* app and enables you to print documents from *S/4HANA Cloud* to the printer in your local network.



<a name="loioc53c2020e51448ca8152e8a8c9c9bfff__ConfiguringTheSAPCloudPrintManager_steps"/>

## Procedure

1.  Download the *SAP Cloud Print Manager for Pull Integration* installation package from the *Install Additional Software* app and select *Run as Administrator*.

    > ### Note:  
    > Keep in mind that you need to have administrator rights in order to proceed with the installation.

2.  Start the downloaded installer executable file. The *SAP Front-End Installer* opens. Select *SAP Cloud Print Manager for Pull Integration* and click *Next*. Wait until the installation has finished and confirm the final dialog. The print manager is now installed.

3.  Copy the system URL that you can find on the bottom of the initial screen of the *Maintain Print Queues* app. You will need this URL to establish a connection from the print manager to your S/4HANA cloud system.

4.  You will find the *SAP Cloud Print Manager for Pull Integration* in the Windows start menu of your print server. After the installation, start the program once with *Run as Administrator*. Enter your system account details. The print manager opens.

5.  Select *Runtime System* and choose *New*.

6.  A pop-up appears asking you to choose an authentication method. Select the *Basic Authentication*.

7.  Choose a *Name* for your print system and enter the URL of *Maintain Print Queues* that you have previously copied.

8.  Enter the communication user and the password you have defined in the communication scenario `SAP_COM_0466`. Select *OK*.

    Your print queue is now visible in the *SAP Cloud Print Manager for Pull Integration*.


**Related Information**  


[Maintain Print Queues](Maintain_Print_Queues_9dd6f64.md "")

[Creating Print Queues](Creating_Print_Queues_ed3e22d.md "You want to set up print queues to manage the printing of documents.")





