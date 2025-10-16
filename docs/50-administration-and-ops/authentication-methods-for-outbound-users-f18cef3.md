<!-- loiof18cef354fb84026b5022020d82ae01d -->

# Authentication Methods for Outbound Users

You can define how your solution authenticates itself when it sends business documents to the external system. For security reasons, we recommend the use of certificate-based authentication.

You can choose between the following authentication methods:

-   User name and password

-   SSL Client Certificate

-   OAuth 1.0

-   OAuth 2.0

    You can choose between the following authentication methods:

    -   Basic

        If you use this method, you need to enter a client secret.

    -   mTLS

        If you use this method, you need to select a client certificate.

    -   JWT

        You can use JWT \(JSON Web Tokens\) to authenticate an OAuth client at the token endpoint of an OAuth authorization server \(instead of using a client ID and a client secret\).

        If you use this method, you need to download the corresponding certificate to your local device.

    -   None



If you want to use a SSL Client Certificate, you can either use the default certificate of your solution or a client certificate you have defined in the *Maintain Client Certificates* app.

