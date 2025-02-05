<!-- loio81aed02afbdb41379fe0eb4b23f7756a -->

# Maintain Protection Allowlists

With this app you can maintain a list of trusted hosts or URL patterns.



With this app you can define secure applications by adding trusted hosts to allowlists. The following allowlists are available as separate tabs in the app:

-   *Clickjacking Protection*

    By default, clickjacking protection is active to protect your systems against malicious clickjacking. If the system is embedded into another application, the check determines whether the other application is allowed as a framing parent \(that means it is allowed to embed the UI within frames in external pages\). To add trusted hosts, you have to enter specific details, such as schema and port, for each trusted host to make sure that malicious hosts are identified and prevented from calling your system.

-   *Trusted Network Zones*

    Here you can list URL patterns for which a redirect is allowed or blocked. Trusted network zones configuration also restricts uploads defined by URLs.

-   *Trusted CSS Style Sheets*

    Here you can list URL patterns for loading CSS style sheets. This may be necessary if customer extensions are using external CSS style sheets.

-   *Cross-Origin Resource Sharing*

    Here you can add trusted hosts using Cross-Origin Resource Sharing. For more information, see the *Related Information* section.




<a name="loio81aed02afbdb41379fe0eb4b23f7756a__section_fmw_cch_jfb"/>

## Key Features

You can use this app to:



-   Add trusted hosts to the required allowlist

-   Edit trusted hosts or URL patterns

-   Delete trusted hosts or URL patterns


> ### Note:  
> You can also define wildcards if required, such as `*test.com`.



<a name="loio81aed02afbdb41379fe0eb4b23f7756a__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loio81aed02afbdb41379fe0eb4b23f7756a__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-APS-COM`.

**Related Information**  


[How to Add Trusted Hosts for Cross-Origin Resource Sharing \(CORS\)](how-to-add-trusted-hosts-for-cross-origin-resource-sharing-cors-5ea6325.md "")

