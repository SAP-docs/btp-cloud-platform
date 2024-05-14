<!-- loio0fc8df84e93147f58c4329b454809d22 -->

# Monitoring and Analysis



Monitoring and analysis tasks are part of the daily work as administrator.

Common activities in this context include the following:

-   Find business users with unnecessarily high privileges \(for example, too many admin users\)

-   Find users with unnecessary or critical authorization combinations \(the result of privilege creep\)

-   Find business roles granting access to data too generously \(that is, having unmaintained restrictions\)

-   Analyze the root cause for authorization errors


You can use the*IAM Information System* app to monitor the relationships between business users, business roles, business catalogs, and so on.

The *IAM Key Figures* app enables you to monitor KPIs for your authorization system. It shows the number of locked business users, for example. Also, the number of unrestricted business roles is shown. Thresholds can be defined to visualize critical deviations from the desired state.

For the analysis of issues with privileges you can use the *Display Authorization Trace* app.

An overview of the technical users in the system – both communication users and SAP support users – is provided by the *Display Technical Users* app. The *Maintain User Sessions* app enables you to analyze sessions containing a lock and to find the associated business user.

**Related Information**  


[IAM Information System](iam-information-system-82d17cf.md "With this app you can get an overview of business users in your system and what roles and restrictions are assigned to them.")

[IAM Key Figures](iam-key-figures-f249696.md)

[Display Authorization Trace](display-authorization-trace-79b3c9b.md)

[Maintain User Sessions](maintain-user-sessions-dde9087.md)

