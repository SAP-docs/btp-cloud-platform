<!-- loio31d793c8a80644a9bc25b1e1b3ee147e -->

# Manage Content Security Policy



Content Security Policy is a standard that allows to disable certain HTML/Javascript features to reduce the attack surface of applications running in a browser \(for example as second line of defense against cross-site scripting attacks\).

With this app you can view an allowlist of trusted sources. You can add your own trusted content for example if you have developed your own SAPUI5 app that loads external resources such as fonts, scripts or styles. Moreover, you can display any violations of the policy in a log.



## Key Features

You can use this app to:



-   Display a whitelist of allowed sources

-   Add new allowed sources to the whitelist

    For fonts, use UI\_RESOURCES\_FONTS; for scripts, use UI\_RESOURCES\_SCRIPTS, for styles, use UI\_RESOURCES\_STYLES.

-   Display logs listing violations

    Please note the following information about browser-related effects that in some cases might result in additional violations while in other cases violations are not listed:

    -   The violation logs might contain records indicating that an EVAL violation has occurred. These violations can be ignored. They are caused by unexpected behavior in Google Chrome.

    -   Firefox does not send the session cookie with the reporting requests. These requests will therefore be rejected by the backend, and are thus not included in the log.

    -   Browser extensions sometimes insert non-policy conform code into an HTML page. This results in violation log entries that are not caused by the applications themselves.





<a name="loio31d793c8a80644a9bc25b1e1b3ee147e__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loio31d793c8a80644a9bc25b1e1b3ee147e__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component ``BC-SRV-APS-COM``.

