<!-- loiof810031a67b04cb3988de9d651bb0c2e -->

# No Client with Requested ID



## Symptom

You are not yet authenticated, and you send your first request to a web application, which is running on SAP BTP, Cloud Foundry environment. After you enter your credentials in the login screen, the system responds with the following error message:

```
No client with requested id: <OAuth2 Client-Id> - Authorization Request Error - There was an error. The request for authorization was invalid.
```

The URL in the address-field of the browser contains the following URL-pattern **https://<subdomain\>.authentication.<cloudFoundryDomain\>/oauth/authorize?<urlParameters\>**.



## Reason and Prerequisites



### Technical Reason

Even though you were authenticated successfully, **the SAP Authorization and Trust Management service \(XSUAA\) could not assign the authorizations** \(scopes and attributes\) of your business user to the web application that you initially called. **The web application acts towards the SAP Authorization and Trust Management service as the OAuth2 client** and recognizes if the business user is sending an authorized request or not. If the request is not authorized, the web application first redirects the request to the authorized endpoint of the SAP Authorization and Trust Management service.

**The SAP Authorization and Trust Management service acts towards the web application as the OAuth2 Authorization server** and recognizes if the request to be authorized is authenticated or not. If the request is not authenticated, the service redirects the request to the configured identity provider \(IdP\) to initiate the authentication process.

The IdP sends a login screen to your browser so that you can authenticate yourself. The IdP then redirects your answer then back to the service with a SAML2 Bearer Assertion, which holds the authentication information of your business user. The SAP Authorization and Trust Management service can now retrieve the authorizations of your business user.

The service now wants to assign these authorizations to the OAuth2 client \(the web application\). The web application provides its OAuth2 client-id in the `client_id` URL parameter of the authorized endpoint. **The main point to consider here is that the SAP Authorization and Trust Management service accepts only the client-ids of those OAuth2 clients that it already knows**. That means that OAuth2 clients must register themselves to the service, before they call the authorized endpoint. This error occurs because **the web application was not registered as a valid OAuth2 client for the service**, before it called the authorized endpoint.



### Reasons


<table>
<tr>
<td valign="top">

**Reason**

</td>
<td valign="top">

**Solution**

</td>
</tr>
<tr>
<td valign="top">

You didn't create a service instance of the SAP Authorization and Trust Management service for your application.

</td>
<td valign="top">

Create a service instance for your application.

</td>
</tr>
<tr>
<td valign="top">

You're trying to access a SaaS application that you have unsubscribed from.

</td>
<td valign="top">

Subscribe to the SaaS application.

</td>
</tr>
</table>



## Solution



### Create a service instance for your own application

1.  Create a service instance in the space in which the web application is deployed.

    ```
    cf create-service xsuaa application my-uaa -c security/xs-security.json
    ```

2.  Create an entry in the `manifest.yml` file, defining the service binding between the web application and the SAP Authorization and Trust Management service application plan service instance.

    ```
    services:
      -my-uaa
    ```

3.  Redeploy the web application.

    ```
    cf push
    ```




### Subscribe to the SaaS application

1.  Log in to your Global Account.
2.  Choose your subaccount.
3.  Choose **Subscriptions**.
4.  Choose the SaaS application that you want to subscribe to.
5.  Choose **Subscribe**.
6.  Retry accessing the SaaS application \(it might be necessary to clear your cache\).

