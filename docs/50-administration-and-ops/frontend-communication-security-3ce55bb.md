<!-- loio3ce55bbd3cc54ad8a4986d5b57d17eb7 -->

# Frontend Communication Security

Communications between the customer browser and the system landscapes of SAP BTP, ABAP environment are secured by industry best practices and state-of-the-art open cryptographic standards. Customers use a unique, customer-specific URL. Communication is carried out via the Reverse Proxy \(RP\) component. The communication channels are secured by using Transport Layer Security \(TLS\) protocol version 1.2.

Client-side security controls implemented by the browser and by SAP BTP, ABAP environment mitigate the risk of various attacks, including cross-site scripting, data injection, and clickjacking.

Some of these controls can be configured with allowlists such as the following:

-   Trusted sources of scripts, stylesheets, and fonts can be added to the default Content Security Policy.

-   Trusted hosts can be defined for the clickjacking protection, and for safe redirects.


