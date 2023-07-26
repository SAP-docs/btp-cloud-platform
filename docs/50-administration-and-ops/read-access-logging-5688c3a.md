<!-- loio5688c3a63f4e400e841a4c7afc2bee8b -->

# Read Access Logging



<a name="loio5688c3a63f4e400e841a4c7afc2bee8b__section_N1007D_N1007A_N10002"/>

## Definition

Read Access Logging \(RAL\) is used to monitor and log read access to sensitive data. This data may be categorized as sensitive by law, by external company policy, or by internal company policy. The following typical questions might be of interest for an application that uses Read Access Logging:

-   Who accessed the data of a given business entity, for example a bank account?
-   Who accessed personal data, for example of a business partner?
-   Which employee accessed personal information, for example religion?
-   Did anyone search, for example, if VIPs were admitted to hospital?
-   Which accounts or business partners were accessed by which users?

These questions can be answered using information about who accessed particular data within a specified time frame. Technically, this means that all remote API and UI infrastructures \(that access the data\) must be enabled for logging. Read Access Logging is available for different channels such as Dynpro and Web Dynpro.



### Main Purposes of Read Access Logging

Read Access Logging is often required to comply with legal regulations or public standards such as data protection and privacy, for example in banking or healthcare applications. Data protection and privacy is about protecting and restricting access to personal data. In some countries, data protection and privacy regulations even require that access to certain personal data is reported. Companies and public institutions may also want to monitor access to classified or other sensitive data for their own reasons. If no trace or log is kept on who accesses data, it is difficult to track the person responsible for any data leaks to the outside world. Read Access Logging provides this information.

Read Access Logging is always based on a logging purpose that is freely defined according to the requirements of an organization \(for example, data protection and privacy\). This logging purpose is then assigned to each log entry as an attribute, which allows the log data to be classified and organized according to the logging purpose. For example, various archiving rules or reportings can be created based on logging purposes.

The Read Access Logging framework can thus be used to fulfill legal or other regulations, to detect fraud or data theft, for auditing purposes, or for any other internal purpose.



### Background Information on the Architecture of Read Access Logging

When an application is started, the Read Access Logging configuration is read. It indicates whether, for example, the current function module, operation, or UI element is log-relevant and to what extent. For example, should only the access itself be logged, or the content too? Log entries can be structured according to their semantics.

SAP applications may contain predefined configurations. However, the customer's key user will usually have to adapt them to his or her needs in order to fulfill the legal requirements of his or her organization - requirements that are not all known to SAP.

> ### Note:  
> -   As with all logging, your need to log data must be balanced with the effect logging will have on the performance of your system. The performance of your system will depend upon the amount of data you log, as well as the complexity of the conditions you specify for which data is logged.
> 
> -   You can find information on Read Access Logging configurations and templates in specific areas in the documentation for those areas.



<a name="loio5688c3a63f4e400e841a4c7afc2bee8b__section_N10119_N1007A_N10002"/>

## Activities



### Configuration Tasks

1.  Determine which data must be logged under which circumstances.

    The organization must define which legal or security requirements to apply and which data must be logged on a semantic level. For example, the legal department might determine that access to the social security number must be logged.

2.  Define purposes for Read Access Logging.

    Depending on the logging purpose and the laws and regulations that must be fulfilled, the application can define reports and rules for saving and processing the data. For more information, see [How to Define Purposes of Read Access Logging](how-to-define-purposes-of-read-access-logging-591b668.md).

3.  Determine the channels \(such as Dynpro or Web Dynpro\) through which the data can be accessed.
4.  Define log domains.

    Log domains are groups of semantically related data fields that need to be logged. For example, *Gross salary* and *Net salary* might be grouped together in the *Salary* log domain. Log domains bundle different technical representations of the same semantic entity. Log domains are channel-independent. For more information, see [How to Define Semantic Grouping of Fields to Be Logged](how-to-define-semantic-grouping-of-fields-to-be-logged-bac9a42.md).

5.  Define which data needs to be logged and whether only the access is logged or also the content.

    For more information, see [How to Define What to Log](how-to-define-what-to-log-0eb5542.md).




### Tasks During Operations

-   Defining a user exclusion list for Read Access Logging configurations.

    If you want to exclude certain users from Read Access Logging, they need to be added to a user exclusion list. This is useful for any automatic processing without user interaction, for example, background jobs. For more information, see [How to Exclude Specific Users from Read Access Logging](how-to-exclude-specific-users-from-read-access-logging-9ee32b3.md).

-   Displaying changes made to Read Access Logging configuration and evaluating errors and warnings.

    For more information, see [How to Check Runtime Errors and See Changes to Configurations](how-to-check-runtime-errors-and-see-changes-to-configurations-db0eade.md)




### Monitoring

You can view all log entries using the Read Access Logging monitor. For more information, see [How to Monitor the Read Access Log](how-to-monitor-the-read-access-log-5a1011a.md).

**Related Information**  


[SAP Signavio Process Navigator for Data Protection and Privacy \(Scope Item 5LE\)](https://me.sap.com/processnavigator/SolP/5LE)

