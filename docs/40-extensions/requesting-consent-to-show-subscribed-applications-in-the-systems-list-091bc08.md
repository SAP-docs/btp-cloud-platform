<!-- loio091bc0872f2f4666b8395fcf5eb5411c -->

# Requesting Consent to Show Subscribed Applications in the Systems List

SAP Partners develop multitenant applications and sell subscriptions to their customers. These applications are deployed to the global account in SAP BTP of the SAP Partner. When customers buy a subscription to such an application, the SAP partner has a dedicated subaccount for each customer and creates a subscription to the application in every subaccount for every customer. Then, the SAP Partner takes the respective URL from *Services* \> *Instances and Subscriptions* of every subscription and sends it to the respective customer.

Customers do not have access to the subscription in their global accounts in SAP BTP. However, they might need to use the subscription to the application they've purchased from the SAP Partner in a formation and to integrate it with other systems. To do that, customers need to have this subscription listed as a system in the *System Landscape* \> *Systems* page.

To have this system listed in the *Systems* page, customers need to make a request to the SAP Partner in the *System Landscape* \> *Consent Requests* page. The SAP Partner sees the request and then approves or rejects it. When the request has been approved, the customers see the system of this application listed in the *Systems* page of their global accounts in SAP BTP.



<a name="loio091bc0872f2f4666b8395fcf5eb5411c__section_qkl_354_22c"/>

## Customers of Partner Applications

As a customer of a partner application, after subscribing to this application, you have received a URL so you can use the application. To have a system corresponding to your application subscription in the *Systems* page of your global account in SAP BTP, you have to request a consent. To do that:

1.  Log in to the SAP BTP cockpit and navigate to *System Landscape* \> *Consent Requests*.
2.  In *My Consent Requests* tab, choose *Request Consent*.
3.  Enter the URL of the application that you've been given by the SAP Partner and choose *Request*.

Wait for the SAP Partner to approve or reject your request. Once it is approved, you will have a system corresponding to your application subscription in the *Systems* page. After that, you will be able to integrate this system with services and systems using a formation.



<a name="loio091bc0872f2f4666b8395fcf5eb5411c__section_o4n_k54_22c"/>

## SAP Partners

As an SAP Partner, you develop multitenant applications, deploy them to SAP BTP and sell subscriptions to your customers. When customers have subscribed to your application, they may want to request a consent from you so they have a respective system in their *Systems* page in their global accounts. To approve or reject such a request, you have to:

1.  Log in to the SAP BTP cockpit and navigate to *System Landscape* \> *Consent Requests*.
2.  In the *Incoming Consent Requests* tab, choose *Approve* or *Reject* for each request.

