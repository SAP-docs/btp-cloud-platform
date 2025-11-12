<!-- loio038c3bbda9f74beba63b59f1e759c65b -->

# Request Consent



## Context

There are a couple of use cases which include requesting consent to work with a dedicated system in the *System Landscape*. See [Requesting Consent for a System](requesting-consent-for-a-system-091bc08.md).

You request consent for a system in one of the following cases:

-   As an administrator of a customer who has bought a subscription of an SAP partner application. You have received from the partner a URL to directly use the application. To have a system corresponding to your application subscription in the *Systems* page of your global account in SAP BTP, you have to request a consent by providing the URL of the application.

-   As an administrator of a global account in SAP BTP, you have a system listed in the *System* page but you need additional authorizations to include this system in a formation. In this case, you provide the system ID and namespace in the consent request.




## Procedure

1.  Sign in to the SAP BTP cockpit and navigate to *System Landscape* \> *Consent Requests*.

2.  In *My Consent Requests* tab, choose *Request Consent*.

3.  In the *Request Consent By* dropdown menu, select one of the following:

    -   *System URL*

        In the *URL* field, enter the URL of the application you are subscribed to.

        > ### Note:  
        > If the URL is not unique, you might get an error. If you subscribe to an application provided by an SAP Partner and you have only a URL, you have to get back to the SAP Partner and ask for the system ID and namespace of the application and use the *System ID and Namespace* option.

    -   *System ID and Namespace*

        1.  In the *System ID* field, enter the ID of the system.
        2.  In the *System Namespace* field, enter the namespace of the system.

        You get the system ID and namespace from the system details in the *Systems* page. To open the details, choose *System Landscape* \> *Systems* and then choose the system for which you are requesting consent.


4.  In the *Scopes* dropdown menu, select the scope that you need. See [Requesting Consent for a System](requesting-consent-for-a-system-091bc08.md).

5.  Choose *Request*.


