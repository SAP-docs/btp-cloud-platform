<!-- loio978b0394caf94e558f488282f68a8bcb -->

# Configuration of Event Publishing and Event Consumption Scenarios

You can define which event types shall be published or consumed using a connection defined through the communication arrangement. Each event type is assigned to one topic. Topics form a logical tree to organize events, such as a folder hierarchy in a file system. Thus, the topics appear as strings that consist of multiple segments and are separated by one defined delimiter, similar to file paths.



> ### Note:  
> Only events, which are bound to a connection, can be exchanged between an ABAP environment system and the SAP Business Technology Platform.



The following steps are required to configure event publishing and event consumption scenarios:

