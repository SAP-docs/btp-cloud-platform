<!-- loio091bc0872f2f4666b8395fcf5eb5411c -->

# Requesting Consent for a System

For some systems, you might need to ask for additional authorizations so that:

-   You can use these systems in formations.

    You have the system added in the *Systems* page, but to include it in a dedicated formation, you need to request a consent. See [Integrating SAP Solutions](integrating-sap-solutions-3414bbc.md).

-   You have an application you are subscribed to added to the *Systems* page.

    SAP Partners develop multitenant applications and sell subscriptions to their customers. These applications are deployed to the global account in SAP BTP of the SAP Partner. When customers buy a subscription to such an application, the SAP partner has a dedicated subaccount for each customer and creates a subscription to the application in every subaccount for every customer. Then, the SAP Partner takes the respective URL from *Services* \> *Instances and Subscriptions* of every subscription and sends it to the respective customer.

    Customers do not have access to the subscription in their global accounts in SAP BTP. However, they might need to use the subscription to the application they've purchased from the SAP Partner in a formation and to integrate it with other systems. To do that, customers need to have this subscription listed as a system in the *System Landscape* \> *Systems* page.

    To have this system listed in the *Systems* page, customers need to make a request to the SAP Partner in the *System Landscape* \> *Consent Requests* page. The SAP Partner sees the request and then approves or rejects it. When the request has been approved, the customers see the system of this application listed in the *Systems* page of their global accounts in SAP BTP.




<a name="loio091bc0872f2f4666b8395fcf5eb5411c__section_qkl_354_22c"/>

## Request Consent

You request consent for a system in one of the following cases:

-   As a customer of a partner application, after subscribing to this application, you have received a URL so you can use the application. To have a system corresponding to your application subscription in the *Systems* page of your global account in SAP BTP, you have to request a consent by providing the URL of the application.

    Wait for the SAP Partner to approve or reject your request. Once it is approved, you will have a system corresponding to your application subscription in the *Systems* page. After that, you will be able to integrate this system with services and systems using a formation.

-   As a user of SAP BTP, you have a system listed in the *System* page but you need additional authorizations to include this system in a formation. In this case, you provide the system ID and namespace in the consent request.


When you request consent for a system, you specify a scope, that is what is the purpose of the requested authorizations. These are the scopes you can choose from:

-   Integration

    Use this scope when you have the system in the *Systems* page and you need additional authorizations to include it in a formation.

-   System Sharing

    Use this scope when you are subscribed to an application and you want this application to appear as a system added to the *Systems* page.


To request consent for a system, you have to:

1.  Log in to the SAP BTP cockpit and navigate to *System Landscape* \> *Consent Requests*.
2.  In *My Consent Requests* tab, choose *Request Consent*.
3.  In the *Request Consent By* dropdown menu, select one of the following:
    -   *System URL*

        In the *URL* field, enter the URL of the application you are subscribed to.

        > ### Note:  
        > If the URL is not unique, you might get an error. If you subscribe to an application provided by an SAP Partner and you have only a URL, you have to get back to the SAP Partner and ask for the system ID and namespace of the application and use the *System ID and Namespace* option.

    -   *System ID and Namespace*

        1.  In the *System ID* field, enter the ID of the system you want to include in a formation.
        2.  In the *System Namespace* field, enter the namespace of the system you want to include in a formation.

        You get the system ID and namespace from the system details in the *Systems* page. To open the details, choose *System Landscape* \> *Systems* and then choose the system for which you are requesting consent.


4.  In the *Scope\(s\)* dropdown menu, select the scope that you need.
5.  Choose *Request*.



<a name="loio091bc0872f2f4666b8395fcf5eb5411c__section_o4n_k54_22c"/>

## Approve or Reject Consent

You approve or reject consent for a system in one of the following cases:

-   As an SAP Partner, you develop multitenant applications, deploy them to SAP BTP and sell subscriptions to your customers. When customers have subscribed to your application, they may want to request a consent from you so they have a respective system in their *Systems* page in their global accounts.

-   As a system administrator giving additional authorizations so the system can be included in a formation.

To approve or reject such a request, you have to:

1.  Log in to the SAP BTP cockpit and navigate to *System Landscape* \> *Consent Requests*.
2.  In the *Incoming Consent Requests* tab, choose *Approve* or *Reject* for each request.

