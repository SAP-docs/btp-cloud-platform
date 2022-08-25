<!-- loio5ea6325d8b2f49efae8622635dd0a542 -->

# How to Add Trusted Hosts for Cross-Origin Resource Sharing \(CORS\)



<a name="loio5ea6325d8b2f49efae8622635dd0a542__CreateTrustedHostsCors_context"/>

## Context

CORS is a mechanism that allows web browsers or other web clients access to your sites. Access of this kind is usually forbidden by the Same-Origin-Policy \(SOP\). To add trusted hosts using CORS, proceed as follows:



## Procedure

1.  Open the *Maintain Protection Allowlists* app on the SAP Fiori Launchpad.

2.  Open the *Cross-Origin Resource Sharing* tab.

3.  Enter the *Trusted Host Name* \(SAP Analytics Cloud, for example, could have the following pattern: *mytenant.us1.sapbusinessobjects.cloud*\).

4.  Enter the *HTTP Service Path* \(for example ***/sap/opu/odata/sap/APS\_IAM\_API\_BROLE\_CDOC***\).

5.  Select the allowed HTTP methods .

6.  Enter the allowed headers \(for example ***content-type***\)

    Only the following response headers are generally accessible in a CORS query:

    -   *Cache Control*

    -   *Content Type*

    -   *Last Modified*

    -   *Content Language*

    -   *Expires*

    -   *Pragma*


    If the server wants to give the client access to further headers, it has to use the *Exposed Headers* option.

7.  In addition, you can define exposed headers under *Optional Response Headers* if required. Please select the required checkboxes.

8.  Click *Add*.


**Related Information**  


[Understanding the Same-Origin Policy and CORS](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/2d7115b0e0aa4f78bfd9c06fdc1fe4f6/883074bbfe304f7c86e4b5088783a706.html?locale=en-US)

