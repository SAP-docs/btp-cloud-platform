<!-- loio00de26798389472f989601306d2207e1 -->

# Manage Incidents

**Incident Management System**

As a provider of a SaaS solution, you should establish an incident management system, such as SAP Resolve, so that consumers can report issues.

If consumers of your SaaS solution run into problems, they need to be able to contact the provider of the software in a standardized way.

**Information to Identify ABAP System and Consumer Tenant for Incident Processing**

To process an incident, you have to identify the ABAP system and tenant, where the consumer issue has occurred. Therefore, the following information is required:

-   SAP Fiori launchpad URL

    In the SAP Fiori launchpad user actions menu, the SAP Fiori launchpad URL of a consumer tenant is displayed as *Server* in the *Settings* dialog. See [Settings](https://experience.sap.com/fiori-design-web/services/#settings).

-   System Details

    In the user actions menu, information about the ABAP system and tenant is displayed in section *System* in the *About* dialog. See [About](https://experience.sap.com/fiori-design-web/services/#about).

    The system name and description are of particular interest.


**Information to Reproduce the Customer Issue**

To reproduce the consumer issue, the following information should be provided:

-   Application details

    In the user actions menu, information about the SAP Fiori application is displayed in the *About* dialog in the *Application* section. See [About](https://experience.sap.com/fiori-design-web/services/#about).

    The application title and technical component ID are of particular interest.

-   Error details

    The error message is displayed in the SAP Fiori application or as a status code of the HTTP request that is failing.

-   Business user details

    In the user actions menu, the name and email address identifying the business user of the consumer are displayed in the *Settings* dialog in the *User Account* section. See [Settings](https://experience.sap.com/fiori-design-web/services/#settings).

-   Step-by-Step Description of the User Actions and Input

    To reproduce the customer issue, you need detailed information about the user actions that lead to the error, and, if possible, user input that was performed during these steps.


