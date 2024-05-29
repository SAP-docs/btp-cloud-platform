<!-- loiod3eb18db88504e348a0096c5a20b3659 -->

# Deprecation Trial for Google's Third-Party Cookies

Google has announced its plan to phase out support for third-party cookies by the third quarter of 2024. See [The Privacy Sandbox Timeline for the Web](https://privacysandbox.com/intl/eng/open-web/#the-privacy-sandbox-timeline) and [Prepare for Third-Party Cookie Restrictions](https://developers.google.com/privacy-sandbox/3pcd).

Third-party cookies are cookies that are set by domains other than the one a user is directly visiting. They are commonly used for online advertising and tracking user behavior across multiple websites. They can be set through JavaScript, iframe, embedded images, or media. SAP primarily uses third-party cookies for service management and single sign-on.

Google offers the [third-party deprecation trial](https://developers.google.com/privacy-sandbox/3pcd/temporary-exceptions/preserving-critical-user-experiences) that allows re-enabling third-party cookies for a page embedded within a cross-site iframe until December 27, 2024. To enable the depreciation trial, all applications' responses must include a deprecation trial token obtained for each affected domain. At SAP, the process of obtaining the tokens is handled centrally.

There are three different ways to add the deprecation trial token - you can either provide it in an HTTP header, use a meta tag, or inject the token with JavaScript. For SAP BTP, Kyma runtime workloads, it is recommended that you use the HTTP header. You must add the token manually for each of the affected workloads.



<a name="loiod3eb18db88504e348a0096c5a20b3659__section_lrn_gnc_kbc"/>

## Technical Details

In SAP scenarios, the first request to the origin in a session typically requires cross-site cookies. Sending the `Critical-Origin-Trial` header in the HTTP response with the trial name causes the browser to retry the request with third-party cookies enabled.

```
Critical-Origin-Trial: Tpcd
```

For SAP BTP, Kyma runtime, it is not possible to identify the initial request, so the `Critical-Origin-Trial` header is included in every response. This approach has been accepted by Google.

Each HTTP response must also include a valid depreciation trial token for the used domain in the following HTTP header:

```
Origin-Trial: <token-domain>
```

For domains specific to a particular customer, use the token\(s\) provided by that customer. For the domain `ondemand.com` managed by SAP, use the following token:

```
Avu6rn7emV5gK8gvyGHlX8TMqM9uo1FacP2j/RWTq+8j+yKnqcTO0TQh0bXJ/7QntxD4/JzXv8aXoqxxZQuqXgYAAABdeyJvcmlnaW4iOiJodHRwczovL29uZGVtYW5kLmNvbTo0NDMiLCJmZWF0dXJlIjoiVHBjZCIsImV4cGlyeSI6MTczNTM0Mzk5OSwiaXNTdWJkb21haW4iOnRydWV9
```

The token consists of the feature name \(Tpcd\) and its source, along with other attributes. If an application or service can be accessed from multiple domains simultaneously, you can add one token per domain as a comma-separated list.

```
Origin-Trial: <token-domain1>, <token-domain2>, ...>
```

**Related Information**  


[Apply Third-Party Cookie Deprecation Trial Tokens for Kyma Runtime Workloads](apply-third-party-cookie-deprecation-trial-tokens-for-kyma-runtime-workloads-479a43e.md "Learn how to use EnvoyFilter or Istio VirtualService to add a third-party cookie deprecation token to an HTTP response for a particular workload exposed under the domain ondemand.com.")

[Preparing and Testing Your Solution for Third-Party Cookie Deprecation](https://help.sap.com/docs/btp/preparing-and-testing-your-solution-for-third-party-cookie-deprecation/what-is-purpose-of-this-document?version=Cloud)

