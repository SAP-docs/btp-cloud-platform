<!-- loio978b0394caf94e558f488282f68a8bcb -->

# Configure Event Publishing and Event Consumption Scenarios

You can definewhich event types shall be published or consumed using a connection defined through the communication arrangement. Each event type is assigned to one topic. Topics form a logical tree to organize events, such as a folder hierarchy in a file system. Thus, the topics appear as strings that consist of multiple segments and separated by one defined delimiter, similar to file paths.



**Prerequisites**

-   You have the *SAP\_BR\_ADMINISTRATOR* role.

-   The *Enterprise Event Enablement - Configure Channel Bindings* app is visible.

    > ### Note:  
    > If the *Enterprise Event Enablement - Configure Channel Bindings* app is not visible, add the corresponding business catalog to the *SAP\_BR\_ADMINISTRATOR* role using the *Maintain Business Roles* app. The change in your role becomes effective after you have logged out and logged in again. For more information about adding catalogs to business roles, see 

-   You have established a connection through the configuration of the communication arrangement in the previous steps. For more information, see [Create, Maintain and Delete Communication Arrangements](create-maintain-and-delete-communication-arrangements-2144420.md).


> ### Note:  
> Only events which are bound to a connection can be exchanged between an ABAP environment system and the SAP Business Technology Platform.

