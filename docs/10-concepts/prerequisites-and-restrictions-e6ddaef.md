<!-- loioe6ddaefcbb571014b70fa01fc6a3f818 -->

# Prerequisites and Restrictions

Find a list of the product prerequisites and restrictions for SAP BTP.



<a name="loioe6ddaefcbb571014b70fa01fc6a3f818__section_EE6558EE0B104EF49C81123E4689AB01"/>

## General Constraints

-   For information on constraints and default settings to consider when you deploy an application in the Cloud Foundry environment, see [http://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html\#limits\_table](http://docs.cloudfoundry.org/devguide/deploy-apps/large-app-deploy.html#limits_table).
-   SAP BTP exposes applications only via HTTPS. For security reasons, applications can’t be accessed via HTTP.



<a name="loioe6ddaefcbb571014b70fa01fc6a3f818__section_lxn_zl1_ybb"/>

## SAP BTP Tools

-   SAP BTP Tools for Java and SDK have been tested with Java 7, and Java 8.
-   SAP BTP Tools for Java and SDK run in many operating environments with Java 7, and Java 8 that are supported by Eclipse. However, SAP doesn’t systematically test all platforms.
-   SAP BTP Tools for Java must be installed on Eclipse IDE for Java EE developers.

For the platform development tools, SDK, Cloud connector, and SAP JVM, see [https://tools.hana.ondemand.com/\#cloud](https://tools.hana.ondemand.com/#cloud).



<a name="loioe6ddaefcbb571014b70fa01fc6a3f818__section_1C5DFC4FEB8C4608B6E7C659D1B4BFD4"/>

## Browser Support

For a list of supported browsers for the SAP BTP cockpit, see [Feature Scope Description](https://help.sap.com/doc/5e8107bf49684962b897217040398007/Cloud/en-US/SAP_Cloud_Platform_FSD.pdf).

For a list of supported browsers for developing SAPUI5 applications, see [Browser and Platform Support](https://sapui5.hana.ondemand.com/sdk/#/topic/74b59efa0eef48988d3b716bd0ecc933).

To find out the browser support for a specific service, refer to the corresponding feature scope description.

For security reasons, SAP BTP doesn’t support TLS1.1 and older, SSL 3.0 and older, and RC4-based cipher suites. Make sure that your browser supports at least TLS1.2 and modern ciphers \(for example, AES\).

