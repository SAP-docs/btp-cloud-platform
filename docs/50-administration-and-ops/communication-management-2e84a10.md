<!-- loio2e84a10c430645a88bdbfaaa23ac9ff7 -->

# Communication Management

The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.



<a name="loio2e84a10c430645a88bdbfaaa23ac9ff7__CommunicationManagement_prereq"/>

## Prerequisites

-   Predefined communication scenarios are available for different use cases, for example the integration for employee data. Decide which scenario you are going to use to create a communication arrangement.




<a name="loio2e84a10c430645a88bdbfaaa23ac9ff7__CommunicationManagement_processOverview"/>

## Process Overview

![](images/Communication_Management_Overview_35904a6.png)

The communication management apps allow you to establish secure communication between your solution and other systems. The best practice to organize efficient data exchange is to proceed as follows:

1.  Create communication user for inbound communication according to your needs using the *Maintain Communication Users* app.

2.  Create communication system using the *Communication Systems* app that represents the system you want to communicate with. If the selected scenario contains inbound services, you select the user for inbound communication that you have created earlier.

3.  Create a communication arrangement using the *Communication Arrangements* app. You select the communication system that you have created earlier. The information about the user for inbound communication will be populated automatically. If several users for inbound communication exist for the system, you can select the appropriate one. Otherwise the first user in the list will be selected automatically. If the selected scenario contains outbound services, you have to enter the outbound user information manually.

4.  Select *Save* to activate the communication arrangement.


**Related Information**  


[Maintain Communication Users](maintain-communication-users-eef80dd.md "You can use this app to create and edit communication users. Communication users are used by solutions to authenticate themselves to be able to post data.")



[Maintain Communication Systems](maintain-communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

[IAM Information System](iam-information-system-82d17cf.md "With this app you can get an overview of business users in your system and what roles and restrictions are assigned to them.")

