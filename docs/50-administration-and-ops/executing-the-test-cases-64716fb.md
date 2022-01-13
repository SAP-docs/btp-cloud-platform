<!-- loio64716fba70264ab0b0f00f3a867df824 -->

# Executing the Test Cases

Instruct your testers to perform the steps described in the test cases to measure the workload for sizing.



<a name="loio64716fba70264ab0b0f00f3a867df824__prereq_pj1_g1k_hrb"/>

## Prerequisites

Before testing starts, make sure that the following prerequisites are met:

-   Testers have the authorizations that correspond to that of a business user.

-   A capture profile exists, and it is set to *Active* \(see also [Defining a Capture Profile for Sizing](defining-a-capture-profile-for-sizing-ba3ddae.md)\).

-   Testing is performed within the time period that is entered in the capture profile.




## Context

The testers' system activities are captured to estimate the workload as a basis for system sizing.



## Procedure

1.  Instruct your testers to execute the preparation steps as documented in [Defining Test Cases for Sizing](defining-test-cases-for-sizing-0e95d18.md).

2.  Instruct your testers to execute the steps of the test case within the defined time period for testing.




<a name="loio64716fba70264ab0b0f00f3a867df824__result_kqm_v35_tqb"/>

## Results

The ABAP statistics records relating to the tester activities in the ABAP system have been captured. To ensure stable results, consider defining multiple capture profiles with different test times for one test case and repeat the measurement 2-3 times.

