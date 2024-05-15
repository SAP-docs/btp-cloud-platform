<!-- loioaafd07479eb34a14bed887ec248432a0 -->

# Clickjacking Protection

Clickjacking \(or UI redressing\) is a type of attack that tricks the user into triggering actions within an application by hijacking mouse clicks or other user inputs.

In the simplest attack scenario, an invisible iFrame containing the attacked page is positioned over an attacker-controlled page. The user thinks the UI is original and is unaware of the actual actions triggered on the invisible page in the frame. To protect against this attack, you need to control whether to render your application within a frame and which pages are allowed.

The allowlist service is an ABAP-wide service and supports HTML-based frameworks to implement protections. By default, clickjacking protection is active.

As soon as the protection is enabled, a special check is performed every time an application is rendered. If the application is embedded into another one, the check determines whether the other application is secure. If the check fails, the embedded application is not framed. An error message appears.

An application is considered secure if one of the following applies:

-   The application itself is not embedded in another frame

-   The host of the application is part of the same domain as the embedding applications \(same origin policy\).

-   The host of the application is part of the allowlist. For multi-domain scenarios, you have to make sure that the host name of the application in which your application is embedded, is part of the allowlist.


**Related Information**  


[Maintain Protection Allowlists](maintain-protection-allowlists-81aed02.md "With this app you can maintain a list of trusted hosts or URL patterns.")

