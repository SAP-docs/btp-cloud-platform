<!-- loio7cd77caf04bf4b3e8276a52327252637 -->

# Logon Screen Shows "SAP HANA XS Advanced"



## Symptom

After sending a request to a web application in the SAP BTP, Cloud Foundry environment, you see a logon screen with the title SAP HANA XS Advanced.

Below the Log On field, the following domain is displayed: xs2security.accounts400.ondemand.com

> ### Note:  
> **The expected system behavior is to return a logon screen with the title Welcome <IdP\_tenant\_name\>!.**



## Reason and Prerequisites

The request of the business user is not authenticated, so it needs to be redirected to the identity provider where the business user is defined. The trust of the identity provider is configured and assigned to the tenant to which the business user belongs. In this case, SAP BTP, Cloud Foundry environment cannot correctly determine the tenant of the business user. As a result, it cannot find the correct identity provider and falls back to

[https://authentication.sap.hana.ondemand.com](https://authentication.sap.hana.ondemand.com/)



## Solution

This error indicates a problem with the ***TENANT\_HOST\_PATTERN*** environment variable in the ***manifest.yml*** file of the web application. The tenant host pattern is a regular expression \(regex\) and is used to determine the tenant ID \(which is identical to the subdomain\) with which the request is associated. For more information, see [Multitenancy](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/5310fc31caad4707be9126377e144627.html). The system shows the behavior described earlier if the URL of the request does not match with the defined pattern.

The tenant host pattern should be defined as follows:

```
.
.
.
  env:
    XSAPPNAME: <application_name>
    TENANT_HOST_PATTERN: "^(.*)-<application-router-hostname>.cfapps.<region>.hana.ondemand.com".
.
.
.


```

> ### Note:  
> Separate the regular expression and the Cloud Foundry host name with a hyphen \(-\). The subdomain of the tenant is not a subdomain of the web application in a technical sense. The subdomain would be separated from the Cloud Foundry host name with a dot \(.\). Since there is no automatic certificate creation process each time that a new tenant is onboarded, you must use a workaround.
> 
> The current workaround is to concatenate the subdomain of the tenant with the Cloud Foundry host name using the hyphen \(-\). All such concatenations share the same Cloud Foundry top level domain, together with the certificate of this top-level domain.
> 
> The following example shows the web application
> 
> ***bulletinboard***
> 
> in the
> 
> ***cfapps.eu10.hana.ondemand.com***
> 
> Cloud Foundry domain:
> 
> ```
> .
> .
> .
>   env:
>     XSAPPNAME: bulletinboard
>     TENANT_HOST_PATTERN: "^(.*)-approuter.cfapps.eu10.hana.ondemand.com".
> .
> .
> .
> ```

> ### Note:  
> Recheck the definition of the ***TENANT\_HOST\_PATTERN*** environment variable in the ***manifest.yml*** file, and correct it, if necessary.**The route for the TENANT\_HOST\_PATTERN has to be lowercase.**

