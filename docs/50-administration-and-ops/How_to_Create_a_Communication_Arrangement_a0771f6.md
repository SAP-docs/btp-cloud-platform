<!-- loioa0771f6765f54e1c8193ad8582a32edb -->

# How to Create a Communication Arrangement



<a name="loioa0771f6765f54e1c8193ad8582a32edb__HowToCreateCommunArrangements_prerequisites"/>

## Prerequisites

-   You have already created a communication system with inbound and outbound users.

-   You have already created a communication user with a supported authentication type that is defined in the selected communication scenario.




<a name="loioa0771f6765f54e1c8193ad8582a32edb__HowToCreateCommunArrangements_context"/>

## Context



### Process Steps

![](images/Create_Communication_Arrangement_76fd898.png)

To create a communication arrangement, proceed as follows:



<a name="loioa0771f6765f54e1c8193ad8582a32edb__HowToCreateCommArrangements_steps"/>

## Procedure

1.  Open the *Communication Arrangements* app from the SAP Fiori Launchpad. Already existing communication arrangements are listed on the initial screen.

2.  Select *New*. In the *New Communication Arrangement* window, select a communication scenario and define the arrangement name. Select *Create*.

3.  New screen *Communication Arrangements* is now open. Under *Common Data* in the field *Communication System*select a communication system that you want your system to connect to.

4.  If the selected communication system already has a communication user for inbound communication, the user and required authentication type will be displayed in the field *User Name* under *Inbound Communication*. In the *Inbound Services* section, the URLs to the service endpoints are displayed.

     **Note:** Always use the API hostname of your tenant including the "-api" suffix. Don't use the UI hostname without the "-api".

5.  If the selected communication system already has a communication user for outbound communication, the user and required authentication type will be displayed in the field *User Name* under *Outbound Communication*.

6.  Save the arrangement.


**Related Information**  


[Maintain Communication Users](Maintain_Communication_Users_eef80dd.md "You can use this app to create and edit communication users. Communication users are used by solutions to authenticate themselves to be able to post data.")

[Maintain Communication Systems](Maintain_Communication_Systems_15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

