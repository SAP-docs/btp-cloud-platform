<!-- loiodb0eade2a1b24a99a9d1a8c18e37eb77 -->

# How to Check Runtime Errors and See Changes to Configurations



## Context

The Administrative Log of Read Access Logging provides information about different types of information such as:

-   Action - changes made to Read Access Logging configuration.
-   Error - errors that occur within the Read Access Logging framework.



### Action Log Entries

The action log records the following Read Access Logging changes:

-   Configuration
-   User exclusion list
-   Enabling and disabling of Read Access Logging in the current client

> ### Note:  
> Only configuration changes performed manually are recorded in the log. Configurations that have been transported into the system are not included in the Administrative Log.



### Error Log Entries

Error entries could be errors in the configuration, or problems that occur during logging. The log entry may recommend action to resolve the error and/or provide other information relevant for key users or SAP Active Global Support.



## Procedure

1.  In the app Read Access Logging Configuration, open *Administrative Log*.

2.  Select a *Data Source*, either the database or the archive.

3.  For *Databases*, specify a time filter. For *Archives*, select the *Archive Name*.

4.  Enter a *User Name* to search the log for configuration actions or read access performed by a specific user.

5.  Specify a log *Type* for archives or *Event Type* for databases \(*Error*, *Warning*, *Message*, *Action* or *Logging Error*\).


