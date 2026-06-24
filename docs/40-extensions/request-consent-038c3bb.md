<!-- loio038c3bbda9f74beba63b59f1e759c65b -->

# Request Consent



## Context

There are a couple of scenarios which include requesting consent to work with a dedicated system or system type in the *System Landscape*. See [Requesting Consent for a System or System Type](requesting-consent-for-a-system-or-system-type-091bc08.md).

You request consent for a system in one of the following cases:

-   As an administrator of a customer who has bought a subscription of an SAP partner application. You have received from the partner a URL to directly use the application. To have a system corresponding to your application subscription in the *Systems* page of your global account in SAP BTP, you have to request a consent by providing the URL of the application.

-   As an administrator of a global account in SAP BTP, you have a system listed in the *System* page but you need additional authorizations to include this system in a formation. In this case, you provide the system ID and namespace in the consent request.


You request consent for a system type when you went to add a system of this system type and you don't have it in your system landscape by default.



## Procedure

1.  Sign in to the SAP BTP cockpit and navigate to *System Landscape* \> *Consent Requests*.

2.  In *My Consent Requests* tab, choose *Request Consent*.

3.  In the *Request Consent For* dropdown menu, select one of the following:

    -   *System*: when you want to add a system in the *Systems* page or include a system in a formation.
    -   *System Type*: when you want to add a system of a specific system type in the *Systems* page and you don't have this system type by default.

4.  In the *Request Consent By* dropdown menu, select one of the following:

    For a system:

    -   *System URL*

        In the *URL* field, enter the URL of the application you are subscribed to.

        > ### Note:  
        > If the URL is not unique, you might get an error. If you subscribe to an application provided by an SAP partner and you have only a URL, you have to get back to the SAP partner and ask for the system ID and namespace of the application and use the *System ID and Namespace* option.

    -   *System ID and Namespace*

        1.  In the *ID* field, enter the ID of the system.
        2.  In the *Namespace* field, enter the namespace of the system which is the namespace of the system type.

        You get the system ID and namespace from the system details in the *Systems* page. To open the details, choose *System Landscape* \> *Systems* and then choose the system for which you are requesting consent.


    For a system type, in the *Namespace* field, enter the namespace of the system type.

5.  In the *Scopes* dropdown menu, select the scope that you need:

    -   *System Sharing*: when you want to add a system corresponding to your application subscription in the *Systems* page of your global account in SAP BTP.
    -   *Integration*: when you want to include a system in a formation and this formation requires consent for this.
    -   *System Type Sharing*: when you to add a system of this system type and you don't have it in your system landscape by default.

    See [Requesting Consent for a System or System Type](requesting-consent-for-a-system-or-system-type-091bc08.md).

6.  Choose *Request*.




## Next Steps

Once you've sent the consent request, wait for the owner of the system or system type to approve or reject it. You can monitor the state of your requests in the *For Systems* and *For System Types* tabs in *My Consent Requests*.

