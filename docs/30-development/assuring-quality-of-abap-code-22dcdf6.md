<!-- loio22dcdf6c7cb54a19908056f2e257df42 -->

# Assuring Quality of ABAP Code

This is an overview of ABAP quality tools that help you to keep your custom code clean and performant.

The two most important quality tools for your custom ABAP code are:

-   *ABAP Unit* for dynamic tests
-   *ABAP Test Cockpit \(ATC\)* for static code analysis



<a name="loio22dcdf6c7cb54a19908056f2e257df42__section_yzq_jpb_pvb"/>

## ABAP Unit

Writing ABAP Unit tests is the way to provide high-quality software, which can be easily evolved over time without introducing regressions. In methodologies, like extreme programming and test-driven development, the role of unit testing is even more important.

ABAP unit is the state-of-the-art unit testing framework for ABAP. It's embedded into the ABAP programming language, which supports you in writing unit tests. In the ABAP Development Tools \(ADT\), you have various possibilities to execute the unit tests and to evaluate the results concerning functional correctness and code coverage.

We recommend measuring the test coverage of all objects in a transport before releasing the transport. A high coverage \(above 80%, for example\) and a wide variety of test methods help to identify issues and make the code more robust.

For more information, see [Unit Testing with ABAP Unit](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/08c60b52cb85444ea3069779274b43db.html).



<a name="loio22dcdf6c7cb54a19908056f2e257df42__section_zlq_ypb_pvb"/>

## ABAP Test Cockpit \(ATC\)

ATC is the tool of choice for all kinds of static code analysis in ABAP. As an ABAP developer, you can use ATC in the ABAP Development Tools \(ADT\) to find potential bugs already during the development phase.

In particular, you can check ABAP development objects for many types of problems, including syntax errors, potential problems in performance, suboptimal or potentially faulty programming, adherence to standards, errors in ABAP Unit testing, among others.

For more information, see [Checking Quality of ABAP Code with ATC](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/4ec5711c6e391014adc9fffe4e204223.html).



### ATC Check Variant

The basic configuration of the ATC is the so-called ATC check variant, which includes the set of checks that should be executed. The default variant is set to ABAP\_CLOUD\_DEVELOPMENT\_DEFAULT. It includes all recommended checks to fulfill the ABAP cloud code quality standard incl. the execution of ABAP Unit tests.

You can create a copy of this variant and add additional checks. You can also add custom created checks to your variant.

For more information, see [Working with ATC Checks](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/438842e71bfa4ff09443562f5ce2282d.html).



### Transports

The basic quality gate is the release of transport tasks and transport requests.

For findings with priority level 1 and 2, the release of tasks and requests is blocked by the system in the default setting. For findings with priority level 3, the developer only gets a notification. This default setting can be individually sharpened based on your needs.

For more information, see [Working with ATC During Transport Release](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/c0d95a9263da476eb5b6ae03225ce7ba.html).



### Test Runs

You can either set up scheduled automated test runs for the ATC, or trigger it manually via ADT.

For more information, see [Working with ATC During Development](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/a6961953041b48e6b823e15310ed9ecd.html).



### ATC Exemptions

Sometimes ATC findings can't be corrected. For example, it’s possible that a correction is planned for an upcoming development cycle or only a test program is affected. It could also happen, that checks return false positives.

In this case, you can still process the issue by requesting an exemption. Once approved, it masks an ATC error or warning message. The finding then isn’t displayed as an open issue in the ATC results anymore.

In the ABAP environment, exemptions are transportable objects of the type CHKE. The full workflow for the request and approval of exemption is integrated in ABAP Development Tools \(ADT\).

For more information, see: [Working with ATC Exemptions](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/b317b37b06304f99a8cf36e0ebf30861.html).



### ABAP Test Cockpit Configurator App

You can use the ATC Configuration app to set up the default variant. You can also change the priorities of check messages, set priority levels that block or interrupt transport releases, and set the handling of pseudo comments and pragmas.

For more information, see [ABAP Test Cockpit Configurator](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/22c26ff27b9f44b7b7229a01e8e8ed25.html).

