<!-- loio74c8e423c6da4de08cd59acfe74a168e -->

# Content Security Policy

Content Security Policy \([https://www.w3.org/TR/CSP3](https://www.w3.org/TR/CSP3)\) is a standard which allows you to disable certain HTML/JavaScript features to reduce the attack surface of applications running in a browser \(for example, as a second line of defense against cross-site scripting attacks\). The policy explicitly lists all allowed sources from where resources \(scripts, styles and fonts\) can be loaded.

Servers can define different content security policies \(CSPs\) for different paths \(applications\) and different resource types to provide very granular control.

CSPs can be defined in reporting or blocking mode. In reporting mode, a violation will be reported to a URI specified within the CSP. In blocking mode, violations are not only reported but execution of violating code or loading of the violating resource is additionally blocked by the browser.

**Related Information**  


[Manage Content Security Policy](manage-content-security-policy-31d793c.md)

