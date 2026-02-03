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

3.  The new *Communication Arrangements* screen is now open. In the *Communication System* field under *Common Data*, select a communication system that you want your system to connect to. Alternatively, you can click *New* to create a new communication system.

4.  Depending on the underlying communication scenario, maintain the *Additional Properties*.

5.  If the communication scenario provides inbound services, you have to select the desired communication user and authentication method from the assigned communication system. The defined communication user then has the authorization to call these services. In the *Inbound Services* section, the URLs to the service endpoints are displayed. Depending on the underlying scenario, maintain the required inbound parameters.

    > ### Note:  
    > The inbound section of the communication arrangement provides the correct URLs for API consumption. Depending on the protocol and scenario, the host name or path might differ. Always use the URLs provided in this section when configuring the calling service. For security reasons, we have different URLs for each user type.

6.  If the communication scenario provides outbound services, you have to select the desired outbound user and authentication method from the assigned communication system. In the *Outbound Services* section, the URL path and port need to be defined. Depending on the underlying scenario, maintain the required outbound parameters and job execution details.

    > ### Note:  
    > If the required outbound service is of the type *Outbound SQL Access*, you need to make the following additional settings:
    > 
    > -   *Remote Database Schema Name*: Here you enter the schema in the remote system containing the objects to be accessed.
    > 
    > -   If required click *Use Default*. This reads the*Remote Database Schema Name* from the Outbound SQL access service.
    > 
    > -   *Remote Database Name*: The database in the remote system containing the objects to be accessed. Usually you can leave the field empty unless the remote system hosts multiple databases.

7.  Save the arrangement.


**Related Information**  


[Maintain Communication Users](maintain-communication-users-eef80dd.md "You can use this app to create and edit communication users. Communication users are used by solutions to authenticate themselves to be able to post data.")

[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

