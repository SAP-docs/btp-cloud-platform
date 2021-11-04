<!-- loioa4285436577142daaa48e1da2d765085 -->

# Measurement Prerequisites

To ensure meaningful and reproducible results, make sure that prerequisites for the test system and test organization are met before measurements for sizing are taken.



Before you start testing, check the following:

-   The setup and configuration of the test environment should be equivalent to a production environment. As you only perform single user tests, the test environment doesn't need the same hardware resources, but make sure that the following is the same as in a production system:

    -   Software releases of all software components involved in the stack

    -   Settings of the application that influence its behavior, for example, Customizing settings that control internal data verification steps


-   Moreover, prevent any concurrent workload that consumes a noticeable amount of resources during the test. Having some house-keeping jobs active in the background is unproblematic. You should, however, avoid that tests compete with other, resource-intensive business processes.

-   The test environment should contain a defined amount of existing business data. The SAP HANA database can consume different amounts of resources in a system with no business data compared to a system with a significant amount of existing business data.

-   All test cases should be executed with a specific test user. A dedicated test user makes it much easier to separate calls originating from the test case execution from other activities, for example, calls originating from measurement tools. This test user should have the same authorizations that a corresponding business user has in the relevant business process.

-   Consider caching effects of the application. The initial load of an application can consume more resources than a later use of the same application. To ensure a measurement that considers caching effects, execute the business scenario once without capturing the workload and a second time with capturing it.


